# MOFGen

#### Aim: We are trying to finetune the PMTransformer (formerly MOFTransfromer) on OpenDAC data 

### Abstract:

PMTransformer is a BERT based transformer architecture trained on around 2 million crystal structures: mostly MOFs, but also a decent number of COFs, PPNs, and Zeolites. A Model trained on such type of diverse crystal data learns the synergistic effects existing between different types of crystals; It learns the thick and thin of crystal structures and the kind of topology they can adopt. It is the reason why we can fine tune such a model for different tasks, given that we have a good data.  


![MOFTransformer_img](https://github.com/shazam37/MOF-Generator-/assets/119686545/9f5dbea9-d16e-482b-856a-dd0bb5e8b0b6)


More info on the PMTransformer can be found at: https://github.com/hspark1212/MOFTransformer/tree/d8d80eec391ccb78cbed79a4d6a1bb60216403d6

One such task is Direct Air capture (DAC) or the adsorption of CO2 and water vapor for different tasks. It could be about cleaning the air or harvesting water from the atmosphere in places where water is scarce. MOFs are known to be very good at this given their porous structure. If we can explore the practical MOFs suited for this task then we can optimise the manufacturing process and make the MOFs mainstream. The possibilities are endless!

The DFT based OpenDAC dataset released by Meta recently is the most accurate representation of the adsorption interaction between different MOFs and CO2 and H2O molecules. It is derived from the Core-MOF dataset which held this title before. OpenDAC overcame the edge cases of Core-MOF dataset: 
1. It took into account the fact that CO2 is often accompanied by H2O given their relative abundance and similar size. This could lead to competitive adsorbance.
2. It is the first of its kind DFT dataset made specifically for gas adsorption. All the datasets before including Core-MOF were based on Force Fields. 
3. It addressed the significance of crystal defects and introduced them in the data through defect engineering. All the datasets before contained only the pristine structures.

  
![Screenshot from 2024-02-25 16-41-48](https://github.com/shazam37/MOF-Generator-/assets/119686545/c0e1a774-5a7d-4277-aedb-0e1c751b8a53)


It contains the DFT stimulation trajectories of ~8000 MOFs. They arrived at this small number through extensive data cleaning. But! each MOF is stimulated with different cases, whether it could be adsorbing just 1 CO2 molecule, 1 H2O molecule, and 1 CO2 and 2 H2O molecule. This way, we have around ~176K adsorption energy values and ~38M single-point DFT calculations. They have defined the energy metrics for calculating the adsoprtion values for different cases. 

Besides, they have made 4 testing datasets sets each containing a different set of MOFs not included in the training and validation data: the test-ood (big) set contains MOFs with over 500 atoms in their unit cells, the test-ood (linker) set contains novel linkers but known topologies, the test-ood (topology) set contains novel, topologies but known linkers, and the test-ood (linker & topology) set contains both novel linkers and novel topologies. 

More info on the OpenDAC can be found at: https://open-dac.github.io/

### Conclusion

We plan to feed the OpenDAC data in PMTransformer. First we experiment with fine-tuning the OpenDAC model on PMTransformer for CO2 adsorption prediction and see the outcome. Next we will experiment with the frame wise data and see that if we can predict the trajectory of CO2 adsorption on novel MOFs. 

The chemical space of MOF is still largely unexplored. We want to steer in the direction where we can find novel MOFs specifically for the CO2 adsorption task. We might use Reinforcement learning coupled with a generative algorithm to generate novel MOFs and rank the best ones through the fine-tuned PM transformer. But thats a work for the future. 
