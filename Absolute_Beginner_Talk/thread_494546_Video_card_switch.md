---
title: "Video card switch"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by awiggin on 2007-07-07
Hello,

I am going to switch to a new video card that will work better with my machine.  I want a good, budget card that will be easy to install.

Can anyone give me some advice?  Before I buy one and install it, I need to know how I change the drivers and if I should do that before switching the card.  

Also, should I upgrade to Ubuntu 7.04 first?

Thanks in advance!

---

### Post by CautionaryX on 2007-07-07
What's your budget, current card, and slot type?

---

### Post by awiggin on 2007-07-07
My budget is around $50-75.

I don't know what kind of video card I have now.  When I look at my device manager in Windows, it says "Legacy Video Capture Device".  Is that it?

How do I find out what kind of slot I have?

Thanks and I'm sorry for being a total newbie.

---

### Post by awiggin on 2007-07-07
I think it's a PCI-E slot.  Does that make sense?

---

### Post by awiggin on 2007-07-07
Help!  Anyone?

---

### Post by djchandler on 2007-07-07
> **awiggin said:**
> Hello,

I am going to switch to a new video card that will work better with my machine.  I want a good, budget card that will be easy to install.

Can anyone give me some advice?  Before I buy one and install it, I need to know how I change the drivers and if I should do that before switching the card.  

Also, should I upgrade to Ubuntu 7.04 first?

Thanks in advance!

First, I would say to get a card with an Nvidia GPU. Whether or not you need to change the drivers depends on what you are switching from. People are still having troubles with ATI.

I second what the second poster said.

An easy way to get a new xorg.conf is to boot the Live CD and copy it to a shared folder that has absolutely no restrictions on the hard drive, or something like a USB thumb drive. I like the shared folder because you don't have to worry about possibly having to mount a USB device manually later. The shared directory should be set up before the card switch, in the main filesystem directory, which must be done by su. You can use nautilus as su by hitting "alt-F2" and entering

gksu "nautilus"

in the command line dialog box. Make sure you re-assign the ownership of the folder to your account, and then give create/delete and read/write permission to your main account (so you can change it easily later), your group, and others, all the way down. You will be able to write to this directory later when you boot the Live CD.

After switching video cards, boot the Live CD, become su in nautilus as you did above. Under filesystem, find /etc/X11/xorg.conf. Copy xorg.conf to the shared directory you just made on the hard drive.

Remove the Live CD. Reboot from the hard drive. If you make it into the GUI, you have it made.  Log in, become su in nautilus again, rename the old xorg.conf file in /etc/X11 to something else, and copy the new xorg.conf from the shared folder /etc//X11.

If X windows doesn't work, you'll get an error screen. Don't worry. It's still easy.

Login to your main account from the command line interface. From here on it's real easy. At the prompt, enter

*cd ..*

twice to move you to the main directory, then

*sudo  mv /etc/X11/xorg.conf oldxorg.txt*

After entering your password, the old xorg.conf should be renamed. If you want to be sure you *cd /etc* then *cd /X11* then *ls old*.**
and you should see oldxorg.txt. Now 

*cd ..*

twice to move you to the main directory, then

[I]sudo cp /shareddirectory/xorg.conf /etc/X11
[/I]
enter your main account password again and you're done. To make sure, do the same thing as above to get into the /etc/X11 folder, then enter *ls *.conf* and the only thing you should see is the new xorg.conf

at the prompt enter *sudo shutdown now*

to stop all processes, then re-boot.

I think I remembered the whole thing right. Sometimes when you get used to doing something, you may have a tendency to overlook one small yet significant step.

D.J.

PS If I made something unclear or incorrect above, forgive me, I'm falling asleep at the keyboard. Good night!

---

### Post by djchandler on 2007-07-07
There is a program called sysinfo. Make sure it is installed and available under System Tools in the Applications menu. It will tell you everything we need to know.

---

### Post by djchandler on 2007-07-08
Hey awiggin,

Did I scare you off? I'm sorry if I did. If you already have a PCI-E Nvidia video card, its way easier, because the driver should be identical. Nvidia drivers are what is called "monolithic." I know this is true for Windows, and from what I've seen, the same is true for Linux. It could be as simple as taking out the old card, and putting in the new one. I wrote my post before I saw you say you had PCI-E.

As for finding something better within your price range, that depends on what you already have. If you have a motherboard with graphics built-in, almost anything that fits in the PCI-E slot is probably better than what you have. It's easy to tell if you are using on-board graphics and sharing memory with it. The 15 pin connector for your monitor will be in the same vicinity as all your other ports (USB, mouse, keyboard, ethernet, sound device inputs and outputs). :guitar:

DJ

PS please mark as solved if you have reach a decision.

---

### Post by awiggin on 2007-07-08
Hey DJ-

Thanks for the tips.  Your first post did intimidate me a bit, but I would have worked through it.

Anyhow, I have bought an nVidia 7300.  After seeing your last post, I am sure that my motherboard does have the graphics built in, because it's just like you said.  The connector is right by all the other stuff.  I will put the new video card in and let you know how it works.

So, I don't have to load the drivers or anything into Linux before plugging in my new vid card?  I can just plug it in and go?  I hope you are right because I am eager to experience this new card.  So far, with Linux (and with Windows to some degree) the video has been shite with this current set up.

Thanks.

-awiggin

---

### Post by djchandler on 2007-07-08
> **awiggin said:**
> Hey DJ-

Thanks for the tips.  Your first post did intimidate me a bit, but I would have worked through it.

Anyhow, I have bought an nVidia 7300.  After seeing your last post, I am sure that my motherboard does have the graphics built in, because it's just like you said.  The connector is right by all the other stuff.  I will put the new video card in and let you know how it works.

So, I don't have to load the drivers or anything into Linux before plugging in my new vid card?  I can just plug it in and go?  I hope you are right because I am eager to experience this new card.  So far, with Linux (and with Windows to some degree) the video has been shite with this current set up.

Thanks.

-awiggin

If you had the nvidia 6100 graphics built in the motherboard, you may be just fine. If so, you may want to go under the restricted drivers setting under System Administration and load the Nvidia proprietary driver. It's real easy to go back if something hangs.

A word of advice: the system recovers better from a power failure than it does when pushing the reset button--can't write something nutty to the hard drive and scramble anything. If it hangs, either turn off the switch on the back next to the power cord connector or unplug the computer. Turning off the power on a power strip/surge protector your computer is plugged into works too.

If it is an intel or ati chip set, x server may not start, and you will have to take the video card out and do all that other stuff. Good luck! 

DJ

---

### Post by awiggin on 2007-07-08
OK, here's where I am.

I plugged in the card and things are working in Windows.  Sort of.  The main reason I got the card was that videos in Windows were too dark and I had no way to correct that.  I can correct it now using the nVidia Control Panel, but I can't get the screen brightness right for everything else.

Anyhow, that's another problem.

When I went to boot up Ubuntu, I didn't get anything.  It didn't go to the GUI at all, just a DOS-type screen that told me xorg was screwed up.  

I suppose I could defrag my hard drive and install Feisty from a live CD.  Do you think that would work?  Or is there a better solution? 

Keep in mind - I'm a total noob.

Thx.

-awiggin

---

### Post by awiggin on 2007-07-09
bump

---

### Post by djchandler on 2007-07-09
> **awiggin said:**
> bump

Here I am! I was working earlier (from home) and then I had some interesting email, but I am here now. This is where my previously intimidating posts come in. Go back to the one where I tell you to boot from the Live CD, or you might call it the trial or install CD. Anyway, it is the one you used to install Ubuntu in the first place. Just take it one step at a time, and we will get a new xorg.conf copied into the right folder for you, which is found in /etc/X11. That is a capital "X" in front of the 11. Linux is very particular about case.

One thing I should ask first, is how much personal data or customization have you done so far? It may be far easier than following my instruction below to just install over the old installation. You will have to find and zero out the partitions where Ubuntu is with out taking out the primary  NTFS (Windows) partitions. You may want to use the administrative tool called Computer Management in XP, Go down to Storage, then Disk Management, select the hard drive that Ubuntu is on (if you have more than one hard disk connected) and just delete the partitions that are **NOT** marked NTFS or FAT 32 or FAT 16. **Anything marked as unknown or NFS is Linux, and you may delete them if you are going to re-install the system.**

If you don't want to re-install, here's the intimidating part again. Just print this out, and follow it step by step. Use a highlighter or something after you have completed a step and mark over it. If the computer hangs or gets stuck stuck, turn off the computer by disconnecting the power, like turning off the switch on the powerstrip/surge protector you have your computer plugged into. Or just unplug the computer. **Whatever you do, don't hit reset after booting from the hard disk. **If you booted the Live CD, it doesn't matter, just tell it to shut down.

This will be easier if you put the old video card back in. If you can't do that, the first part of what I'm telling you to do here will be a lot harder. Let me know if you can't or don't want to put in the old video card, and I'll have to tell you how to copy files to and from a floppy disk, which I think is a lot more trouble than putting back the old video card.

**This part is with the old video card in place.**

boot from the Hard Drive

You can use nautilus as su by hitting "alt-F2" and entering

gksu "nautilus"

in the command line dialog box.

Make a new folder. Let's call it **fullshare**

Right click on **fullshare** and go down to properties and left click
Click on permissions and you should see this window - substitute your main account name for mine - I am djc 
[ATTACH]37769[/ATTACH]


The main thing is to make sure that **others** have **create and delete** as well as **read and write** permissions.

Close the dialog box after giving yourself and everybody else full permissions

Shut down!

**Now put the new video card in.**

After switching video cards, boot the Live CD

Become su in nautilus as you did above.
Under filesystem, find /etc/X11/xorg.conf.
Copy xorg.conf to the **fullshare** folder you made on the hard drive.

After copying xorg.conf to **fullshare**, shutdown. Remove the Live CD. Reboot from the hard drive.

If X windows doesn't work, you'll get an error screen with text only. Don't worry. It's still easy.

Login to your main account from the command line interface. Enter your main account name, press **enter**. Enter your main account password, press **enter**. From here on it's real easy.

At the prompt, enter

**cd ..**

twice to move you to the main directory, (there's a space between cd and the two periods) then

[B]sudo mv /etc/X11/xorg.conf oldxorg.txt
[/B]
After entering your password, the old xorg.conf should be renamed. If you want to be sure you **cd /etc** then **cd /X11** then **ls old*.***
and you should see oldxorg.txt. Now

**cd ..**

twice to move you to the main directory, then

**sudo cp /fullshare/xorg.conf /etc/X11**

enter your main account password again and you're done.

To make sure, do the same thing as above to get into the /etc/X11 folder, then enter ls *.conf and the only thing you should see is the new xorg.conf

at the prompt enter

**shutdown now**

If everything went well, you'll find yourself at the log-in in no time.

DJ

---

