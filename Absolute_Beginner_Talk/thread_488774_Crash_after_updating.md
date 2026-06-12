---
title: "Crash after updating"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by whiskeysquared on 2007-06-30
Alright, I updated my system today 6/30/07.  I think there was an update for automatix and drivers on my system - not sure what it was called, I just remember reading, "non-free" or something to the affect.  But then when I went to restart the system, it won't load x11, it sends me to the config screen and dumps me at a command line.  I had everything set up perfectly for my monitor, which was hard (1440x900) and I don't want to go through figuring that out again.  I restarted because, firefox (again, after an update on firefox) started acting strange.  My add-ons weren't functioning right.  I used the FEBE plugin originally to transfer my profile from windows over to my ubuntu firefox profile.

Help.

---

### Post by chamberlain2006 on 2007-06-30
Automatix is sometimes known to break your system after updates.  (And I know people are going to come on saying "oh that's not true, automatix is awesome", but it's the truth).  Automatix isn't a preferred method to do things.  What does the X server say when you try to load it?

---

### Post by whiskeysquared on 2007-06-30
It says:
```
FATAL:  Could not open '/lib/modules/2.6.20-16-generic/volatile/nvidia.ko': No such file or directory

(EE) NVIDIA(0):  Failed to load NVIDIA kernel module!
(EE) NVIDIA(0):  ***Aborting***
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

Like I said, I've restarted before since I went through the pain of getting my monitor right, and nothing like this happened.  Did the NVIDIA driver update cause this?  Is there a way to restore the configuration BEFORE the update?

Thanks.

---

### Post by chamberlain2006 on 2007-06-30
How did you install the Nvidia driver?

---

### Post by whiskeysquared on 2007-06-30
I'm pretty sure through automatix.  Cause nothing else worked for me.

---

### Post by chamberlain2006 on 2007-06-30
Ok.  First of all, turn on your computer, and click ESC when GRUB starts loading and counting down.  Then type:

sudo nano /boot/grub/menu.lst

Then, go down to the "Device" section and change "nvidia" to "nv".  Then click CTRL+O to save it, and then CTRL+X to close.  Then type "reboot" to reboot.  Hopefully you should at least be in a graphical environment now.  If you want I can also try to help you get your card working properly the normal, non-automatix way.

---

### Post by whiskeysquared on 2007-06-30
When I hit ESC during the GRUB load sequence, I just get taken to the GRUB menu where I can choose an OS to load...  I don't get taken to a command line.

---

### Post by chamberlain2006 on 2007-06-30
Whoops forgot to mention that you have to go down to second entry and click "enter".

---

### Post by chamberlain2006 on 2007-06-30
Oh my goodness, what is with me today?  Instead of typing "sudo nano /boot/grub/menu.lst" it should be "sudo nano /etc/X11/xorg.conf".  Sorry!

---

### Post by whiskeysquared on 2007-06-30
No graphical interface, still saying x server is dead...

EDIT:  Went back into xorg.conf and I see that I changed the description too.  Now I'm getting my GUI...

---

### Post by whiskeysquared on 2007-06-30
So now, how do I get it back to working properly.  Because my NVIDIA settings menu under Applications - System Tools is back to being just one window with no options.  And I now have a void in my screen just a big bar of black that's not filling up.

---

### Post by chamberlain2006 on 2007-06-30
Yupp.  You can actually install a program called "Envy" that will do it all automatically.  Get it [here]("http://www.albertomilone.com/nvidia_scripts1.html").

---

### Post by whiskeysquared on 2007-06-30
Ahhh...  Envy, last time I installed envy it hosed my system.  That's the reason I switched to trying automatix.

---

