---
title: "Can't boot with Macbook Pro."
date: 2007-04-29
forum: Apple Intel Users
---

### Post by rgrasell on 2007-04-29
I'm trying to run the LiveCD for 7.04 on my MacBook Pro.  Every time I boot up with the disc in the drive, the laptop spits it out.  No matter if I hold down the "C" or option keys, the cd is spit out and it boots to Mac OS.  I set the computer to boot to the CD default -- still doesn't work.  Any help is greatly appreciated!  Please note that the exact same cd boots with my friends Macbook (not pro).

---

### Post by ronocdh on 2007-04-29
> **rgrasell said:**
> I'm trying to run the LiveCD for 7.04 on my MacBook Pro.  Every time I boot up with the disc in the drive, the laptop spits it out.  No matter if I hold down the "C" or option keys, the cd is spit out and it boots to Mac OS.  I set the computer to boot to the CD default -- still doesn't work.  Any help is greatly appreciated!  Please note that the exact same cd boots with my friends Macbook (not pro).
I wager the burn is bad. Try creating the disc with a program like **Burn**, which I personally found [here]("http://www.opensourcemac.org/"). After burning the image to disc, the program will automatically verify the integrity.

Good luck, and please post back with your results.

---

### Post by rgrasell on 2007-04-29
Still no go!  I've had problem's with P-ram before (an apple guy had to reset it).  Should I reset it, and can that destroy any of my data?

---

### Post by ronocdh on 2007-04-29
> **rgrasell said:**
> Still no go!  I've had problem's with P-ram before (an apple guy had to reset it).  Should I reset it, and can that destroy any of my data?
Hm, if you've a history of hardware problems then I think it's rather likely that's the case again. On a Mac it really is as simple as holding down C to boot from a CD. To test, I would get out your OS X installer DVD and try to boot from that. If that doesn't work, contact Apple or make a trip to the nearest store.

---

### Post by rgrasell on 2007-04-29
Installer DVD works, just not Ubuntu!

---

### Post by Chrisj303 on 2007-04-29
If you want to try resetting your PRAM : [http://docs.info.apple.com/article.html?artnum=2238](http://docs.info.apple.com/article.html?artnum=2238)

Are you mounting your ubuntu image when burning?

It's no good just copying an .ISO/.DMG to a blank cd - you need to mount it first,then burn.

I use TOAST (mac osx) - just drag and drop the ubuntu umage into it, making sure to select the 'MOUNT' option that appears.

Hope that is some help.

---

### Post by rgrasell on 2007-04-29
I reset the P-RAM and it booted once!  From there i was easy to install fglrx and startx.  But it doesn't work anymore.:confused:   What the heck is going on.  I rebooted to see if the disc would work again and it didn't.  How weird.  I'm still trying to find the source of the problem.

---

### Post by ronocdh on 2007-04-30
> **rgrasell said:**
> I reset the P-RAM and it booted once!  From there i was easy to install fglrx and startx.  But it doesn't work anymore.:confused:   What the heck is going on.  I rebooted to see if the disc would work again and it didn't.  How weird.  I'm still trying to find the source of the problem.
OK, this is indeed a problem, but does this mean your Ubuntu installation works? You should be able to hold down the Option key during boot and choose Linux. (Alternatively just grab rEFIt and use that as a bootloader.)

---

### Post by rgrasell on 2007-04-30
But I haven't installed it to the hard drive yet...

---

### Post by Nasiom on 2007-04-30
Hi,

Have you install Apple's BootCamp?  

This install the BIOS compatibility module on top of EFI, that could be the reason why it refuses to boot from the CD/DVD.

Also you should use BootCamp Assitant to partition your disk live, it'll be easier then.

Just a thought

-Nasiom

---

### Post by rgrasell on 2007-04-30
I haven't partitioned the drive yet, though I do have bootcamp installed.

---

### Post by Nasiom on 2007-04-30
Hum...

If you insert Ubuntu CD in you MacBook Pro and reboot while holding option (ALT) , does it show up as a boot device?

Normally it should come up there , you select it with the arrows on your keyboard. It may take a while for the CD icon to show up , if it never shows, then run BootCamp Assistant and partition you disk.  Then repeat the operation.

Also , have you run Apple Software Update to make sure you don't have one of the machine that requires a firmware update?  This update was necessary for the first generation MacBook Pro only.

That's all I can think of.

Keep us posted,

-Nasiom

---

### Post by rgrasell on 2007-04-30
No matter what keys I press (or even if I don't press any) the CD spins and is then spit out.  This is frustrating.

---

### Post by Nasiom on 2007-04-30
Let's go back to the begining;

You downloaded the iso image from here:

[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)

Select North America as the location near you - no matter what , this one is good for sure.

Then use Disk Utilily and simply click the burn button and select that iso image and burnt it?

If all these are true then do run BootCamp Assistant and partition your disk , then quit and reboot while holding C

it has to work unless the image you download is corrupted. 

-Nasiom

---

### Post by Nasiom on 2007-04-30
On more thing ;-)

I hope you're not trying to install the 64-bit version?  BootCamp bios enabler is 32-bit only...

If you need the 64-bit version then use VMWare or the new OpenSource VirtualBOX from Innotek.  

-Nasiom

---

### Post by rgrasell on 2007-04-30
I got it to work!  I messed with the P-RAM (it had an entry about a required boot drive).  Ubuntu runs now.  I must say, I;m impressed by wireless support.  WAP2 works great.  What I didn't like was that I had to install fglrx for 3d support.  Oh, well.  It's such a crappy driver.  All I have to do now is use Boot Camp to partition my drive.  Shouldn't be that hard.

---

### Post by jarrwlee on 2007-05-10
Any idea what you did exactly? I'm running into the same issue here where only the original Mac OS X install DVD will boot. I've tried resetting the PRAM, but that allows it to get part of the way booted and then spits the disc out.

---

### Post by rgrasell on 2007-05-10
open a terminal windows and use the nvram command to clear out nvram.  (read the man page. if you don't know how, type 'man nvram')  Then reboot and clear P-RAM about 5 times.  Then try, it should work!

---

