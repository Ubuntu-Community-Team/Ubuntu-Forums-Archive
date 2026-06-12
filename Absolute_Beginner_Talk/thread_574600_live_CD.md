---
title: "live CD"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by n88n on 2007-10-13
I thought I would give Linux a spin.  I currently run XP.  

I downloaded ubuntu-7.04-desktop-i386.iso in hopes to make a "live" CD that I could boot from just to take a look at what ubuntu has to offer.

created a bootable disk from the iso I download, but when I boot off that CD I get some strange DOS command prompt, not a gui OS.

What am I doing wrong?

thanks!

Nate

---

### Post by FuturePilot on 2007-10-13
Does it say something like ubuntu@ubuntu~$? What's your graphics card? It could be that it can't start X.

---

### Post by n88n on 2007-10-13
thanks for responding.

Not sure what "x start" means.

I am running an IBM thinkpad T42... with ATI MOBILITY RADEON 7500

thanks!

---

### Post by alienexplorers on 2007-10-13
X start or X refers to the GUI you get when Ubuntu boots up (Except server edition).

---

### Post by jerrynewt on 2007-10-13
Try this -- go to where ever you downloaded the iso file and right click on it. Select "write to disc". Make sure your bios is set to boot from the cd first, insert the new cd and reboot. Works for me everytime!!

---

### Post by n88n on 2007-10-13
that for the write to disk trick, I will take a shot.

just to try and clear up what I see when I boot from the disk I made....


Caldera DR-DOS 7.03
[DR-DOS] A:\

---

### Post by Steveway on 2007-10-13
> **n88n said:**
> that for the write to disk trick, I will take a shot.

just to try and clear up what I see when I boot from the disk I made....


Caldera DR-DOS 7.03
[DR-DOS] A:\

Well, you burned it wrong.
Here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
That should explain how you do it right.

---

### Post by Rabindranath on 2007-10-13
Burn the disk with "Infra recorder". Dont burn with nero. 
[http://www.softpedia.com/get/CD-DVD-Tools/Data-CD-DVD-Burning/Infra-Recorder.shtml](http://www.softpedia.com/get/CD-DVD-Tools/Data-CD-DVD-Burning/Infra-Recorder.shtml)
And you should change the 1st boot device priority from your hard disk to your dvd drive. Usually done by clicking 'del' during booting...

---

### Post by n88n on 2007-10-13
that was it!!!!

I just got out of linux.  The last two comments were correct.  The guide said to use "Infra recorder" and after I created the CD image with that program ubuntu booted right up.

I was pleasantly pleased with what I saw.

Now I just have to figure out how to make a usb drive bootable because I have a odd terminal PC that has a corrupted XP install.  The device is real cool, but there are no drives or ports other than a usb port.  I figure if I could get that thing to boot linux from the usb key I could get it to boot into Linux and I could get some use out of that device.

thanks for all you help ppl.

Nate

---

