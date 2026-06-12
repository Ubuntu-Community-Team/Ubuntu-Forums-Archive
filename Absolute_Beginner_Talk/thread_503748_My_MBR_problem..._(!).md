---
title: "My MBR problem... (!)"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by xvertigox on 2007-07-18
Here's the situation. I have two disks, 200gb and 160gb. My 200gb has Vista on it. I resized the 160gb partition down to 150gb so I could have 10gb free for Ubuntu. I installed Ubuntu on this new 10gb partition but after restarting it booted straight into Vista. Now I realize that I didn't set my 160gb drive to boot before my 200gb drive. 

Anyway, I used System Commander to create a new MBR but it messed up so it just sits there with a few symbols instead of presenting me with my boot menu. Here's where it gets annoying, my BIOS doesn't let me choose which drive I want to boot of first so I can't do anything. I don't have my Vista DVD (it broke, hence trying Ubuntu) so I can't repair the MBR. I've reinstalled grub but that doesn't matter since it boots of my 200gb drive first.

Any help would be **greatly** appreciated :)

---

### Post by tgalati4 on 2007-07-18
Well, it doesn't sound like a motherboard problem.

Can you boot the Ubuntu Live CD?  What version of Ubuntu?

Only 10 GB of space?  Perhaps Ubuntu got pissed at being shortchanged.

---

### Post by xvertigox on 2007-07-18
> **tgalati4 said:**
> Well, it doesn't sound like a motherboard problem.


Master Boot Record. Sorry if I'm using the wrong term, I'm new to this and it's 2am :(

> **tgalati4 said:**
> 
Can you boot the Ubuntu Live CD?  What version of Ubuntu?


Yup. Feisty Fawn.

The problem is my Vista boot loader is messed up and I don't have my Vista DVD to repair it. I also can't boot of my other drive because my BIOS sucks :\

---

### Post by Malta paul on 2007-07-18
I would say that you should first select the HD you wish to boot from. You should be able to select the HD using you BIOS 'Integrated Peripherals' (It may take you a few tries to get it correct.) Then use 'Advance BIOS Features' >Boot Device Select. to set your boot order.
Use your live Ubuntu disk and install on your HD of choice. Grub will set itself up for you.
A very good reference is :  [http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index) and [http://ubuntuguide.org/wiki/Ubuntu:Edgy](http://ubuntuguide.org/wiki/Ubuntu:Edgy)
Hope this is of some help :)

---

### Post by pistcivet on 2007-07-18
I have no experience dual booting Vista.

Ubuntu will overwrite the MBR to point to wherever grub is installed.
Which will then give you a choice of OS to boot.
There is no need to change the boot order of the hard drives.

Why you booted straight to Vista, I don't know.
But I would try reinstalling Ubuntu, and let it write a new MBR.

You really should back up important files, and have some way to reinstall
Vista in the event of catastrophe.

I've not used "System Commander", but it seems incompatible with Vista.

---

### Post by Outrunner on 2007-07-18
[Super GRUB]("http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml"). Download it, burn it, love it. Make a CD of this and boot into it. Now, I can't remember exactly in what menu this option is, but if you search around, you'll find that you can Restore GRUB to MBR

Have fun.

---

### Post by tgalati4 on 2007-07-18
You could open your machine, clean out the dust (if you have done so in the past year) and swap the drive ribbons.  See if Grub/Ubuntu loads.  If so, then it's possible that Grub was installed on the Master Boot Record of the second drive.  No worries, just put the drives back in the original order and find a Vista disk to repair the Master Boot Record of the first disk.

The fact that your original Vista disk is hosed makes finding a new one a challenge.  Perhaps you can plead your case to the Windows Genuine Advantage folks.  After all what good is having windows if you can't replace them when they break?

---

