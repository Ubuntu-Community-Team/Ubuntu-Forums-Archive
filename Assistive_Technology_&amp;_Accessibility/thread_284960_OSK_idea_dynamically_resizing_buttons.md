---
title: "OSK idea: dynamically resizing buttons"
date: 2006-10-26
forum: Assistive Technology &amp; Accessibility
---

### Post by Henrik on 2006-10-26
I was playing with onBoard a bit today and I was wondering if typing speed could be improved by changing the size of the buttons. 

First I was thinking that more common buttons like E and S could be larger, but that does make the less common ones more difficult and may not be very efficient.

What if the buttons grew in size when you hovered over them in the same way that the OS X launcher does. Would this make it easier to stop on the button you wanted or am I fooling myself? :)

The most difficult part of the click is when you slow down to stop at the right key. Getting to the approximate area is easy but hitting the right spot at speed takes consentration. The zoom feature would likely not make the distance you have to move the mouse different, but it might make the visual part of the opperation easier by knowing when you are at the right place. I guess some trials should be conducted to decide whether it is the physical movement or the visual focusing that is the most difficult.

Now, what if we combine the two methods? Use the dasher algorithm to decide which keys should grow the most and stay large the longest depending on likelyhoods in predictive text.

Speaking of predictive text: one of the things I find annoying about existing systems is that you type in a few letters and then you have to pick a word from a list of 5-10 options. This takes your vision away from the keyboard and if the word you want is not there you have to type another letter and check back.

With zooming keys you could have one or more small words appear inside the zoomed key. If it's right then click in a special way to select it, if not just click and move on to the next key.

**Update:** Btw, we do have the technology for this in Ubuntu/Gnome today. See: [http://macslow.thepimp.net/?p=61](http://macslow.thepimp.net/?p=61)

---

### Post by frafu on 2006-10-27
> **Henrik said:**
> I was playing with onBoard a bit today and I was wondering if typing speed could be improved by changing the size of the buttons. 

First I was thinking that more common buttons like E and S could be larger, but that does make the less common ones more difficult and may not be very efficient.

What if the buttons grew in size when you hovered over them in the same way that the OS X launcher does. Would this make it easier to stop on the button you wanted or am I fooling myself? :)

The most difficult part of the click is when you slow down to stop at the right key. Getting to the approximate area is easy but hitting the right spot at speed takes consentration. The zoom feature would likely not make the distance you have to move the mouse different, but it might make the visual part of the opperation easier by knowing when you are at the right place. I guess some trials should be conducted to decide whether it is the physical movement or the visual focusing that is the most difficult.

Now, what if we combine the two methods? Use the dasher algorithm to decide which keys should grow the most and stay large the longest depending on likelyhoods in predictive text.


Personally, I don't like when a target moves under my pointer. Particularly, being also a MacOSX user, I have disabled the zooming function of the launcher (I suppose you are talking about  what is called dock in apple-speak) because I find it disturbing. 

Another point is that if the key under the pointer grows, it will cover part of the keys around it. Thus it will also cover part of the key that the user wants to click (let us call it target key) when the pointer has arrived at the key next to the target key. In other words, there will not be a real gain of the size of the target key because it is covered by the zoomed preceding key. 

Having static keys of different size based on their frequency could be an idea to delve into. But that will be different for each language. And would it really speed up typing considering that you have to pay special attention to the smaller keys. By the way, the onscreen keyboard being continuously resizable, the user can give it a size appropriate to his skill with the mouse. 

What about your idea of not zooming the key under the pointer; but zooming a few keys, namely the keys that are likely to be clicked next, based on a prediction algorithm? Again that would imply a dynamic keyboard. Will the extra attention needed to check whether the next key has been zoomed not make the user lose the time he might gain with a large key? 

I think that the typing speed is strongly related the length of the way that the pointer has to travel. The longer the way is, the more attention the user has to pay for not missing the target. In fact, I click two keys the fastest when they are located on next to the other. Maybe we should give up the layout of the hardware keyboard. (which if I am correct has been designed for technical reasons with exactly the opposite scope: placing the letters that are next to another in a word as far as possible apart from another) 


>  
Speaking of predictive text: one of the things I find annoying about existing systems is that you type in a few letters and then you have to pick a word from a list of 5-10 options. This takes your vision away from the keyboard and if the word you want is not there you have to type another letter and check back.
 

First of all, one has to different between: 
* word completion
* word prediction
* multiple word prediction 

I don't want to define exactly what they mean, because their meaning might differ with the different algorithms implementing them. But I would say vaguely: in word completion, each word is a stand alone; in word prediction, the different words are also related together, so that after typing a word 'w1', the algorithm proposes different words 'w2' that the user often types after word 'w1'. 

Moreover, I don't know whether it is the case for all people, but  using my onscreen keyboard with multiple word prediction since a long time, I know roughly how it behaves. For example I know that after the word 'in' the prediction engine automatically gives me the word 'the' among other words. So I don't move the pointer towards the 't' key; I look at once for the word 'the' in the prediction field. 

Further, I know that the engine that I am using strongly prioritieses recently used words. For example, because I have often used the words 'prediction engine' in these last sentences, I know that for the moment I need only 3 clicks to write 'prediction engine': after clicking on 'p' he offers me among others the word 'prediction' and after clicking on 'prediction' he offers me the word 'engine'. On the other hand, I know that I have to type more letters before the prediction engine offers me a word that I use seldom; in such a case, I only look at the prediction field after having typed a few letters. Of course, simetimes I have to go back and forth with the pointer because my estimation was wrong... 

>  
With zooming keys you could have one or more small words appear inside the zoomed key. If it's right then click in a special way to select it, if not just click and move on to the next key.
 

You are right, if the word you need is located around the spot where the user is looking, he is also able to see predicted words (for example when I am typing a letter in the upper row). But what size does a key have to be in order to place words into it? With the size that I give to my onscreen keyboard, each key has about 1cm2; it would really need a big zoom to place words into it! How many keys would be covered? 

We also have to consider the following: if the user has to do something complicated, he has to pay more attention and he gets tired faster. Moreover, doing something complicated, he is not aware of the time passing and he has the impression that he did it quite quickly, but in reality, he has spent much more time than he thought. (There was an experiment with the user interface of computers; unfortunately I don't remember what it was about (it was not accessibility related). The user had to do something in two different ways. The one way, which the user had the impression to have been the fast way, was in reality slower than the other way.) Of course, this can also happen to me: I have not done any experiments under measured conditions. 

>  
**Update:** Btw, we do have the technology for this in Ubuntu/Gnome today. See: [http://macslow.thepimp.net/?p=61](http://macslow.thepimp.net/?p=61)

That is good to know. :)


Finally, how do you find the responsivness of onboard. Sometimes, onboard ignores a click. It does so more often than keystrokes, but maybe it is because I use onboard remotely. keystrokes being more responsive, I tend to type faster on the keys.

frafu

---

