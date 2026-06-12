---
title: "Help with 11.04 booting problem."
date: 2011-09-13
forum: Apple Hardware Users
---

### Post by FlameWorx on 2011-09-13
Hello, I have been trying to install Ubuntu 11.04 on mt Intel mac and have had a few problems but after a few nights of searching have came up with solutions. I have now come to a blank and no matter how many pages of help I work through I cannot get Ubuntu to load from refit. When I click on the penguin it goes into grub, I choose the standard option and it goes to a black screen with the flashing white cursor for a couple of seconds. Finally this pages gets slightly lighter in colour and stays like this. Please let me know where I am going wrong. I do have a suspicion it may be related to one of my earlier problems of getting the live cd to boot. The only way the live cd would boot was to press f6 on the meanu screen followed by esc and typing  “nouveau.noaccel=1&#8243;. Something to do with nouveau being in early  development, and it thinks it knows how to handle your video card but it doesn't apparently. The only reason I know this is because I read it from a forum, I am not the best with computers so any help would be much appreciated. Also it does exactly the same when pressing options @ startup and clicking the windows drive.

Cheers

---

### Post by a_meyer on 2011-09-13
I have had this problem before.  When the computer boots up, press the 'c' key.  Don't go into rEFI.  As soon as ubuntu starts to load press the ESC key.  This should take you to a screen with a few options.  You have to press F5 (or F6, which ever is labeled 'more options').  Disable apci and lapci and press enter.  Hopefully it will boot at this point.  

-Adam

---

### Post by FlameWorx on 2011-09-14
Thanks for the reply, I have manged to boot the live cd now and have installed it to a 40gig partition on my hard drive. Ubuntu wont boot from the hard drive now from refit or if you try to boot from the option (Alt) key. Any help would be appreciated.

---

### Post by FlameWorx on 2011-09-14
Can anyone one help with this problem please, I am not able to boot ubuntu from my macbook pro 5,3 hard drive. I created a 40gig partition and installed ubuntu from a live cd. When I try to boot ubuntu from refit or the options page (pressing ALT) it opens the grub screen, the normal option of ubuntu is selected and then it stays on a black screen with a blinking cursor.

---

### Post by mörgæs on 2011-09-14
Please don't create multiple threads. 
Threads merged.

---

