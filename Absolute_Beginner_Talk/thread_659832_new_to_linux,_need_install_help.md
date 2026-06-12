---
title: "new to linux, need install help"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by juanzo007 on 2008-01-06
Hey Folks...

I'm trying to install ubuntu desktop on an old compaq pentium 2.4Ghz 120mb hard drive tower.  I tried both the live cd and the alternate, restart booting from the cd drive, but all i get is an error message," windows could not start .... system32\hal.dll missing or corupt, pls reinstall copy of the file.

windows was working before the install attempt, but wont now.  i get just the error message page or can select the recovery console.

What to do?  thx much for the help...

John

---

### Post by Defrector on 2008-01-06
How far into the install attempt did you go before you started having problems? Did that error come up immediately once you tried booting from the live/alternate CDs, or after running them?

Before the problem happened, were you able to successfully (loose term) install ubuntu? Were there any issues when trying to run from the CD and install?

additional questions:

What version of windows did you have installed and do you have any special partitions laid out on your drive or is it a mostly traditional windows rig?

You mean you have a 120GB hard drive right?

---

### Post by juanzo007 on 2008-01-06
thx for the quick reply...

the first time i opened the cd from within windows and tried to install, and the only thing was a message stating the ubuntu browser was loading, but nothing happened.  then i figured i needed to reboot the computer.

after that, the error messages started on reboot.  i can get into the recovery console command prompt with D:\MiniNT and D:\i386 selections, but otherwise that's it.

I have not been able to install ubuntu at all.  no partitioning, traditional windows set up.  not sure which version, windows circa 2002.  120gb hard drive, yes.

---

### Post by stijngysemans on 2008-01-06
you need to make sure that you boot from the cd so that ubuntu can install.
you might need to change the boot order in your bios.

---

### Post by Defrector on 2008-01-06
That's interesting that your windows install somehow got corrupted circa the ubuntu windows installer flaked out. Did you have to do a forced reset or were you able to tell windows to restart the machine (or healthily shut down then manually start back up?). 

What I'm probing for is if a forced reset had to happen the drive may have gone berzerk for a split second and corrupted the drive. It's not impossible for the ubuntu installer in windows to corrupt a drive (I don't know much about it) but I assumed that it goes through a lot of partitioning choices, etc before committing any modification of the drive itself.

Your windows XP installer CD-or whatever other windows CD installer you used to install windows-likely has a repair feature on it if you boot from it. That would be your best bet in getting windows to work right. The second best bet would be to boot from the ubuntu installer CD, and assuming your internet configs right and everything, you can then try to (carefully) find and copy your missing DLLs to your drive, and do other random diagnostics.

**NOTE:** You probably should fix windows before installing ubuntu onto your hard drive. If you run windows repair utilities, they may remove the linux partition information and you'll have another problem to fix. Booting from the ubuntu CD will not immediately install ubuntu, but it will run ubuntu in memory, leaving your drive alone until you choose to install.

For the future, I agree with stijngysemans' advice to try and boot from the CD itself rather than run the installer from Windows. Make sure your BIOS is config'ed to FIRST check the CD drive for bootable media and SECOND check the hard drive for bootable media...and (hopefully) that will roll ok.

There's a small possibility that your hard drive happens to be flaking out and ready to die. On spare time it might be safe to check how well it has been behaving with scandisk (Win) or fsck (Linux) or if you're feeling geeky try and dig up its S.M.A.R.T. information somehow.

---

### Post by juanzo007 on 2008-01-06
thanks again...  now tell me if i completely screwed up!!

per normal, i can't find my original recovery cd's, so i created one from a newer hp machine, ran the recovery cd in the old box, and reformatted the c drive.

tried to install ubuntu booting directly from the cd drive, now have a "ntldr is missing" error message.

did i just create a whole new computer education project for myself??!

thx again...

---

### Post by bwtranch on 2008-01-06
As per previous post. You have to BOOT from the Ubuntu CD. You can't load Windows and run the CD. Go to your intial BIOS screen and choose Boot from a CD. Models differ, so you'll have to figure this out. Usually involves hitting a "F" function key at startup.

---

### Post by juanzo007 on 2008-01-06
thx..  yes, I have been booting from my cd drive thru bios screen.  still have the ntldr error message.

I am trying to competely erase the drive with a KillDisk bootable cd, still with the same error message.

eeks?

---

### Post by juanzo007 on 2008-01-06
i created a windows xp boot disk, but still the same error message booting from cd drive

---

### Post by jonnywombat on 2008-01-06
The NTLDR error is caused by one of the following reasons.

      1. Computer is booting from a non-bootable source.
       2. Computer hard disk drive is not properly setup in BIOS.
       3. Corrupt NTLDR and/or NTDETECT.COM file.
       4. Misconfiguration with the boot.ini file.
       5. Attempting to upgrade from a Windows 95, 98, or ME computer that is using FAT32.
       6. New hard disk drive being added.
       7. Corrupt boot sector / master boot record.
       8. Seriously corrupted version of Windows 2000 or Windows XP.
       9. Loose or Faulty IDE/EIDE hard disk drive cable.

As you are attempting to boot from a cd and not your hdd then then only reason that applies is number 1... When you burnt the disks did you ensure you burnt the image to disk and not the .iso file.. if you did the latter it will NOT be bootable and hence your error...

For help fixing your hdd visit [http://www.computerhope.com/issues/ch000465.htm](http://www.computerhope.com/issues/ch000465.htm) (which is where I got the above list from).

HTH

Jonny

---

### Post by juanzo007 on 2008-01-06
Ok, redid the ubuntu boot disk, has all files on it, is bootable, run from my cd drive thru bios setup.  Same ntldr error.

would completely erasing the hd with a proper utilty help?  I'll try anything at this point.

---

### Post by juanzo007 on 2008-01-06
I appreciate the help!!  Ok, new ubuntu boot disk, is bootable, has all the files, booted from cd drive thru bios setup, same error message.  got about 10 hours into this...  windows, ack.....

ok, suggestions, one and all!?  new hard drive?  utility to wipe the disk clean for fresh restart?

---

### Post by juanzo007 on 2008-01-06
ive tried everything i can think of.  tried an ntldr boot disk, same.  disabled the hard drive, get boot disk failure.

Can somebody tell me, if i get a new hard drive with nothing on it, can i simply put in the  ubuntu boot disk, install it, and be on my way???

---

### Post by zabien1970 on 2008-01-06
Just to make sure we understand you correctly, 
 new boot disk> did you burn another disk? what utility are you using to burn the disk?
 is bootable> how do you know this?

---

### Post by doorknob60 on 2008-01-06
Because you get the same error with every boot cd you try, I can pretty much guarantee that it's not even trying to boot from CD. When your computer turns on, go into the settings by pressing a button like F1 or F2 or Delete (different on different computers) and somewhere will be an option to set the boot order, and tell it to boot the CD first. EDIT: either that or the CD' aren't bootable (could be caused from just burning the iso as a file to the cd).

---

### Post by juanzo007 on 2008-01-07
thanks for the continued help, folks...  i don't doubt operator error, but here goes...

I'm in the award bios setup utility, and i have disabled the floppy disk drive, next up is the cd-rw drive.  I did not copy the .iso file on the boot disks, I burned them and on the cd there are a bunch of files, including autorun and start.exe.  i'm hoping that is why it should be a boot disk, not a copied .iso?

am i making sense?

---

### Post by juanzo007 on 2008-01-07
i am using power2go to burn the disk, and selecting to burn the iso as a boot disk.

---

### Post by juanzo007 on 2008-01-07
omg, its reading the boot disk after hitting the esc button...  stand by...
ubuntu on the monitor and everything...

---

### Post by juanzo007 on 2008-01-07
thanks folks, it installed.  not sure why.  a combination of a boot disk, the esc key, and 3 beers b/c i was so pissed off!  operator error, no doubt.  will drink sooner next time.

Thanks so much!!

---

### Post by juanzo007 on 2008-01-07
thanks folks, it installed.  not sure why.  a combination of a boot disk, the esc key, and 3 beers b/c i was so pissed off!  operator error, no doubt.  will drink sooner next time.

Thanks so much!!

---

### Post by jonnywombat on 2008-01-07
Glad your up and running....

You may still need to follow link in my previous post to fix the error if you are dual booting and want to be able to boot back into windows.. otherwise you may get the still once you have selected windows from your grub menu..

Jonny

---

