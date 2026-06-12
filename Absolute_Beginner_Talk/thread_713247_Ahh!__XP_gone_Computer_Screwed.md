---
title: "Ahh!  XP gone? Computer Screwed?"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by Dispatch on 2008-03-02
I was installing Ubuntu on my other computer and all was going well, I thought.  I left the room when it was at 65% and when I came back in a minute later the Installation box was gone and I knew something was wrong...  I tried to reboot to XP but I got "Error Loading Operating System_"  I set everything in the bios so it should have booted in XP but it didn't...](*,)](*,)](*,):icon_frown:

WHAT CAN I DO!?!?:confused:

---

### Post by Dispatch on 2008-03-02
Pleeeeeease help me.

---

### Post by Yes on 2008-03-02
Try booting the live CD and open a terminal (Applications -> Accessories -> Terminal).  Enter the command "fdisk -ls" (That's a lowercase 'L'), and post here what it says.

Your computer probably isn't screwed, GRUB probably just isn't configured correctly.

---

### Post by Dispatch on 2008-03-02
> **Yes said:**
> Try booting the live CD and open a terminal (Applications -> Accessories -> Terminal).  Enter the command "fdisk -ls" (That's a lowercase 'L'), and post here what it says.

Your computer probably isn't screwed, GRUB probably just isn't configured correctly.

Ok, 1 sec and ill post its results

---

### Post by Dispatch on 2008-03-02
> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb7e61057

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5760    46267168+   7  HPFS/NTFS
/dev/sda2            5761        9463    29744347+   f  W95 Ext'd (LBA)
/dev/sda3   *        9464        9729     2136645   83  Linux
/dev/sda5            5761        9442    29575633+  83  Linux
/dev/sda6            9443        9463      168651   82  Linux swap / Solaris


That's the results.  No idea what it means :confused:

---

### Post by Bargeek on 2008-03-02
I am having similar problems, but think I was installing using a corrupt CD.  I checksummed the file, and that was okay.  Like an idiot, I did NOT verify the CD after I burned it.

Anyhow, the problem was installing the base system, which aborted, thus GRUB was never installed either, (it's further down the installation chain.)  I though about trying to set up GRUB from the the CD, but figured if my base system data was screwy, GRUB might well be too.

So, I am currently re-downloading Gutsy to my roommate's computer, then will burn the disk at a slower speed and check to see if that works.  I am hoping it is just a corrupt disk.

I will post back here as soon as I have any results, even if it is just me sobbing and wanting my mommy.  Maybe if it works for me, it will work for you.

---

### Post by Dispatch on 2008-03-02
I just want to get back to XP... I don't care about Ubuntu right now.  My CD was not corrupted, I ran the test.

---

### Post by Yes on 2008-03-02
It means that your Windows partition is still there.

Can you boot into Ubuntu?  What's your /boot/grub/menu.lst file look like (if you're running off of the CD it'll be something like /media/disk/boot/grub/menu.lst)?

Does GRUB start up at all, or does it just go through the POST screen (where the BIOS counts the RAM, might list some hardware info) and then give you the error?

---

### Post by Dispatch on 2008-03-02
> **Yes said:**
> It means that your Windows partition is still there.

Can you boot into Ubuntu?  What's your /boot/grub/menu.lst file look like (if you're running off of the CD it'll be something like /media/disk/boot/grub/menu.lst)?

Does GRUB start up at all, or does it just go through the POST screen (where the BIOS counts the RAM, might list some hardware info) and then give you the error?


Can you dumb that down a little (if that's possible)

[http://i63.photobucket.com/albums/h132/j18french/Screenshot.png](http://i63.photobucket.com/albums/h132/j18french/Screenshot.png)

I don't know if that screenshot will help but I figured it couldn't hurt to add it.

---

### Post by Yes on 2008-03-02
Again in the terminal, run "gedit /media/disk/boot/grub/menu.lst", and copy and paste the contents here.

Before you get the "Operating system not found" error, does the screen say anything like "GRUB starting" or "GRUB loading stage 1.5"?

---

### Post by Dispatch on 2008-03-02
I'm running that in the terminal but I'm not getting anything at all, nothing comes up.

And nothing about GRUB comes up before Operating System not Found.  It comes up right away when I try to boot to windows.  I have no problem booting ubuntu to the livecd mode.

---

### Post by Yes on 2008-03-02
Alright, go to Places -> Search for files, search for "menu.lst", for the "Look in folder:" dropdown box, choose "filesystem".

---

### Post by Dispatch on 2008-03-02
There is nothing in the dropdown box that says "filesystem", could it possibly have been renamed?

---

### Post by Yes on 2008-03-02
Nah.

Just reinstall GRUB from the live CD, I'm betting that's your problem.  Here's a nice howto: [http://ubuntuforums.org/showthread.php?t=224351&highlight=install+grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=install+grub).

---

### Post by Dispatch on 2008-03-02
Okay, I'll try that but I got back to XP.  I opened gparted and flagged the partiton with XP to boot and when I restarted XP started right up.  Thanks for all the help though!

---

### Post by Yes on 2008-03-02
Sure.  If you ever want to try Ubuntu, try reinstalling GRUB (the guide's in that link I gave you).  Ubuntu should already be installed, you just can't get to it.

---

### Post by sidewinder58 on 2008-03-05
I think by now most of you know this story already, but I'll still state my case as detailed as I can in case something differs.

I have a machine with 2 drives in. On the first drive is my XP Pro SP2 installation. On the second is supposed to Ubuntu 7.04. I installed Ubuntu not remembering that there might be some boot issues and when I restarted it told me "Error loading operating system" (same like the other guy).

I have got the GRUB loader to appear a few times under various circumstances and then it goes back to saying "Error loading operating system", but I'd like to know how I can get my system to use the WINNT bootloader once more cos I prefer to copy the linux boot image to the NT partition and boot that way round. 

I've tried gparted like the other guy did but I don't see anything that needs changing. 

I've tried Recovery Console to repair the NT bootloader and also no joy.

I'm obviously missing something. Would someone be so kind as to help me figure out what it is?

---

### Post by sidewinder58 on 2008-03-05
Just a quick update...

I booted with the Ubuntu 7.04 LiveCD and ran sudo gparted in the terminal. I noticed that both the linux partition and the windows partition were set with boot flag. I disabled the boot flag on the linux partition and now it seems to boot winxp ok.

I am gonna try to create that linux boot image and add it to the winxp boot.ini

---

### Post by Joeb454 on 2008-03-05
You might be better of using GRUB to boot into Windows, MS bootloaders tend to not play nice with Linux

---

### Post by maniac_X on 2008-03-05
> **sidewinder58 said:**
> Just a quick update...

I booted with the Ubuntu 7.04 LiveCD and ran sudo gparted in the terminal. I noticed that both the linux partition and the windows partition were set with boot flag. I disabled the boot flag on the linux partition and now it seems to boot winxp ok.

I am gonna try to create that linux boot image and add it to the winxp boot.ini

Sidewinder, since you are using 2 harddrives, I may have an easy solution for you. I myself use 2 h.drives as follows:

step one: installed only drive #1 set as single and master, installed XP Pro SP2

step two: installed drive #2 set as master in duel drive configuration and set drive #1(XP Pro) to slave in duel drive configuration. On drive #2, Ubuntu was installed and since it is master this is also where grub is installed.  It did however recognize the drive #1 as having Windows so that is listed in the grub as well.

Now when I boot, I boot from the drive #2(Ubuntu) which is set as master. Windows shows in grub and I can boot from that as well. I also have 2 options available, 1.) I can enter BIOS during POST and set my drive #1(Windows) to boot first thereby eliminating grub and the Ubuntu drive al together or 2.) I can also remove the Ubuntu drive (#2) completly and reset the Windows drive as master/single and everything is back to before I had Ubuntu.

This setup with Ubuntu(master) and Windows(slave) is especially useful if I want to play with different distros and not have to worry that it will affect my Windows drive and cause it to be inaccesible for some reason.  It's just a small matter to reset the jumper on the drive or enter into BIOS.

---

