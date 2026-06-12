---
title: "console thinks I have a different keyboard"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by legolas on 2006-11-08
I have searched all week on the internet and can't find any clues to how to approach this.  When I go to a virtual console, it thinks my keyboard is different.  I just switched keyboards from a Japanese model to an American one so even though I changed the keyboard setting in the GUI, in the console it still thinks I have the Japanese keyboard.  How do I change the keyboard type in the console?  I tried once using the 
    sudo dpkg-reconfigure console-data
and I screwed up my keyboard so much I locked my self out of the system because I could not type!](*,) 
Is that what I need to use? If so, could someone point me to a link that describes which keyboard I might choose?
Thanks for ANY input or comments.

---

### Post by legolas on 2006-11-15
Ok, I did a lot of research and found out the main style of keyboard for personal computers is called qwerty (named after the letters at the top left of the keyboard.  So to choose a keyboard for your console, type:

    sudo dpkg-reconfigure console-data

Then you choose your qwerty keyboard from the list.

I found out the hard way, if you make a mistake and choose poorly, your keyboard will be the way you chose which may put you in a tight spot- not being able to type correctly.

---

