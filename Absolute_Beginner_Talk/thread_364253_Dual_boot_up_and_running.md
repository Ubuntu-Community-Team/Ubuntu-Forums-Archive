---
title: "Dual boot up and running"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by J11Gyro on 2007-02-18
Got the beast up and running good,except minor bug. How do I get all the older versions off boot list after the updates? the list keeps growing.

---

### Post by Muzik83 on 2007-02-18
Be careful with this one, not to remove the wrong package.

Use Synaptic (System -> Administration -> Synaptic) to remove all linux-image and linux-headers packages which you are NOT using.  I would recommend leaving the one you're using (the most current probably) and one version older installed.

-sean

---

### Post by tommcd on 2007-02-18
I assume you mean the grub boot list that you see when you first boot up ubuntu, is that correct? If that is true, then:
1) Back up the grub list first <sudo cp -i /boot/grub/menu.lst /boot/grub/menu.lst.bak>
2) To remove the old entries <gksudo gedit /boot/grub/menu.lst>
You can then remove older entries for the old kernels. The newest one is at the top, then the 2nd newest is below that, then the 3rd below the 2nd, etc. So to reomove the old ones start at the bottom of the "automagic kernels list". It is good to keep at least one older kernel for backup, just in case your current kernel gets screwd up, you can boot the older one. 
For everything you would ever want to know about grub:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
Sorry, I edited 1). It is correct now.

---

### Post by J11Gyro on 2007-02-18
Thanks Alot. I used the terminal and that worked great. 1 other question though, I am getting $home folder is being ignored warning at boot, is there anyway of removing it from splash screen?

---

### Post by J11Gyro on 2007-02-18
Ok got warning or error message fixed now it is time to play :) Thanks for the help with this total newbie.

---

### Post by tommcd on 2007-02-18
Glad to help. Just out of curiosity, did you find out what was causing that "$home folder is being ignored" error message on bootup? And if so, then how did you fix it?

---

### Post by J11Gyro on 2007-02-19
I went into my home folder and changed the permissions on it and it worked. heh I was grasping at straws and got lucky. Now all I have to do is set up the other members of the family accounts and will be done for awhile I hope. I refuse to give Microcrap any more money for un-secure non working OS's and plan on staying with Ubuntu. Although I am thinking of a Mac. :popcorn:  Thanks again for all the help.

---

