---
title: "keyboard shortcuts - 0xb2? 0xac? what are they?"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by thom314 on 2007-01-19
Before I go in a blindly reprogram all the keyboard shortcuts....I see that many of them have default values like 0xe5, 0xb2, 0xa1. Just out of curiosity, what keys are these? How do I find out?

---

### Post by Buck2348 on 2007-01-19
> **thom314 said:**
> Before I go in a blindly reprogram all the keyboard shortcuts....I see that many of them have default values like 0xe5, 0xb2, 0xa1. Just out of curiosity, what keys are these? How do I find out?
I've been wanting to know that for some time.  I hope someone will tell us.  These are hexadecimal (base 16) numbers of two digits.  The 0x just indicates hex.  You can sometimes find what the number is that represents a particular key by opening the keyboard shortcuts applet, choosing a function that is disabled, click on the word "disabled", which will change to "new accelerator" and then press the key you want info on.  Not all keys come up with a hex code that way though.  

The whole business of key codes seems to be rather complex--there are raw scan codes, interpreted scan codes, ascii codes, and probably more.  You can play with the xev applet (type "xev" in a terminal) to see what you can find.  I have never found a code table that I can use to find a key when given its hex code.

Again, more help on this would be appreciated.

Buck

---

### Post by bladefallcon on 2007-01-20
> **thom314 said:**
> Before I go in a blindly reprogram all the keyboard shortcuts....I see that many of them have default values like 0xe5, 0xb2, 0xa1. Just out of curiosity, what keys are these? How do I find out?

I was just playing around withthe shortcuts on my keyboard. And when i tried to program one of the 'macro' buttons on the top, i got values such as Oxe5...So I would guess that those values are for macro buttons that some keyboard have. 

(Ie: my keyboard has buttons on the top above the f keys. Some are for the internet, to open and then to control thebrowser, some are to open and control media, and volume, etc..)

---

### Post by Geert Jan on 2007-03-06
See also [this thread](http://www.ubuntuforums.org/showthread.php?t=216948) about this issue.

Seems to me the Keyboard Shortcuts app is still quite user unfriendly, which is a shame.

---

