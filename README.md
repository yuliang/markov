markov
======

The goal is to create a randomized text generator, which creates output based on a source text. The source text filename will be provided as a command line argument.

In order to make the random text have some resemblance to real writing, first build up a repository of three-word chains in the source text. For example, if you take the following sentence:
The happy dog followed the car.
The three-word chains are:
(Start)
The
=>
happy
 The
happy
=>
dog
 happy
dog
=> 
followed
 dog
followed
=> 
the
 followed
the
=> 
car
 the
car
=> 
.
The bigger the input text, the better (and stranger) the random sentences will be, because you will have a bigger repository of chains to choose from.

Creating the chains
For each sentence, remove some punctuation, like double-quote marks. Other punctuation, such as commas, semicolons and periods, should be kept and treated as a separate word. 

Then, take all sequential sets of three words in the sentence and add it to the chain data. Goal is to be able to look up a chain quickly based on the first and second words, so you can pick a third word randomly.

A special code element (START) that marks which words can start a sentence. Also, remember that sentences may end with a period, question mark, or exclamation point.

Generating the text
To generate a random sentence, randomly choose a chain that begins with start code. In the above example, we would have to use the chain "(START) - The - happy" because our source text only has one sentence. So our first two words are "The" and "happy". Then, we continue by randomly choosing a chain that starts with the last two words generated ("The" and "happy"), which leads to "dog", because again there is only one possibility.

If you follow this procedure until you hit the period ("."), we will end up recreating our original sentence, which is rather boring. But if your chain database contains many branching possibilities, you will end up with silly sentences like these (chosen from among a generally more-nonsensical output set):
		Good things seem to be used which brings the feeling of completeness.
		Thirty spokes are joined together in a little child.
		Remaining aware of the Wise person acts from the stinging insects, wild beasts, and image less images, subtle, beyond all understanding.
		Whoever knows contentment will be death.
		Great projects are best started while they are too high.
These sentences are created from a public domain translation of the Tao Te Ching. 