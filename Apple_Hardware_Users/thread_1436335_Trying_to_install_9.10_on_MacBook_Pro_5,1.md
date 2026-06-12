---
title: "Trying to install 9.10 on MacBook Pro 5,1"
date: 2010-03-22
forum: Apple Hardware Users
---

### Post by Falconer 2010 on 2010-03-22
I have just got the 9.10 Desktop Edition Disk from the internet and have installed rEFIt on my computer and it works.

I booted onto the disc using rEFIt but when I get to the option 'Try ubuntu', it shows the pulsating logo for like 1-3 minutes then it see very shortly

'Reading database....' or 'Removing guest session' and then my screen turns off, my computer is still on but the screen doesnt respond to anything.

Am I doing anything wrong?

---

### Post by Falconer 2010 on 2010-03-22
Update : Tried the 9.04 disk. No joy.

---

### Post by Falconer 2010 on 2010-03-23
BUMP please could anyone help?

---

### Post by Stoneface on 2010-03-23
I run 9.10 Desktop version on a MacBook Pro 5,3 in VMWare Fusion and I had no issues installing it. So it can be installed without issues on a Intel Mac with that particular hardware signature. Have not used rEFIT in combination with OSX SL and Ubuntu before though. So I can't really help you out. Maybe you should consult their forum as well..

---

### Post by Drenriza on 2010-03-23
Why do you want to run ubuntu on a apple computer?

---

### Post by linuxopjemac on 2010-03-23
Does it make a difference if you boot by holding the "c" after your press the power button and boing sound ?

---

### Post by buntuLo on 2010-03-23
i got exactly the same harware, and i use (k)ubuntu 9.10 64bit as my main OS on it: no troubles here running it from the livecd and installing it.

i would try to boot it from cd in single-user mode (safe mode?), connecting it to wired lan, updating&upgrading software packages; install the latest nvidia packages (i chose nvidia-195 from a specific PPA, but the version in the official repos works too); finally try to launch the gdm. if this brings you to the live X environment, i would proceed installing the OS.
otherwise you may try installing directly from the alternate cd.

anyway i'm puzzled, it's one year and a half that every ubuntu cd runs more or less smoothly on my hardware..
good luck, Lo.

---

### Post by alexmurray on 2010-03-23
Yeah, I used to run Ubuntu 9.10 64-bit on my MacBook Pro 5,1 (and now run Ubuntu 10.04 beta 64-bit) and it has installed fine every time... sorry I can't offer any real help - it should just work...

---

### Post by CCBalla10 on 2010-03-23
hmm that's odd, I'm running Ubuntu 10.04 on my macbook 5.1 (the only operating system I have installed on it) and it's running fine.  Can you explain again how you went about installing it?  I'll try and see if I can may offer some help.



Also, if you are just wanting to try Ubuntu you do not need rEFIt to run the live CD.  All you do is put the cd in the slot and when you hear the bong noise hold the "C" key until it boots from the cd.  Only time you might need rEFIt is if you are dual booting OS X & Ubuntu (but that is assuming you already have installed Ubuntu)

---

### Post by waysaz on 2010-03-26
> **Drenriza said:**
> Why do you want to run ubuntu on a apple computer?

'cause it's fun! (And it freaks people out.) :)

---

### Post by teejmya on 2010-03-27
Try to make a live CD on a USB flash drive. ([https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick))

That link is updated to Karmic (9.10). I know MacBooks can boot from USB, so it's worth a shot.

---

