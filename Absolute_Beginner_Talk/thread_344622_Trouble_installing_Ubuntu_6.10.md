---
title: "Trouble installing Ubuntu 6.10"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by rapattack1 on 2007-01-23
I have an amd machine that I normally have windows running on. I pulled out the hd and put another hd in it that has winxphome on it which I wish to erase and have Ubuntu on. Ofcourse it is not detecting all my hardware. I put the ubuntu cd in and it runs but not the "live" aspect. Well there it is mentioned and I clicked onto it but it was only info and nothing is happening. I don't see anything about install or live to click onto. Eventually this machine will have the two hd's. One with Ubuntu and one with windows so I will dual boot it. I hope I am explaining this ok .

---

### Post by mikewhatever on 2007-01-23
When booted from LiveCD, you should get Ubuntu desktop. There will be install icon, just click on it. What info exactly are talking about?
To help you dual boot with two HDs see here [http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)
To boot from a CD, make sure you have BIOS configured correctly.

---

### Post by rapattack1 on 2007-01-23
Nope there is no install button

---

### Post by mikewhatever on 2007-01-23
check out this guide [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by xpod on 2007-01-23
Have you rebooted with the cd in the drive??

---

### Post by rapattack1 on 2007-01-23
Yep I rebooted with the cd in the drive and I have read that page.

---

### Post by rapattack1 on 2007-01-23
Maybe I should format the dos way but I don't know if that is possible with xp?

---

### Post by mikewhatever on 2007-01-23
Have you tried running the CD when the HD with Windows is plugged in? I don't mean installing, but just to make sure the CD loads up properly. If it does, you can install with both HDs plugged.

---

### Post by rapattack1 on 2007-01-23
Might be an idea but I am not sure about the cables. If I have the right one to make the 2nd a slave. Looking now

---

### Post by mikewhatever on 2007-01-23
> **rapattack1 said:**
> Might be an idea but I am not sure about the cables. If I have the right one to make the 2nd a slave. Looking now

The HD with Windows should be Master as it was (the fist plug on data cable), the other drive should be Slave (the plug in the middle of data cable). Make sure the jumpers are set as master and slave. I've assumed you have two ATA HDs.

---

### Post by lyceum on 2007-01-23
If you cannot get the live CD to work, you need to work on that first. You can check the CD to see if it was a good burn, (the third? option down before it runs, first option , start or instal Ubuntu). You will need a minumum of 250 ram & i think 800 mgh CPU, if your stats are lower than that Ubuntu may not run.

---

### Post by rapattack1 on 2007-01-23
Thanks I am just taking a meal break as my brain has shutdown. 
I wrote the wrong response before and will do things now. Been on the computers too long](*,)

---

### Post by rapattack1 on 2007-01-23
Gee I tried something else and it is working. I am booting from the cd drive with the hd connected as a master that I want Ubuntu on.....working right now....thanks....will visit back when I want to do the dual boot thing....:-\"

---

### Post by mikewhatever on 2007-01-23
See what some food and drink, and break can do for you :D

---

### Post by rapattack1 on 2007-01-23
That is a good way of putting it. I wish I could take credit but a friend was sending me emails and he asked wether I tried to change it to boot from the cd drive...:lolflag: 
I guess with the questions it asks it is formatting my drive at the same time? I noticed that it is a long time between questions. This is there "where are you" part of it that I am up to.

---

### Post by rapattack1 on 2007-01-23
Yep the cable thing I am set about. I can't remember what drive types they are. I think ATA?

---

### Post by lyceum on 2007-01-23
> **rapattack1 said:**
> That is a good way of putting it. I wish I could take credit but a friend was sending me emails and he asked wether I tried to change it to boot from the cd drive...:lolflag: 
I guess with the questions it asks it is formatting my drive at the same time? I noticed that it is a long time between questions. This is there "where are you" part of it that I am up to.

Sounds like you've got it under control. It should be faster once it is on the hard drive. If not, throw in another fan or more memory. I spent $10 on a bigger fan and was amaized at how much faster it was. I set up my second (old) fan to blow right on to my video card and it just kept getting better. :D

---

### Post by rapattack1 on 2007-01-23
Well I have 700 or something ram and I think the cpu runs at 1.6gig. I do have a spare big fan that I could put in.
Gee it has spent 20 minutes on the 2nd question and is not moving forward....is that normal?

---

### Post by ako on 2007-01-23
> **mikewhatever said:**
> The HD with Windows should be Master as it was (the fist plug on data cable), the other drive should be Slave (the plug in the middle of data cable). Make sure the jumpers are set as master and slave. I've assumed you have two ATA HDs.

Can it be Master and the windows disk - Slave?
I am having the same problem as Ubuntu 6.10 does not go into installation on a disk where a Red Hat was previously installed. Ubuntu installation shows multiple error blocks on the disk and never goes any further.

---

### Post by lyceum on 2007-01-23
> **rapattack1 said:**
> Well I have 700 or something ram and I think the cpu runs at 1.6gig. I do have a spare big fan that I could put in.
Gee it has spent 20 minutes on the 2nd question and is not moving forward....is that normal?

When running from the disk, it can be a bit slow,but Ihave never waited 20 minutes. You may want to check the disk. But, if it is working, and you have nothing else to do..

---

### Post by lyceum on 2007-01-23
> **ako said:**
> Can it be Master and the windows disk - Slave?
I am having the same problem as Ubuntu 6.10 does not go into installation on a disk where a Red Hat was previously installed. Ubuntu installation shows multiple error blocks on the disk and never goes any further.

You have to load Windows first, which ever hard drive yoy put it on. Otherwize Windows destroys your boot loader. I really don't think it matters which one you put it on though.

---

### Post by mikewhatever on 2007-01-23
> **ako said:**
> Can it be Master and the windows disk - Slave?
I am having the same problem as Ubuntu 6.10 does not go into installation on a disk where a Red Hat was previously installed. Ubuntu installation shows multiple error blocks on the disk and never goes any further.

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902) This page has the scenario you want, if it doesn't, try otherwise. It should not matter.

---

### Post by rapattack1 on 2007-01-24
Oh thanks so much for the replies. Turns out the bios battery decided to die right at this time. After making several attempts on the install I tried to think back to when I last changed the battery and couldn't remember so I had a spare and it worked. Like a dream too. The 6.10 version of Ubuntu is unbelievably easy and even saw my winmodem....wow!!!! So now I will start working on a dual boot situation as a couple of people posted a link to help me with that. I have never done this before so I am crossing my fingers.:biggrin:

---

### Post by lyceum on 2007-01-24
awesome good luck, and enjoy!

:guitar:

---

### Post by rapattack1 on 2007-01-24
\\:d/

---

### Post by ako on 2007-01-29
The installation error was generated by an old CD ROM. After I replaced it to a new SONY one, installation went OK. :D 

Now another problem. Every time when I shut down the computer and turn it on again, Ubuntu loses its xserver - so after turning the PC on I cannot see the high screen resolutions. Therefore, every time I have to load as recovery option. 
Does anyone know what's the problem?

---

### Post by rapattack1 on 2007-01-30
Is someone using my Username. I did not write that last reply with my name. That is odd!

---

