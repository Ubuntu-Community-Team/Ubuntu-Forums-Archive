---
title: "Black screen on bootup - GeForce 8800"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by Aranthos on 2007-12-12
Ok, I've spent a while looking around here, and have found some people who seem to have had similar problems to me, but I think I'm missing something when people start explaining about command lines.

I've managed to install Ubuntu, which is a start.  If the text-based installer is the one that has no mouse support, is all in basic colours and in which everything is done by keyboard inputs, that is the one I used.  I am dualbooting with Windows XP Home, and am running an nVidia GeForce 8800GTS (which I have been informed by a friend at college is the problem).  My issue is this:  When I boot I get a menu that asks me to select between Ubuntu 7.10, Ubuntu 7.10 recovery mode, the 32-bit memory test, and Windows.  Whenever I boot into Ubuntu 7.10, I get a message about the kernel being aliove and directly mapping tables, then it goes black.  Graphics card driver issue apparently.  What I don't know is how to install the driver.  I have read [this thread]("http://ubuntuforums.org/showthread.php?t=591188") and as far as I can work out, I must select the Ubuntu 7.10 recovery mode, and type in the following once it has done all of its pre-flight checks:
```
nano /boot/grub/menu.lst
``` Is this correct?

The impression I get is that after typing this in, I will get a list of lines, one of which will be ```
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=43a49820-eae9-4b96-9f94-a81a2aadcb2c ro quiet splash
``` from which I have to remove "splash".  Here we go....  File: /boot/grub/menu.lst

Big bunch o' text, and at the bottom I have a grey box saying [ Read 161 lines ].  Yay.  So, I scroll down with the arrow keys, and find what is, as far as I can tell, the correct line.  Scroll to the end of it, and delete the word "splash" from it.  All good so far, now Ctrl+X, to save.  Hit Y to confirm changes, hit enter to confirm save, and we're off.  I'm now going to make the very bold assumption that because it says [ Wrote 161 lines ] it's saved my changes.  Type exit into the command line.  It does some checks or something, and I get a little cursor.  Ubuntu works.  It seems that just by typing this post, I have firgured it out.  Thank you so very very very very much Cowrecked and Therion.  You are proper :KS's

If you have the same problem as me, just read through this post and imagine if you were the person who typed it.  I really did stumble upon the solution.  Thanks again.  You made me think about it  =]

Now I've just got to try and remember my username and password.

BTW - RAWK!  :guitar:

---

### Post by Aranthos on 2007-12-12
Sorry, one other thing I forgot to mention, but I feel is important:

-= I did NOT use the Live CD, I had to install from the "alternate" CD, which lacked the Live capabilities.=-

Very important bit, that is  =]

---

