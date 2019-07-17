# Analyze-A-B-Test-Results
This project is dedicated to Udacity. It is conducted to understand the results of an A/B test run by an e-commerce website.  The ultimate goal is to work through this notebook to help the company understand if they should implement this new page, keep the old page, or perhaps run the experiment longer to make their decision.


After finishing projects and receiving feedbacks from senior coders, here is some lessons I have learnt:

1. When possible, it is always more computationally efficient to use numpy built-in operations over explicit for loops. Because numpy-based operations attack a computational problem based on vectors by computing large chunks simultaneously. Additionally, using loops to simulate 10000 can take a considerable amount of time
vs using numpy. My code uses for loop operation and it consumes more time as follows:

# Create 10,000 Pnew - Pold values using the same simulation process above. 
# Store values in a Numpy array called p_diffs.
p_diffs=[]
for i in range(10000):
    new_page_converted = np.random.choice([1,0], size=n_new, p=[p_new,(1-p_new)]).mean()
    old_page_converted = np.random.choice([1,0], size=n_old, p=[p_old,(1-p_old)]).mean()
    diff= new_page_converted - old_page_converted
    p_diffs.append(diff)

https://softwareengineering.stackexchange.com/questions/254475/how-do-i-move-away-from-the-for-loop-school-of-thought

Fast code:
new_converted_simulation = np.random.binomial(n_new, p_new, 10000)/n_new
old_converted_simulation = np.random.binomial(n_old, p_old, 10000)/n_old
p_diffs = new_converted_simulation - old_converted_simulation