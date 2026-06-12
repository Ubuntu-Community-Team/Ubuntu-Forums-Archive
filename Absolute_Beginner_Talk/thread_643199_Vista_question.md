---
title: "Vista question"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by thedrizz on 2007-12-17
Well, i've decided that while i love linux, i need games. ANd since my XP boot is screwed up beyond recognition, i've decided to back up the essentials and install vista. Because honestly, why the hell not. 


My question is, which version do i need- x86 x64 or something else? How do i know which i need?

Also, when i tried installing linux off of my transplant dvd drive, i could not boot off the disk. When i changed it to a cd, and plugged in the old cd drive, it worked fine. Any idea why this might happen?

One last thing- Will installing vista over my xp partition have any effect at all on my ubuntu partition?

Thanks in advance!

---

### Post by SOULRiDER on 2007-12-17
IMHO, dont even bother with it, just reinsall XP.

When you change ddrives, remember to ste your BIOS to boot from CD-ROM

x86-x64 depends on your processor, which do you have?

Vista will erase GRUB, you will have to restore it.

---

### Post by philinux on 2007-12-17
> **thedrizz said:**
> 

One last thing- Will installing vista over my xp partition have any effect at all on my ubuntu partition?

Thanks in advance!

It will overwrite the mbr so grub will need to be reinstalled.

---

### Post by thedrizz on 2007-12-17
well, when i tried to do it with the dvd player i would set it to boot first, it just wouldent.

I opened the boot menu and chose the cd drive (and it still said cd drive, that could be the problem) and it didn't boot.

reinstalling xp would be easier i guess....

does an xp reinstall overwrite grub?

oh, and my processor is a pentium 3.2ghz

---

### Post by thelatinist on 2007-12-17
> **thedrizz said:**
> ...i've decided to back up the essentials and install vista. Because honestly, why the hell not.

Because Vista is a bloated, resource-hogging unstable behemoth of an OS which may cripple your machine with DRM and can at any time decide to disable your hardware if it decides your drivers aren't up to its standards?

Reinstall XP.  It's by far the better OS.

---

### Post by philinux on 2007-12-17
> does an xp reinstall overwrite grub?

Yes.

---

### Post by lespaul_rentals on 2007-12-17
Don't install Vista.  It will discover other partitions and likely overwrite them.

---

### Post by thedrizz on 2007-12-17
alright you've convinced me as to XP.

Any precautions i should take before doing the reinstall?

oh, and if anyone can solve this problem, i can put off reinstalling for a bit.

> Hiya,

So i was updating my drivers earlier, uninstalling the old ones, all that jazz. My video card is a radeon 9800xt 256mb, and i was going to use the omega drivers. Everything was working fine until i got to the installing of the actual driver. I got the error:

[quote]error extracting support files

error loading type library/dll

At this point it acted like everything had gone smoothly. But the drivers were not installed. I tried the catalyst drivers, got the exact same problem.

Anyone?[/QUOTE]

Posted on another forum, but my XP is really really screwed up. But fixing this could buy me some more lazy time, i guess

---

### Post by thedrizz on 2007-12-17
Edit: got XP,

How would one reinstall gnome after reinstalling xp?

---

### Post by jasonrandolph on 2007-12-17
Why not run your games using wine, or run XP from within Linux using a virtualization program (such as VMware or Virtual Box.  From what I understand, you can run XP in Linux this way, but not Vista.

By the way, Vista is junk.  The only reason I upgraded was that it came free with my laptop.  Now that I have Photoshop CS2 running in Linux, the only reason I still have Vista is for my iphone.

---

### Post by thedrizz on 2007-12-17
> **jasonrandolph said:**
> Why not run your games using wine, or run XP from within Linux using a virtualization program (such as VMware or Virtual Box.  From what I understand, you can run XP in Linux this way, but not Vista.

By the way, Vista is junk.  The only reason I upgraded was that it came free with my laptop.  Now that I have Photoshop CS2 running in Linux, the only reason I still have Vista is for my iphone.

wine works for nothing really

Virtualization, using a broken windows doesnt help that much :)

But as for reinstalling XP over the previous partition

Anything i should watch for? I got supergrub on a cd, so that should fix grub. Anything else?

---

### Post by thedrizz on 2007-12-17
alright hit a snag.

When i tried to install, it said i do not have a hard drive installed. Exept i kinda do. Do i need to delete the windows partition ahead or time or anything?

Argh confusing

---

### Post by Joeb454 on 2007-12-17
I'm sure it should automatically recognise that there's a drive there...even if it's partitioned with 1 ext3 and one NTFS :/

---

### Post by Presto123 on 2007-12-17
Which games did you want to install? B/c there are many out there that Wine CAN run...you just need to tweak a few things, but, of course it isn't perfect.

But I can agree with everyone else, STAY FAR away from Vista. I can say this b/c I HAVE to dual boot this laptop with it, and I cannot stand it. XP is by FAR the better OS.

Since you have chosen to NOT install Vista, this is just to add more emphasis on it. ;)

If it isn't showing your HD, try running a check on the Ubuntu disk first and see where we can go with it from there.

---

### Post by thedrizz on 2007-12-17
> **Presto123 said:**
> 

If it isn't showing your HD, try running a check on the Ubuntu disk first and see where we can go with it from there.

How?

When i had my external hard drive plugged in, it recognized that. However, it does not recognize the hard drive i'm currently bloody running to type this.

:(

---

### Post by Presto123 on 2007-12-17
> **thedrizz said:**
> How?

When i had my external hard drive plugged in, it recognized that. However, it does not recognize the hard drive i'm currently bloody running to type this.

:(

Put the Ubuntu disk back in, reboot and it will be there as "Check Disk", something like that. It will check it and then reboot computer after giving you an "okay" or "not okay" type of message. If it comes up as not being okay, reburn your disk.

This is just a first check kind of thing...it probably isn't it, but worth checking.

---

### Post by thedrizz on 2007-12-17
> **Presto123 said:**
> Put the Ubuntu disk back in, reboot and it will be there as "Check Disk", something like that. It will check it and then reboot computer after giving you an "okay" or "not okay" type of message. If it comes up as not being okay, reburn your disk.

This is just a first check kind of thing...it probably isn't it, but worth checking.

i think you have it backwards.

I have xp and ubuntu installed right now, and i'm dual booting

i want to reinstall xp because its messed up

when i try, the xp install does not recognize any hard drive being present

where does the ubuntu live cd come into this?

---

### Post by Presto123 on 2007-12-17
> **thedrizz said:**
> i think you have it backwards.

I have xp and ubuntu installed right now, and i'm dual booting

i want to reinstall xp because its messed up

when i try, the xp install does not recognize any hard drive being present

where does the ubuntu live cd come into this?

Okay...you are right, I AM backwards. I was thinking you were talking about that the Ubuntu doesn't show.

Which is it really? Vista or XP?

Someone else will be better to help you with this; someone with more Windows issue experience.

---

### Post by thedrizz on 2007-12-17
xp, reinstalling over effed up xp

---

### Post by philinux on 2007-12-17
Ok so make sure no external disk pluged in, insert xp install disk - reboot.

---

### Post by thedrizz on 2007-12-17
> **philinux said:**
> Ok so make sure no external disk pluged in, insert xp install disk - reboot.

done twice. 

It auto-reboots after telling me it did not detect any hard drive

---

### Post by lespaul_rentals on 2007-12-18
This is because you have either a SCSI, SATA or RAID setup that XP cannot recognize because it is too old or doesn't have the drivers for it.  A couple of questions:

How new is this computer?  Did it come out within the last 6 months or year?  If so, Ubuntu 7.10 will be able to recognize the newer HDD drivers as will Vista, but XP, Ubuntu 7.04, etc. will **not**.  The only other distro I've seen that will recognize these newer HDD setups is OpenSuSE 10.3 (which I installed on my friend's computer).

Do you have the drivers for your SATA or RAID setup?  If you do, press F3 or F6 I think it is (it will show you when XP install first comes up). They may or may not have come on a seperate CD with your computer.  These days, the manufacturers are sending you home with a computer with Vista and a Recovery Partition.  This Recovery Partition contains all the drivers, files, etc. that you would need to restore or re=install Vista.  This way, they don't have to give you the original Vista DVD or any of the proprietary, brand-new driver CDs...thus successfully locking you in with Vista and the setup they give you.  That is what I fear has happened with you.  If you don't have these driver CDs, you are basically forced to use Vista, Ubuntu 7.10, or OpenSuSE 10.3.

---

### Post by Presto123 on 2007-12-18
> **lespaul_rentals said:**
> This is because you have either a SCSI, SATA or RAID setup that XP cannot recognize because it is too old or doesn't have the drivers for it.  A couple of questions:

How new is this computer?  Did it come out within the last 6 months or year?  If so, Ubuntu 7.10 will be able to recognize the newer HDD drivers as will Vista, but XP, Ubuntu 7.04, etc. will **not**.  The only other distro I've seen that will recognize these newer HDD setups is OpenSuSE 10.3 (which I installed on my friend's computer).

Do you have the drivers for your SATA or RAID setup?  If you do, press F3 or F6 I think it is (it will show you when XP install first comes up). They may or may not have come on a seperate CD with your computer.  These days, the manufacturers are sending you home with a computer with Vista and a Recovery Partition.  This Recovery Partition contains all the drivers, files, etc. that you would need to restore or re=install Vista.  This way, they don't have to give you the original Vista DVD or any of the proprietary, brand-new driver CDs...thus successfully locking you in with Vista and the setup they give you.  That is what I fear has happened with you.  If you don't have these driver CDs, you are basically forced to use Vista, Ubuntu 7.10, or OpenSuSE 10.3.

Are you sure about this? Seems like when I had Ubuntu 7.04 installed, it recognized my SCSI just fine. I'm not saying I KNOW this for a fact, because I had it running on an external. I don't know about the XP having this issue, though.

---

### Post by thedrizz on 2007-12-18
the computer is about 3 years old, came with xp, and its one hard drive, i dont see why it should be so hard.

I will try that f6 idea tomorrow, however

---

### Post by Presto123 on 2007-12-18
Sorry you are having so many issues with it. Wish I could help. Don't give up on it, though. Someone will most likely be able to help you fix this problem.

---

### Post by lespaul_rentals on 2007-12-18
> **Presto123 said:**
> Are you sure about this? Seems like when I had Ubuntu 7.04 installed, it recognized my SCSI just fine. I'm not saying I KNOW this for a fact, because I had it running on an external. I don't know about the XP having this issue, though.

Yes, I am sure.  It all depends on the SCSI/SATA drives.  Sometimes older OSes will recognize the setup, sometimes not.

---

### Post by Niniel on 2007-12-18
If you really want to run cutting-edge games in all their glory, you WILL have to go to Vista because MS decided to help sell Vista by making the new DirectX Vista-only. Of course you'll also need a DX10 graphics card... But the point is, in the long run, you may have to install that OS anyway. For now, new games still support both, and the DX10 effects aren't all that earth-shattering, but that is likely to change in the future.

---

### Post by thedrizz on 2007-12-18
> **Niniel said:**
> If you really want to run cutting-edge games in all their glory, you WILL have to go to Vista because MS decided to help sell Vista by making the new DirectX Vista-only. Of course you'll also need a DX10 graphics card... But the point is, in the long run, you may have to install that OS anyway. For now, new games still support both, and the DX10 effects aren't all that earth-shattering, but that is likely to change in the future.

well i dont even have a dx10 card, and i'm not that picky.

So no one has a solution to my invisable hard drive? F6 told me i needed 3rd party stuff or something

---

### Post by stchman on 2007-12-18
> **thedrizz said:**
> Well, i've decided that while i love linux, i need games. ANd since my XP boot is screwed up beyond recognition, i've decided to back up the essentials and install vista. Because honestly, why the hell not. 


My question is, which version do i need- x86 x64 or something else? How do i know which i need?

Also, when i tried installing linux off of my transplant dvd drive, i could not boot off the disk. When i changed it to a cd, and plugged in the old cd drive, it worked fine. Any idea why this might happen?

One last thing- Will installing vista over my xp partition have any effect at all on my ubuntu partition?

Thanks in advance!

Just reinstall XP, Vista is ultra bloated.  If you reinstall Vista you will need to then reinstall GRUB.

---

### Post by thedrizz on 2007-12-18
Wait where can i get a floppy disk SATA driver thingy?

i got a spare floppy, i just need the drivers themselves

---

### Post by thedrizz on 2007-12-18
Well, i reinstalled XP, and while i dont like posting xp problems on the Ubuntu forum, this has been helpful so far.

Reposted from another forum-

> first off heres my computer

[http://support.dell.com/support/downloads/driverslist.aspx?c=us&l=en&s=gen&ServiceTag=&SystemID=DIM_PNT_P4_XPS_G2&os=WW1&osl=en&catid=&impid=](http://support.dell.com/support/downloads/driverslist.aspx?c=us&l=en&s=gen&ServiceTag=&SystemID=DIM_PNT_P4_XPS_G2&os=WW1&osl=en&catid=&impid=)

I dual boot ubuntu and xp

I recently completely reinstalled xp because it was just a mess. Now, when i boot xp i have 2 xp options. Should i be at all concerned about this?

Also, Xp seems a little, well, silly. It wont read my ethernet connection (which obviously works, as i'm using it on ubuntu right now), sound card (i'm listening to music in ubuntu right now) and i'm sure some other things are lacking.

Presumeably i need drivers. What sort should i be on the lookout for, and from where? I already did my video card, that works fine. If anyone could help, that'd be great

---

### Post by rkd on 2007-12-19
The two XP options at bootup probably isn't a serious problem, and also probably is easy to fix -- post the contents of boot.ini from the root directory of your XP C: drive here and I should be able to tell you what to do to fix that.

As for your ethernet, when you installed XP, there should have been a step where it asked you about setting up your network.  Do you remember what you told it at that point?  Maybe you gave an answer not appropriate for your setup.  I think you can run the network setup again by going to the network control panel and double clicking on Network Setup Wizard.  Go through that, noting down all the questions and your answers, then if your ethernet still doesn't work, post those questions and answers here, and I (or someone else) can help you figure out what is wrong.

I'm not sure why your sound isn't working.  Did you reinstall from a Dell-supplied CD or a generic Windows XP installation CD?  If you didn't use a Dell-supplied CD, then maybe you just need to download and install the audio driver from the Dell page you pointed to in your last post, assuming that is the correct page for your computer.  Try looking into the Device Manager under "Sound, video and game controllers" to see what it says about the name of your sound device.  There may be a number of lines under that entry.  If you aren't sure which is the proper one, tell us the whole list and we'll help you figure it out.

While you are in the Device Manager, note any devices that have the yellow or red warning icons -- you probably will want to fix the problems with them, too.  You might need drivers for those devices from that same Dell Support web page.  Come to think of it, you probably should check the Device Manager before you try the Network Setup Wizard, in case there is a warning by your network adapter and you need to download a driver for it.

---

### Post by seventhc on 2007-12-19
> By the way, Vista is junk. The only reason I upgraded was that it came free with my laptop. Now that I have Photoshop CS2 running in Linux, the only reason I still have Vista is for my iphone.
Just curious, why do you need vista for the iphone? I don't have one, but curious as to what vista does for it.

---

