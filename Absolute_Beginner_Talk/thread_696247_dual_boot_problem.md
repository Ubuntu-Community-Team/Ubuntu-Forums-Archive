---
title: "dual boot problem"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by firewick on 2008-02-13
I put about 7 or 8 hours into this, so I finally decided to give up and ask for help... I have 2 dell computers. Comp A is an optiplex gx150 pent III 1ghz, 512mb ram, 40 gb hd. Comp B is a dimension L1000R pent III 1ghz, 512mb ram, 20gb hd and 8gb hd.

I installed 7.10 and XP on comp A (partitioned 12gb ntfs=sda1, 27gb ext3 sda2, and 1gb swap sda3). Work's just fine. (other than a pci bridge error about 1 second after it is loading into ubuntu, doesn't seem to affect anything, and I haven't looked into it yet)

Here's the problem. On comp B I can not get the windows cd to boot it just ignores it... I have a feeling it is the bios to that computer, but I am not sure. I had the 20gb partitioned with 7gb ntfs sda1, 12gb ext3 sda2, and 1gb swap sda3. (I was using the 8gb for my backup 7.10 boot drive) I now have the 20gb partitioned 12gb ext3 sda1, 1gb swap sda2, and 7gb ntfs sda3 (I don't really know why I changed it, but I am hoping I can still use this setup when I get XP installed) I installed 7.10 on comp B's 20gb sda1 drive off the same cd that I used on comp A (and also for the 8gb backup drive) I just don't understand how the 7.10 cd boots right up on comp B but the XP does not, and they both do on comp A... If anyone could help I would appreciate it.

Also, I switched the cd drv from comp A to B with no luck. Same outcome 7.10 cd comes right up, no XP...

I know the real question everyone is going to ask is why are you putting XP on anyhow? I have asked myself this over and over again, and I do not know. What a headache though... I have been using ubuntu for about 3 months now and it is great. I put XP on that gx150 and it took about 2 seconds before it started getting registry errors and locking up on me... I don't even know how I put up with windows for as long as I did...

Thanks,

Eric

---

### Post by BrentMlady on 2008-02-13
First of all the Dell machines have massive problems with loading and detecting CD's.  At least the ones I have touched.

For some of the older machines it will not inform you that there is a cd in the drive and boot from it.  Have you tried to press the following key before the computer boots.  

F2, Esc, F5, and maybe F8 (you never know with a dell)

---

### Post by Moop on 2008-02-13
Using gparted check all the partitions on the hard drive and uncheck any of them that have a boot flag. XP gets confused by more than one boot flag. 

If that's not the problem try disconnecting the hard drive and see if it will boot from the XP  cd. If it does then you know you have a partitioning error.

---

### Post by firewick on 2008-02-13
Thanks for the input. I tried the various keys. (I never used f5 or esc) they also did not work. I also checked the boot flags. Both dives were marked so I unmarked the 8gb. No change. I unplugged both drives, no change. Just came up with an error about not being a bootable disk.

I feel bad for even putting "dual boot problem" in the subject line, it should be "windows boot problem". Ubuntu works great.

Does anyone know if I can just put an extra config file on the xp boot cd to get it to be recognized? I could copy the cd and add it at that time. I just don't know what file or line to add, or if that would even work?

Thanks again,

Eric

---

### Post by mrsteveman1 on 2008-02-13
I suspect perhaps the CD itself may have errors on it, i've noticed that sometimes burn errors go unnoticed and then later on cause problems on some drives.

Is this a pressed (IE factory provided) XP cd? or is this an image you burned to a CD-R etc?

---

### Post by Moop on 2008-02-13
You could try booting from a windows 98 boot disk and then when you reach the command line switch to the cd drive (d: or whatever) pop in your XP cd and run setup. 

You can download windows 98 boot disks if you don't have one. I think 98se is what you want. I don't know what else to try. :popcorn:

---

### Post by firewick on 2008-02-13
It is a cd-r copy. If it was an error on the disk noticed by different drives, then that problem should have been solved when I moved comp A cd drive to comp B. It reads 100% of the time on comp A and it's regular drive (I didn't put B's drive in A, I guess that would be another place to go, but I would suspect it would work.)

I tried booting from a dos prompt (floppy with cd drivers) and I could read all of the information on the cd. When I ran setup.exe it said it was not executable in ms-dos... I could have sworn that the first 40 mins of the windows install is in dos, but I could be mistaken, maybe it just looks that way...

Thanks again guys, I am not trying to shoot anyone's ideas down I am just trying to give as much info as I can about what I have done, in hopes someone can solve this weird little problem... I really appreciate the help.

Eric

---

### Post by noname123 on 2008-02-13
I work on a lot of dell's 99% use f12 maybe that will help


P.S. at the dell screen f12

---

### Post by mrsteveman1 on 2008-02-14
If the CD is good my next guess would be a bios bug. If you can take a working cd+drive combination to another box and it refuses to boot, the only variable is the bios, which seems to be refusing to load the el torito boot image from the CD for some reason.

BTW, the XP setup takes place in an NT environment, which means the setup program won't run on a W95 boot disk.

---

### Post by KCormier on 2008-02-14
/edit  I'm sorry.  I had this thread confused with another thread I was helping with a little while back.  It seems that the cd is being completely ignored and that partitioning errors have been ruled out.  Try booting the ubuntu live cd on the non-working computer.  Lets see if the computer won't boot to ANY cd, or just the windows cd...

---

### Post by dstew on 2008-02-14
My guess about the Windows CD not booting is that it is not a bootable CD. Maybe it is a custom recovery CD meant to be used with a recovery partition or some other special hardware on a specific computer.

---

### Post by carolus on 2008-02-14
"The issue is due to the fact that xp won't boot if grub is installed on the mbr."
Isn't that where grub normally goes in a dual boot configuration?  I thought it replaced the Windows bootloader, so that to uninstall Ubuntu on a Vista machine, you have to replace grub with the Windows bootloader  by means of a Windows install disk.

---

### Post by noname123 on 2008-02-14
Not to shoot down the grub wont let xp run Carolus but when you install xp or vista after  grub the xp\vist mbr kills the grub and then you have to install easybcd or like you said install xp\vista first then your ubuntu.

---

### Post by noname123 on 2008-02-15
i agree with Dstew

---

### Post by KCormier on 2008-02-18
look at his first post.  it boots fine when sda1 is ntfs.  It doesn't like an unrecognizable partition on sda1.  The reason is xp doesn't boot like most operating systems.  The boot loader does not go in the mbr, it goes at the beginning of the first partition.  Boot to your linux live cd and mark sda1 and sda2 as hidden in gparted (flags).  From there the xp cd should boot! (i think)  lol.  If not then let me know and I'll start testing.  All I know is xp really isn't happy unless it's the first drive on the disk or at least thinks it is!

-Kevin

---

### Post by stalkingwolf on 2008-02-18
on my 4 dell laptops F2 is for setup menu and F12 takes you to the boot menu.

I agree about the partition secquence although I have had a couple older machines that I have had
to set all three boot devices to CD-rom before they would boot from it.

---

### Post by KCormier on 2008-02-19
when you put the disk in, does it say hit any key to boot from cd, then when you do the screen just goes black and stays that way?  you might have already said that but I can't remember and didn't see it when reviewing quickly :-\ sorry.

---

### Post by GearedForWar on 2008-02-19
Seeing as its a BIOS bug you may need to call Dell and they can flash it for you.  That will set it back to factory default, and if it still persists then you may need to get a new chip set or motherboard.

---

### Post by KCormier on 2008-02-19
There's no saying it's a bios bug yet.  Windows displays a similar problem from time to time.  I can't remember the exact details as it's been a long time since dealing with it, however if he comes back and confirms that it starts to boot from cd but just stays at a black screen, and i think he just may, then it's an issue with the way windows cd's boot and he needs to either overwrite grub or hide his ext3 partition or something...there's some sort of crazy issue.

-Kevin

---

### Post by CrazyAzazel on 2008-02-25
> **KCormier said:**
> when you put the disk in, does it say hit any key to boot from cd, then when you do the screen just goes black and stays that way?  you might have already said that but I can't remember and didn't see it when reviewing quickly :-\ sorry.

Thats exactly the problem, that I have :/
I first destroyed both Ubuntu and Windows by playing with Super Grub Disk >.<
Then I fixed Ubuntu, but now my Windows CD is not booting, after telling me I have to hit any key, and talking about hardware configurations, because then the screen simply goes black and stays that way until I hit several keys that cause the system to reboot-.-

-Manuel

---

