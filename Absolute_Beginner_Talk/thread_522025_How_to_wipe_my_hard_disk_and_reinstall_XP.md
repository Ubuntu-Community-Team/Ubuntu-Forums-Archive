---
title: "How to wipe my hard disk and reinstall XP?"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by kickstart on 2007-08-10
Hi, 

My Uni Degree requires me to have photoshop, and due to the problems that people have been experiencing running Photoshop CS3 on Ubuntu, i am forced to remove Ubuntu completely and reinstall XP.

I have tried running the XP Pro Cd at startup and letting it automatically boot, but it appears GRUB doesn't want to let it run.

I cant select the CD to run before the harddrive because for some reason when i enter the boot selection i cant move the cursor at all. I can use F8 to get into the boot selector but the arrow keys do not respond. I think it may have something to do with my USB keyboard, but it is strange that i can get to the menu but not make a choice. any help here?

So basically, what i am asking is, how do i wipe the hard disk drive of Ubuntu AND Grub and anything else that will prevent me from reinstalling xp.

PS. I have used the search function to no avail.

Thanks

---

### Post by TravMan63 on 2007-08-10
get gdisk - make a boot floppy

done in seconds...

---

### Post by splintercellguy on 2007-08-10
Couldn't the XP Pro installer just wipe out all partitions and let you create a new NTFS part?

---

### Post by iAndrew on 2007-08-10
I don't see how grub wouldn't let it run. Change the bios so it boots from cd/dvd first?

---

### Post by stoer on 2007-08-10
So long as your bios is set to "boot from cd" then xp will reinstall as normal, giving you the option of where you want to install it and with all the usual formatting options. ie. erase partitions/create new partitions or use the whole disk etc.
Sure you don't want to dual boot? If it is only photoshop that is a problem, set up a small xp partition and install photoshop, for the rest carry on using Linux.  It's what i do, (still using windows for my kids and their games and for a couple of windows only apps for myself - - 80% linux / 20% xp) I'm happy with the compromise.

---

### Post by houstonbofh on 2007-08-10
It may be that the BIOS will not recognize your USB keyboard.  If so, you will need a PS2 keyboard to tell the BIOS to recognize the USB keyboard in the boot menu.  Note that this is far before Linux is doing anything.

---

### Post by TravMan63 on 2007-08-10
One would THINK that the XP cd would simply wipe/format the disk...

but...

I tried XP home -- to remove Xubuntu - and it reported 'no valid partitions'

I did have fat32 partitions on disk as well - valid for XP - but they may have been extended partitions - not good (for XP - I think... seems XP wants to exist in a primary partition - something to look into...)

It could be - that XP would see the drive as having a valid partition table, and be 'confused' with extx filesystem.  It SHOULD work and just format... but for me - it did not.

gdisk on a floppy (IF a floppy drive is present)... otherwise there is the ultimate boot cd...

---

### Post by Calash on 2007-08-10
Sounds like a BIOS issue not correctly using the keyboard.  It would be better in the long run to figure out what this problem is and fix it rather than force your way around it and possibly end up in a worse situation.

Try a PS2 keyboard, or another USB one.  Can you get into the BIOS and adjust the settings there or does the keyboard not work?

One thing you can try is once you are at the point the keyboard does not work, unplug it and plug it back in.  Sometimes this clears up issues like that for me.

---

### Post by Burbruee on 2007-08-10
Does it have to be CS3? Photoshop CS (CS1, 8.0) works almost perfect in ubuntu.

---

### Post by kickstart on 2007-08-10
Thanks for your help so far guys, I'll update you on my stituation:

1). I don't have a floppy disk drive so i cant use a floppy boot disk
2). I can GET INTO the boot menu but i cant choose CD ROM after im in there, it just has HDD selected. It seems really strange that i can select the boot menu (F12) but cannot use the arrow keys or enter or esc keys to control it. 
3). When i boot the computer, it says:

"Boot from CD:
  Boot from CD:
  Grub....."

now, i dont have a cd in the drive so it seems strange that this is happening.

In regards to trying a ps2 keyboard, i don't own one, and im not particularly keen on buying one but if i have to i guess i will. are there any other methods of getting my keyboard to work? i tried unplugging and replugging to no avail.

Look forward to hearing from you.

Also, rather than partitioning my HDD, would it be better (if i were to have xp and ubuntu) to have 2 hard drives, one for xp and one for ubuntu?

I'm open to any input.

---

### Post by original_jamingrit on 2007-08-10
> **kickstart said:**
> Thanks for your help so far guys, I'll update you on my stituation...

I'd consider using GParted on your xubuntu disk to try and format your drive, but only if you had access to a friend's computer if something went wrong and you needed to download something.

Although two hard drives may be a good idea as well.  Have you had problems dual booting from one hdd?

---

### Post by kickstart on 2007-08-10
I havent dual booted before.

Also, im running Ubuntu as opposed to Xubuntu if that makes any difference?

---

### Post by TravMan63 on 2007-08-10
...as far as getting around in bios - it may not be the arrow keys that are needed...

check the screen - or your manual.

Some pc's use tab, some Dell's use ctrl-d to move... there is no standard...

If you can't select your cd drive/change the boot order - the bios may also be password protected...

you can also check your pc/motherboad/bios website for more info

---

### Post by anewguy on 2007-08-11
The "Boot from CD:" stuff is normal when the BIOS is set to boot from CD before booting from the hard drive.  It is trying to boot from CD, finds no bootable CD, so it goes to the hard disk.  Not a problem.

To help you, I give you 2 sets of intructions.  

(1) If you have a dual-boot system, see this post: [http://ubuntuforums.org/showthread.php?t=508927]("http://ubuntuforums.org/showthread.php?t=508927")

(2) All you have on your hard drive is Ubuntu, and you want remove it and install Windows:

- locate your Ubuntu LiveCD that you installed from
- put that CD in the drive and reboot your PC.  Given what you say shows at boot, it should boot up the Ubuntu desktop off the LiveCD.  Be patient - it can take a while.
- once the desktop is up:

- via Applications/Accessories/Terminal,   open up a terminal window so you have access to the command line

- type:   sudo  gparted     and press enter

This will bring up the Linux graphical partition manager.  You will supposedly only see your Linux partitions, since Windows isn't installled.  Right click on each and delete them.  Once no more Linux partitions are showing, the disk should list free (perhaps "unused", I don't remember the exact wording now) in place of everything.  

Exit gparted, remove the CD, put your Windows installation CD in the drive and reboot.


This should do it for you.  Windows doesn't seem to want to install over the top of active partitions, that is why I had you delete them.  We had to use the LiveCD to gain access to gparted without your normal Ubuntu session running (just as with Windows, you can't remove the running partitions).  Once the partitions are gone, Windows installation should see nothing but free space and should be able to install.  

Please post back with your results!:)

---

### Post by TravMan63 on 2007-08-11
> **anewguy said:**
> 

... This should do it for you.  Windows doesn't seem to want to install over the top of active partitions, that is why I had you delete them.  We had to use the LiveCD to gain access to gparted without your normal Ubuntu session running (just as with Windows, you can't remove the running partitions).  Once the partitions are gone, Windows installation should see nothing but free space and should be able to install.  

Please post back with your results!:)

ahh - maybe that was my problem - I had partitions setup and formatted ready to install XP (home) - and it couldn't see 'any valid partitions'

I'll remember that...

---

