<h1>SIR model ofCovid19 outbreak</h1>
<h2>SIR Model</h2>
<p1>The SIR model describes the outbreak and evolution of an infectious desease in a population with N individuals (<a href='https://en.wikipedia.org/wiki/Compartmental_models_in_epidemiology' target=_blank>See Wikipedia page for additional detaills)</a> This model is refered to as a compartmental model as the population is assigned to compartments. The SIR model has 3 components:
<dl>
    <dt>S(t)</dt>
    <dd>Represents the number of individuals not yet infected at a time t, but are susceptible to the disease</dd>
    <dt>I(t)</dt>
    <dd>Represents the number of individuals at a time t that are infected and contagious</dd>
    <dt>R(t)</dt>
    <dd>Represents individuals who have had the disease and can no longer be infected or transmit the disease, either due to immunization of death.</dd>
</dl>
Given these 3 compartments, we have that the total population is N = S(t) + I(t) + R(t) is constant. For any given individual, their progression is given by S -> I -> R.
The SIR model is given by a system of differential equations, which relate the different components of the model to each other.<br>The system is given by:<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
<img src="https://render.githubusercontent.com/render/math?math=\frac{dS}{dt}= -  \frac{\beta S I}{N}"><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
<img src="https://render.githubusercontent.com/render/math?math=\frac{dI}{dt}= \frac{\beta S I}{N} - \gamma I"><br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
<img src="https://render.githubusercontent.com/render/math?math=\frac{dR}{dt}= \gamma I"><br>
<img src="https://render.githubusercontent.com/render/math?math=\gamma"> = mean recovery/death rate in units of <img src="https://render.githubusercontent.com/render/math?math=\frac{1}{days}">, and  <img src="https://render.githubusercontent.com/render/math?math=\frac{1}{\gamma}"> is the mean infective period, denoted   <img src="https://render.githubusercontent.com/render/math?math=p_{inf}">. <br><br>
 <img src="https://render.githubusercontent.com/render/math?math=\beta"> is the infection rate. Define <img src="https://render.githubusercontent.com/render/math?math=n_{inf}"> to be the number of individuals in S each individual in I infects, the, <img src="https://render.githubusercontent.com/render/math?math=\beta=\frac{n_{inf}}{p_{inf}} = n_{inf} \gamma">. <br><br>
</p1>

<p2>We will be using the SIR model to model the outbreak of Covid19. We will first use the model reproduce the data of the first 14 days of the outbreak in Wuhan. Once our model fits the data, we wull use it to predict how the virus will affet the population for the next 100 days.<br><br>
For this model, we will be using <img src="https://render.githubusercontent.com/render/math?math=\gamma = \frac{1}{10days^{-1}}">, so <img src="https://render.githubusercontent.com/render/math?math=p_{inf}"> = 10 days. We will be using the following initial values: (<img src="https://render.githubusercontent.com/render/math?math=S_{0}, I_{0}, R_{0}">) = (<img src="https://render.githubusercontent.com/render/math?math=N-I_{0}, 574, 0">) and N = 11 000 000 (Wuhan population).

<br>Wuhan Data:<br>
<img src='/images/Cvirus.png'>
<br> Data generated using our SIR model:
<img src='/images/SIR_model_plot.png'>
Comparing both plots, we see that the SIR model gives similar results than the data. So we can comfortably use this model to predict the next 100 days to get an idea of how Covid19 will spread in Wuhan. In this simulation we will plotting all 3 components (S, I, R) individually, aswell as hospital admissions per day and total hospital beds available. We wull define the hospital admission rate due to Covid to be 5% of those who transition from I to R, i.e., 5% of <img src="https://render.githubusercontent.com/render/math?math=\frac{dR}{dt}">. China has on average <a href='https://en.wikipedia.org/wiki/List_of_countries_by_hospital_beds' target=_blank>4.34 hospitals bed per 1000 people</a>. We assume that only 20% of the hospital beds are allocated to Covid19 patients, and these patients stay 4 days in hospital. Lastly we assume the death rate of the disease to be 1% of R. 
100 day simulation of outbreak: <br>
<img src='/images/SIR_100days.png'>
To reproduce that Wuhan data we had to set ninf to 4, meaning the disease is preading fast (lots of social interactions between individuals). Under these conditions, hospitals in Wuhan will not be able to accomodate all Covid19 patients for a (about) 50 day period starting from the 25th day after the initial breakout.<br>
To emphisize how important social distancing measures are, we can looke at the number of infected of individuals while varrying ninf:<br>
<img src='/images/Varying_ninf_infected.png'><br>
We see that for the infected curve has a similar shape, put the peaks are a lot higher the greater ninf is. <br>
<img src='/images/Varrying_beds_needed.png'><br>
We see that social measures also effect the numbers of beds needed for Covid 19 patients. <br><br>
From our model, we can conclude that Covid19 spreads very quickly and can rapidly overwhelm the hospitals. Our model also highlights the importance of putting social distancing measures in place. We see that the measures are strict, and people respect them (i.e. keep ninf between 1 and 2), the number of infected individuals greatly goes down and the hospitals will not be able to operate and take care of everyone who needs to be administered.<br><br>
It is worth keeping in mind that the SIR model is a relatively basic model. Meaning, it doesnt take into account a lot of factors, such as indivduals who might be immune for exemple, or latency period (period where infected people are not yet infectious), just to name a few. More accurate models exist, such as the SEIR (Ssceptible-Exposed-Infected_Removed) model, which has been used in <a href='https://translational-medicine.biomedcentral.com/articles/10.1186/s12967-020-02513-7' target=_blank>academic papers</a> to model the Covid-19 outbreak.
