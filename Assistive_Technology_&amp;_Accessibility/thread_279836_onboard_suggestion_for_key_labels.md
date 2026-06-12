---
title: "onboard suggestion for key labels"
date: 2006-10-18
forum: Assistive Technology &amp; Accessibility
---

### Post by frafu on 2006-10-18
Hello, 

I have seen that the size of the letter in the keys of onboard is coded in the xml file of the keyboard layout. 

Would it not be possible to implement it dynamically? When the keyboard is resized, onboard would get the height of the keys and size the letter that labels the key accordingly. For example computing the size of the font to write the key label to be 4/5 (if this ratio makes sense) of the height of the key. 

By using this method, there will probably be a problem with the label of the modifiers because they will not fit anymore into the key. Can't you simply replace the word in the modifier with a scalable symbol?

frafu

PS: @t0rtois3 and Henrik

Please, don't get me wrong because of the different threads that I have opened with the problems I encountered using onboard. I and very probably other people appreciate what Henrik and you have done so far and plan to do with onboard. 

By the way, is there a way I can change the title of a thread to include for example the word 'solved' in order to indicate that the problem of the thread has been solved?

---

### Post by t0rtois3 on 2006-10-19
It looks quite odd to the eye having different size fonts for different keys.  

Also i'm not sure if there is a way to get the size of each label from cairo (the graphics library i'm using).  

It could be done by the number of characters though.  Having one size for one character long labels and a smaller size for two and longer length labels. 

thanks Frafu it's good to have a user that tests onboard so thoroughly, you've been a great help.

---

### Post by frafu on 2006-10-19
> **t0rtois3 said:**
> It looks quite odd to the eye having different size fonts for different keys.  

It could be done by the number of characters though.  Having one size for one character long labels and a smaller size for two and longer length labels. 
 

Sorry, I think I made a mistake. I thought that the font tag in the keyboard file was the size of the font. Now I suppose it to be the minimum fontsize to use!? 

I agree with you that having different size fonts for different keys would be odd. The keys of the default keyboard having all the same height, I forgot to consider that with onboard, it is possible to have keys of different heights. 

Now, I have set font='9' instead of 5 in the keyboard file, because otherwise, the single letter label on the keys were barely readable with the size I usually give to onboard. It is not ideal because some multiletter labels do not fit anymore into the key, but it is better than before where I had in part to guess the label. 

>  
thanks Frafu it's good to have a user that tests onboard so thoroughly, you've been a great help.

I am glad that I can help.

---

### Post by t0rtois3 on 2006-10-19
The number is multiplied with a number worked out by looking at the keyboards width and height to get the actual font.  So a bigger font number will make the font bigger in all cases.

Chris

---

### Post by frafu on 2006-10-20
Hello, 

Thanks for your reply. 

Don't you think that using the width and height of the keyboard to compute the fontsize is a bit unprecise?

What about parsing the .svg file to get the width and height of each key? 

frafu

---

### Post by t0rtois3 on 2006-10-21
You can resize onboard out of ratio to the svg file.  I could try and find out the size of the key but I think all the labels being different sizes would look odd.

Chris

---

