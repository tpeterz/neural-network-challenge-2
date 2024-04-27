# neural-network-challenge-2
# Module 19 Challenge 
# MSU AI Bootcamp 2023 - 2024
---
## Author
- Taylor Peterson
---
# Background
>You are tasked with creating a neural network that HR can use to predict whether employees are likely to leave the company. Additionally, HR believes that some employees may be better suited to other departments, so you are also asked to predict the department that best fits each employee. These two columns should be predicted using a branched neural network.
# Part 1: Preprocessing
* Import the data. 
* Create y_df with the attrition and department columns. 
* Choose 10 columns for X. 
* Show the data types of the X columns. 
* Split the data into training and testing sets. 
* Encode all X data to numeric types. 
* Scale the X data. 
* Encode all y data to numeric types. 
# Part 2: Create, Compile, and Train the Model
* Find the number of columns in the X training data. 
* Create an input layer. 
* Create at least two shared hidden layers.
* Create an output branch for the department column.
* Create an output branch for the attrition column. 
## Additional Note
#### Each step of my process to complete the starter code is detailed in the comments at the beginning of each cell
#### I have also detailed references throughout my code that reference module activities that aided my code completion.
---
# Part 3: Summary
## Questions:
1. Is accuracy the best metric to use on this data? Why or why not?

2. What activation functions did you choose for your output layers, and why?

3. Can you name a few ways that this model might be improved?
## Answers:

1. Accuracy may not adequately reflect the effectiveness of this model. Looking at the data I began with for my `y_df`, it is easily visible that the data from both of the columns is rather imbalanced and probably skewed. This can cause bias or mispleading/high scores during the training process, possibly leaning towards one outcome over another. I believe that I need to incorporate other metrics to use on this data, such a precision, recall, F1-score, and possibly a confusion matrix. 
2. 
* For the **department** output layer, `department_output`, I chose **Softmax**. This is because this column is a multi-class categorical variable. From my understanding, this is best so that exactly one class is the correct classification for each *instance*, through the probability distribution over the classes. It will ensure that the sum of potential outcomes will be 1. A similar thought process was applied when thinking about the encoding menthod that the starter code required for this column (**OneHotEncoder**). A simpler explanation would be that each value in the department column cannot be true at the same time (For example, you cannot work in both the sales AND human resources departments at the same time. They are exclusive of each other).
* For the **attrition** output layer, `attrition_output`, I chose **Sigmoid**. This is because of the binary categorical variable (Yes or No : 1 or 0). There are only two possibilites here; if it is not 'Yes', it will be 'No', and vice versa. My first choice for use was Softmax, however even after changing it to my final choice of sigmoid, the results did not change. 
3. 
*  First, when creating `shared_layer1` and `shared_layer_2`, I used 'relu' for activation. I could use a different activation function for these, such as leaky relu. 
* Second point about my layer creation; I used 64 neurons for the first shared layer, and only 32 for the second shared layer. This could be changed when tuning the model as well, such as increasing the neurons and adding additional hidden layers (adjusting neurons from there). 
* Third, I could adjust the number of epochs used to train the model, increasing them to allow further analysis.
* The last and main improvement that I will point out is the encoding method used for the 'Attrition' column. While 'OneHotEncoder' was specifically what I am told to use, wouldn't a 'LabelEncoder' be better to use in this instance? With such a binary choice as "Yes" or "No," this would dispell any unnecessary complexity, and result in just those two output probabilities. This would further change the compile method I used, where it would require *`binary_crossentropy`*. I could also use an OrdinalEncoder with categories set to yes or no.

---
# References
1. [How To Improve Deep-Learning Performance](https://machinelearningmastery.com/improve-deep-learning-performance/
) - Jason Brownlee, *20 Tips, Tricks and Techniques That You Can Use To Fight Overfitting and Get Better Generalization*
2. [Fundamentals of Deep Learning – Activation Functions and When to Use Them?](https://www.analyticsvidhya.com/blog/2020/01/fundamentals-deep-learning-activation-functions-when-to-use-them/
) - Dishashree26 Gupta
3. [Categorical Data yes/no to 0/1 python - is it a right approach?](https://stackoverflow.com/questions/49227490/categorical-data-yes-no-to-0-1-python-is-it-a-right-approach) - Stack Overflow Question/Answer (regarding encoding approach)
4. [Encoding Before vs After Train_Test_Split?](https://www.geeksforgeeks.org/encoding-before-vs-after-train_test_split/)