# Using Reservoir Computing to find Exoplanets in Deep Space

## The Data Set

Hunting for Exoplanets in Deep Space is a data set taken from NASA’s Kepler Missions. 
The cleaned data used for this implementation was found on 
[Kaggle](https://www.kaggle.com/datasets/keplersmachines/kepler-labelled-time-series-data).

An exoplanet is defined as a planet that orbits a star other than our Sun. 
Identifying exoplanets is key to furthering our understanding of the universe and our place in
it.
The data consists of light flux readings from 5,657 stars. For each star there are 3,198
light flux readings taken over time and a label classifying the star as having an exoplanet in orbit or not.

The goal of this implementation will be to predict whether or not a star has an exoplanet
in orbit based on how these light flux readings change with time. This is called
the transit method for exoplanet detection. This is a time-series classification task
as the goal is to apply a label to a sequence.

![image](https://user-images.githubusercontent.com/129991245/231482094-1e995b97-5dbe-41de-8968-821b3f56a7af.png)

The image above shows the transit method. A star is being orbited by a planet. At time t=1 the
planet does not obscure the light of the star. At time t=2 the planet partially obscures
the star and we see a drop in the light flux. At time t=4 the planet no longer obscures
the planet and the flux returns to its initial value. The graph at the bottom shows the
change in light flux (brightness) with time.


## Reservoir Computing

Reservoir Computing (RC) is a machine learning paradigm which aims to significantly
reduce training cost by only training the readout layer. 
The rest of the model is untrained and consists of a fixed high-dimensional system, referred to as the ’reservoir’.

The idea of RC was originally derived from Recurrent Neural Networks (RNNs), with
the main change being the Neural Network was randomised and treated as a ’black
box’ - this became known as the Echo State Network (ESN), which is what was used for this project. This framework has
been proven incredibly effective despite its simplicity. 

In this project I used the 
[*ReservoirPy*](https://pypi.org/project/reservoirpy/) 
library to create a virtual reservoir.
