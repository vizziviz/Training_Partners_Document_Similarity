# Training Partners Document Similarity
This analystic project seeks to pair personal training clients by text similarity with extracted text from intake forms.

### Extract text
First I used PDF extraction tools to read text from uploading PDF docs.

### Clean Text Data
I used **regular expressions** and **text parsing libraries** to clean the text remove blank lines, numbered lists, questions from the form, personal data, and extranous information to collect important text reflecting client goals, needs, limitations, and customer profiles. 

Text transformed from this: 

![Screen Shot 2023-05-18 at 8 25 03 PM](https://github.com/vizziviz/Training_Partners_Document_Similarity/assets/64040862/44fc4127-f7c4-4ef1-a98b-e3592a66adef)

To this:

![Screen Shot 2023-05-18 at 8 26 19 PM](https://github.com/vizziviz/Training_Partners_Document_Similarity/assets/64040862/ce572206-cbda-4256-9954-8621032b1371)

### Visualize and Explore Data
Some simple visualizations helped me explore different ways clients might be approaching their first experiences with the fitness company: some to build muscle, some to lose fat, some to get healthy, and others to feel better and more energetic. 

Here I look at the most common words used in intake forms.

![Screen Shot 2023-05-18 at 8 26 55 PM](https://github.com/vizziviz/Training_Partners_Document_Similarity/assets/64040862/a86339a1-6e7b-4a32-83c1-c6d5f6d6f121)

### Algorithms, algorithms, algorithms
But which function should I use to judge most "similar" text and thus most similar clients. I went with the inner product function, which takes sparse vectors to represent each client (lots of 0s and 1s), then normalizes each sparse vector to avoid weighing longer texts more heavily than shorter texts, and "scores" each combination of clients by summing the inner products of the vectors. For example, if Carl has a vector [.3, .1, 0] representing the words ['muscle', 'strong', 'skinny'] and Sarah's vector is [0, .1, .9] representing the same words, then their inner product is 0.3\*0 + 0.1\*0.1 + 0\*0.9 which resolves to 0.01.

### Putting It All Together
Finally I iterate through all possible pairs of partners until I find the best suited pairs. 
