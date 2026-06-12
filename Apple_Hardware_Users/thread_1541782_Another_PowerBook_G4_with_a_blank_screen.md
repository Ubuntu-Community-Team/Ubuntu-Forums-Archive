---
title: "Another PowerBook G4 with a blank screen"
date: 2010-07-29
forum: Apple Hardware Users
---

### Post by rjmusto on 2010-07-29
Ubuntu 10.04 + PowerBook G4 12"

I've read through some other posts on this, but am still a bit lost. No expert I'm afraid.

The live CD worked fine and the initial install also was fine, but subsequent boots seem to run ok but leave me with a blank screen.

I've tried booting with qualifiers I've seen such as "Linux video=ofonly" etc, but no success.

I've also seen post modifying the xorg.conf file, but have no idea how to do that from the boot prompt.

Any assistance much appreciated.

---

### Post by svtguy88 on 2010-07-30
What exactly do or do you not get on the screen?  Any sort of terminal output that looks like Linux loading (it would be white text on a black screen)?

If the LiveCD worked fine for you, you can boot to that, mount your internal hard drive and edit the Xorg.conf file (/etc/X11/Xorg.conf).

---

### Post by rjmusto on 2010-07-30
The screen is completely blank.  I get the Ubuntu chime and I have the feeling it has completed the boot-up except that the screen is blank. 

Ok, I'll try booting up via the live CD.

Since the live CD itself works fine, can I copy the settings it is using from somewhere and modify the xorg file to match?

Thanks.

---

### Post by rjmusto on 2010-07-30
Update:

Have managed to use the live CD to create an xorg.conf file copied from this post
[http://ubuntuforums.org/showthread.php?t=1507389&highlight=powerpc+blank+screen&page=2]("http://ubuntuforums.org/showthread.php?t=1507389&highlight=powerpc+blank+screen&page=2")
and that got it working in 'low res' mode. Then installed the neaveu(?) driver and it seems to now be ok. 

Thanks pkmgarf for your help.

---

### Post by svtguy88 on 2010-07-30
Glad things are up and running.

---

