---
title: "ubuntu wont boot"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2006-10-17
I have just installed it and started configuring wireless. I restarted it and now I can't get past the screen after when I sign in, like the splash screen never shows up and it just sits there. How can I fix this?

---

### Post by dbd on 2006-10-19
No idea. Did you change anything strange when configuring wireless?

---

### Post by ReaderRat on 2006-10-19
> **fuzzyhair said:**
> I have just installed it and started configuring wireless. I restarted it and now I can't get past the screen after when I sign in, like the splash screen never shows up and it just sits there. How can I fix this?
Boot the Live CD to Recovery Mode, and run this in Terminal:
```
sudo dpkg-reconfigure xserver-xorg
```
and see if this fixes it.

---

### Post by devnulljp on 2006-10-19
You've killed your xserver configuration
Try this:
Cntrl-Alt-F1
Should dump you to a terminal
Then type 
```
sudo dpkg-reconfigure xserver-xorg

```
Then restart X (or reboot)
```
sudo /etc/init.d/gdm restart
```

---

### Post by jkvv_1973 on 2006-10-20
> **devnulljp said:**
> You've killed your xserver configuration
Try this:
Cntrl-Alt-F1
Should dump you to a terminal
Then type 
```
sudo dpkg-reconfigure xserver-xorg

```
Then restart X (or reboot)
```
sudo /etc/init.d/gdm restart
```


Thanks alot this worked for me!;) 


1.I couldnt Load LIVE CD (kernel panic bla bla errors) even in safe mode (this was all after I installed ATI drivers via EASYUBUNTU <tsk tsk
2.frequency overange on hard drive boot after grub black out...

what I did...(for the clueless)

-ctrl+alt+f1 on load up (again and again and...)
-got terminal login (user + password entered)
-got terminal/login prompt
-typed your commands
-went through questions accepted all defaults
-voila im here typing this message...


although I still have the problem of changing resolution...everything looks small 1280x1024 

I still need help...

update
problem solved...went through steps again and x out the res I didnt need...ahhhh this feels good...Im a troubleshoot junkie...now I can go on with my life...:neutral:

---

### Post by devnulljp on 2006-11-06
Glad it worked for you. I've always found X configuration to be a minefield, especially with ATI GPUs.

---

### Post by StaJs on 2006-11-06
> **jkvv_1973 said:**
> 


1.I couldnt Load LIVE CD (kernel panic bla bla errors) even in safe mode (this was all after I installed ATI drivers via EASYUBUNTU <tsk tsk
2.frequency overange on hard drive boot after grub black out...

what I did...(for the _clueless_)

-ctrl+alt+f1 on load up (again and again and...)
-got terminal login (user + password entered)
-got terminal/login prompt
-typed your commands
-went through questions accepted all defaults
-voila im here typing this message...


I'm having the same problems too. Just _when do you _"**ctrl+alt+F1**"?
I was getting nowhere, so I wiped the HD clean to start over and now the CD still won't boot! What gives?? I get "Kernel panic - not syncing: Out of memory and no killable processes..."

---

### Post by DaveBorealis on 2006-11-06
> **StaJs said:**
> <snip>so I wiped the HD clean to start over and now the CD still won't boot! What gives?? I get "Kernel panic - not syncing: Out of memory and no killable processes..."

Are you sure you're actually booting from the CD and not the hard drive?  Not sure what you mean when you write that you "wiped the HD clean".

Best regards,
Dave

---

### Post by StaJs on 2006-11-06
> **DaveBorealis said:**
> Are you sure you're actually booting from the CD and not the hard drive?  Not sure what you mean when you write that you "wiped the HD clean".

Best regards,
Dave

I formated it. Nothing on it now (had Ubuntu on it). BIOS is set to boot from the CD and nothing else as well. Still the CD won't boot now.

---

### Post by DaveBorealis on 2006-11-06
If you were able to boot from the live CD before you tried to install, and now you cannot boot from the same live CD, then I would guess that the CD has errors on it from the burning process.  Which also might explain why you had trouble installing.

If you want, try making a new CD, burning it at a slow rate, and see what happens.

---

### Post by StaJs on 2006-11-06
Other liveCD distros I had laying around did the same thing!
Reformated the drive and now the Ubuntu CD works again.
I'm now reinstalling, see what happens.

---

### Post by StaJs on 2006-11-07
Locked up again, now I'm back to square one. I've never had so much trouble with a Linux distro like I'm having with this one!

---

### Post by DaveBorealis on 2006-11-07
> **StaJs said:**
> Other liveCD distros I had laying around did the same thing!

If other distros aren't working either, then I'd be thinking hardware failure.  You could easily swap out the CD drive, assuming that you have an extra one handy, and see what happens.  Wouldn't be a bad first thing to try on the hardware side of the problem solving.

---

### Post by StaJs on 2006-11-10
Bad memory, all is well now. Sheesh . . . . .

---

