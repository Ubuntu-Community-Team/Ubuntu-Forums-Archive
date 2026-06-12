---
title: "Problem w/ a few keys"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by Europa2010AD on 2007-03-31
I have a MS Natural Keyboard (the most plain and simple model -- w/o any special function keys). For some reason, when I try to type the double quote (") or the tilde (~), I always have to press the keys twice before they'll show up on screen. And the double quote that shows up on screen doesn't look right neither (it's a double quote alright, but just doesn't look normal... it appears as if it's a special character).

In fact, it seems to me that after pressing the key once, the system is waiting for me to input some other commands -- for example, I would press tilde (~) once, then, say, I press the letter "a" -- I would get a system beep and nothing shows up on screen.

I have my keyboard profile set to "MS Natural Keyboard" and the input layout to "U.S. International". I have tried the rest of the U.S. input layouts and the problem persists. I tried the default generic keyboard profile as well. 

Does any one have any idea how I can solve this issue? Any help would be greatly appreciated!

---

### Post by mlissner on 2007-04-02
You might try installing and experimenting with xkeycaps. I've found it useful in the past when I was converting my caps lock key to a backspace key. Though it's somewhat ghetto, it can be enlightening. 

Once you figure out the problem using that, you can use xmodmap to fix it permanently (or so my theory goes).

---

### Post by freebird54 on 2007-04-02
What you seem to have are 'dead' keys - that you press first, then when you press another their effect is 'combined'.  For instance, hitting single quote, then e should give you a french e with a right tick above it.

The layout you are looking for should be US English.  But I am not sure of the best way to get it back.  I'm sure there is something other than reconfiguring your xserver!

Hang on - an expert will get to you  :)

---

### Post by Europa2010AD on 2007-04-03
> **freebird54 said:**
> What you seem to have are 'dead' keys - that you press first, then when you press another their effect is 'combined'.  For instance, hitting single quote, then e should give you a french e with a right tick above it.

The layout you are looking for should be US English.  But I am not sure of the best way to get it back.  I'm sure there is something other than reconfiguring your xserver!

Hang on - an expert will get to you  :)

You´re right, when I press single quote + e, I get this --> é.

I figured out how to solve the problem.  You see, when I look at the keyboard layout options, I see US English. But because there's a little arrow next to it, I intuitively thought I have to double click on it to expand it out, and only choose from the ones under "US English" --> US International, Dvorok, whatever.

It turns out I don't have to expand it out and simply choose US English, and now I don't have any problems with the quote or tilde keys any more!

Thanks for help guys! Really appreciate it!  :)

---

