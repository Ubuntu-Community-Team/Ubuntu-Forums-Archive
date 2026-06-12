---
title: "Grub &quot;Unistall&quot;"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by vcvanillacoke on 2008-04-10
YES I want to actually unistall or remove GRUB. I just don't know how to do it. Hear me out....

I have a dualboot Windows/Ubuntu setup.
I have Acronis Disk Manager to load up either OS.

When I installed Ubuntu, I had no idea what exactly I was doing and managed to put GRUB on the partition where I installed Ubuntu.

Therefore, without Acronis, I was in a state of "WTF WHY WONT THIS **** WORK." Needless to say, Acronis makes dual booting very easy. I recomend it to those who have absolutely no clue how setup a dualboot.

So anyways, when I loaded up Ubuntu via Acronis for the first time I was like... "SO THATS WHERE GRUB IS HIDING."

To make the previous story very short... I have to go through two load screens(Acronis followed by GRUB) to boot up into Ubuntu. Call me lazy but having to push that ENTER key in GRUB or waiting 10 seconds is a big pain. 

So as you can see, I do actually want to remove GRUB if possible.

Any solutions would be very much appreciated.
I would be happy to provide any details needed.

---

### Post by Rhubarb on 2008-04-10
I'm not familiar with acronis boot manager.
As grub and other tools in ubuntu / ubuntu live CD can do pretty much whatever acronis boot manager can do, all for free.

Grub can let you dual boot into Ubuntu / windows fine, in fact it's very easy to get going from the ubuntu live CD (when you install Ubuntu, just tell it to re-size your existing windows partition, or resize you windows partition first, then tell Ubuntu to install to free continuous space).

IMHO your question shouldn't be how to remove grub, it should be how to remove acronis boot manager software and re-setup grub.

There's a few threads in the ubuntu forums that describe how to re install grub into the MBR, and tell it to detect windows and ubuntu easily.  - Do a search for it.

If you just want to use acronis boot manager and lessen the grub delay, you can edit your menu.lst file like so within Ubuntu:
Open up the Terminal within Ubuntu, and type this in:
```
gksu gedit /boot/grub/menu.lst
```
Find the line "timeout		3"
and change it to "timeout		0"

This will no longer display the grub menu upon start up, it will automatically enter into the default grub menu option upon start up.  So make sure that grub starts up on the menu item you want it to start up before you change anything in the menu.lst file.
Also doing this will prevent you from easily going into single user mode / performing memtests / passing other boot options to ubuntu.

I strongly recommend you ditch acronis boot manager, and learn how to use grub.
Or, at the very least, put up with the grub menu upon start up - if you run into any problems in ubuntu, it can be handy to go into single user mode / configure boot up.

*Edit: You can't get rid of grub, you can only stop it from displaying it's menu for x amount of seconds upon start up.  Grub is needed to boot the linux kernel and start up Ubuntu.*

---

### Post by vcvanillacoke on 2008-04-10
I will take your advice and reduce the timeout. My timeout is something ridiculous like 10 seconds.

---

### Post by lswest on 2008-04-10
yeah, or you can have a look at my how-to (link in my sig, second line) and see if that works, or, if it works, just leave GRUB there.  However, if you're going to remove Ubuntu, the grub files will be gone, resulting in an error 15 (or 17? not sure which error exactly)

---

### Post by Zralou on 2008-04-10
I would recomend setting the delay to something like 2-3 seconds, then you can at least catch 'safe mode' if you ever have problems.
Also, if you uncomment 'hidden' in your menu.lst, it won't display the boot menu unless you hit 'esc' within the 2-3 seconds.

Sara Lou

---

### Post by bodhi.zazen on 2008-04-10
You can do it either from windows or linux.

[http://ubuntuforums.org/showthread.php?p=4691608](http://ubuntuforums.org/showthread.php?p=4691608)

---

