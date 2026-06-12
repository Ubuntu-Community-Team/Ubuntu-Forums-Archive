---
title: "Help With Install"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by ianb72 on 2007-03-14
Hi all
I am trying to install the latest verion 6.10 onto my spare PC before I completely get rid of MS XP on my main PC, just to make sure I am happy with it and it can run all the software I need for my amateur radio.

My spare PC is an old AMD Duron 800Mhz with 512Mb of Ram and 2x20Gb hard drives, but when I go to install the software from boot up I get a page of messages and the last one saying something along the lines of trying to kill idle processes and then the PC just sits there doing nothing!

Any suggestions?

Thanks
Ian

---

### Post by dstew on 2007-03-14
How are you installing? Using the LiveCD?

---

### Post by ianb72 on 2007-03-14
To be honest I am not sure I just download the 700MB file from the site and burnt it onto cd, the file name is ubuntu-6.10-desktop-i386

---

### Post by dstew on 2007-03-14
When you burnt the file to the CD, did you do it correctly? That is, did you burn a disk image, or did you burn a data disk? If you explore the disk, and it has only one file on it with an .iso extention, then you burned a data disk. That is incorrect. You have to burn an image disk.

---

### Post by ianb72 on 2007-03-14
> **dstew said:**
> When you burnt the file to the CD, did you do it correctly? That is, did you burn a disk image, or did you burn a data disk? If you explore the disk, and it has only one file on it with an .iso extention, then you burned a data disk. That is incorrect. You have to burn an image disk.

OK I have explore the cd and I have several files, I used Power ISO to burn the ISO file like I've used loads of times before, I have even checked out the checksum and all is fine there.

Ian

---

### Post by dstew on 2007-03-14
Does the Ununtu desktop load and function normally when you boot the live CD? Or do you only get problems when you start the installer?

---

### Post by Shmifty on 2007-03-14
I am having the same problem. The only difference is instead of ubuntu launching the GUI I get a console type of screen, and I am unsure of what to do from there.

---

### Post by lamalex on 2007-03-14
do a check check when you boot, its an option rather than boot to livecd, or try the alternate install cd.

---

### Post by Shmifty on 2007-03-14
I have checked it and the disk is fine, I have read in another topic my graphics card may be the problem with the lack of gui. How do I run the installer from the console area?

---

### Post by ianb72 on 2007-03-14
> **Iamalex said:**
> do a check check when you boot, its an option rather than boot to livecd, or try the alternate install cd.

When I stick the cd in my Win XP pc it brings up a screen, but when I stick it in the AMD 800Mhz spare PC, and select Install Linux it brings up \casper\?? then dots but on the second one it brings up the black window full of writing and the last line says Kernel Panic or Panic Kernel trying to kill idle process, I have now burnt this onto 2 different CD's and tried 2 different CD-Roms on my spare PC, it was running win XP Pro SP2 fine before

---

### Post by dstew on 2007-03-14
Again, on your spare AMD 800Mhz PC, when you boot the Live CD, do you see the initial splash screen with Ubuntu, followed by a series of menu options?

---

### Post by ianb72 on 2007-03-14
> **dstew said:**
> Again, on your spare AMD 800Mhz PC, when you boot the Live CD, do you see the initial splash screen with Ubuntu, followed by a series of menu options?

Yeah I get that, a list of 4 or 5 options

---

### Post by dstew on 2007-03-14
And then, you select the first menu item "Start or Install Ubuntu", correct? And it goes crazy immediately?

---

### Post by nonpareilpearl on 2007-03-14
I may be wrong on this, but you said you are using the i386.iso file, and I'm pretty sure that works only on Intel computers. I know that Phoenix (my desktop) is an AMD and my laptop is an Intel, and I had to use separate disk images for both (when I accidentally put the i386 into the AMD computer it didn't run). Try selecting the alternate options when you go to the site and choosing one of the AMD iso's.

---

### Post by Songwind on 2007-03-14
> **nonpareilpearl said:**
> I may be wrong on this, but you said you are using the i386.iso file, and I'm pretty sure that works only on Intel computers. I know that Phoenix (my desktop) is an AMD and my laptop is an Intel, and I had to use separate disk images for both (when I accidentally put the i386 into the AMD computer it didn't run). Try selecting the alternate options when you go to the site and choosing one of the AMD iso's.

The i386 disc is the 32-bit, Intel-compatible version.  That includes AMD chips.  (I just did an install of Kubuntu i386 last week on my AMD64 system).

---

### Post by nonpareilpearl on 2007-03-14
> I just did an install of Kubuntu i386 last week on my AMD64 system
Fair enough, perhaps something else was going on with mine :)

---

### Post by dstew on 2007-03-14
Ian72b, if you get kernel panic when trying to boot from a Live CD that you know works on other computers, the problem is an incompatibility between the Live CD kernel and that specific computer. One way this can happen is if you have bad hardware (no good disk, mouse or keyboard). The other way this can happen is that the assumptions the Live CD makes about your system are incorrect, and it tries to use a kernel that does not match your system.

To modify the kernel that the Live CD loads to be compatible with your system, you can add boot options to a command line before clicking the "Start or Install" choice. You open this boot command line by pressing F6 while the initial screen is displayed. If you don't know exactly what the incompatibility is, you can try the boot options most likely to work. Type these on the boot command line:

```
ide=nodma apci=force
```

You can try one, then the other to see which one (if either) works. You might also have to use one or both of these options in the kernel boot command line after you get it installed on your hard disk.

---

### Post by ianb72 on 2007-03-14
> **dstew said:**
> And then, you select the first menu item "Start or Install Ubuntu", correct? And it goes crazy immediately?

Not immediately it does a few things on the screen first then brings up the black screen with all the text and numbers

---

### Post by dstew on 2007-03-14
Yes, that is Live CD kernel panic, an uncommon illness. See my other posts for some thoughts on treatment.

---

### Post by ianb72 on 2007-03-14
> **dstew said:**
> Yes, that is Live CD kernel panic, an uncommon illness. See my other posts for some thoughts on treatment.

Done what you said with the ide=nodma apci=force and still I got the same error!!

The error is:
<0> Kernel panic - not syncing: Attempted to kill idle task!

It couldn't be something to do with the old PCI video card I've got installed in the system could it?

I am gonna try another HDD and CD-Rom drive, but it was working fine with Win XP Pro SP2!!

---

### Post by dstew on 2007-03-14
It's got to be some hardware incompatibility. The messages on the screen above the kernel panic message will have more information. Kernel panic is just the final common pathway for a kernel that cannot load. Can you post the messages that are printed on the screen above the kernel panic message?

The video card could certainly be a cause. What kind is it? See this for some other boot options that might help.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by ianb72 on 2007-03-16
> **dstew said:**
> It's got to be some hardware incompatibility. The messages on the screen above the kernel panic message will have more information. Kernel panic is just the final common pathway for a kernel that cannot load. Can you post the messages that are printed on the screen above the kernel panic message?

The video card could certainly be a cause. What kind is it? See this for some other boot options that might help.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Hi
Yeah I've found out what it was, it was a knackered CD-Rom drive. when I changed it it works fine.

It just keeps asking for a username/ password as I'm trying to install it, I've tried root, admin but all are incorrect!!

What am I doing wrong??

---

### Post by honns on 2007-03-16
are you using su or sudo to gain root access?

---

### Post by dstew on 2007-03-16
It wants you to create a username and password. Root is reserved, and the root account is not activated in Ubuntu installs by default. You don't need a root account, because you just use the sudo command as a regular user to do administrative things.

Just create a simple username for yourself, and then create your password.

---

### Post by ianb72 on 2007-03-16
No its when I am trying to set up the localization settings from the Install icon from the Desktop, it just asks me to type in a username then a password

---

### Post by honns on 2007-03-16
I am not sure what you mean, where excactly are you in the install process?

---

### Post by ianb72 on 2007-03-16
> **dstew said:**
> It wants you to create a username and password. Root is reserved, and the root account is not activated in Ubuntu installs by default. You don't need a root account, because you just use the sudo command as a regular user to do administrative things.

Just create a simple username for yourself, and then create your password.

OK when the CD boots up to the Destktop, it then asks for a Username which I type in one, then a Password, again I enter one.  Then it says Username/Password incorrect and then something along the lines of it must all be in the same case, which it was!!

---

### Post by ianb72 on 2007-03-16
> **honns said:**
> I am not sure what you mean, where excactly are you in the install process?

Right at the begining all I did was select Start/Install Ubuntu 6.10 then it boots to the Desktop, then it asks for a username and password!

---

### Post by dstew on 2007-03-16
I am confused. If you are truly booting the Live CD (put CD in the drive, turn off the computer, turn it on) it should come up with the Ubuntu splash screen, and the first menu item should read Start or Install. Where do you see "Start/Install Ubuntu 6.10" on the splash screen?

---

### Post by honns on 2007-03-16
to ianb -  has it finised installing, askes you to remove the disk and restart?

to dstew - list for us the options on the Ubuntu splash screen

is it possible that your not actually booting from the cd-drive?  you must go to your bios to make sure that your cd-drive is higher than your hard drive or some bios might have an option for a boot selection on the first screen when you start up. make sure that you select the cd-drive.

---

### Post by ianb72 on 2007-03-16
> **honns said:**
> to ianb -  has it finised installing, askes you to remove the disk and restart?

to dstew - list for us the options on the Ubuntu splash screen

is it possible that your not actually booting from the cd-drive?  you must go to your bios to make sure that your cd-drive is higher than your hard drive or some bios might have an option for a boot selection on the first screen when you start up. make sure that you select the cd-drive.

Yeah I am booting from the CD Rom drive as the Hard Drive is Blank, there is only one hard drive and one cd-rom drive in the system.

The first screen I get is the screen that asks you if you want to start and install Ubuntu 6.10 which I selected then it goes to the Desktop and then thats when it asks for the username/password, and no matter what I enterit always says it is incorrect!
SO no it has not even started to install yet alone finish installing, I don't get to enter where I live or any network or anything like that.

Ian

---

### Post by honns on 2007-03-16
sorry about the earlier post - i didnt understand what was going on

so you cant even get the live disk to boot correctly.  what i would do, is redownload the iso and burn it again, but this time you should try and use a different source.  every time that I have used the live disk, it simply boots to the desktop without a password.

---

### Post by dstew on 2007-03-16
I am still puzzled. The first thing that happens when you click the install icon on a regular Ubuntu live CD is you select your language, then your time zone. It does not ask you to create a username or password until later. Here is a video of a regular installation. Does the desktop you see look like this?

[http://www.metacafe.com/watch/334327/easy_linux_install_ubuntu_6_10/](http://www.metacafe.com/watch/334327/easy_linux_install_ubuntu_6_10/)

---

### Post by ahmatti on 2007-03-16
For some reason I always have trouble trying to install using the live cd so I always use the alternate install disc. It's much faster too!

---

### Post by dt71 on 2007-03-17
Greetings -- I have the same problem as Ian.  The strange thing is the live CD rolls right through to the desktop on my laptop (Celeron 433 MHz) but not on my PC (PII 350 MHz), which is where I want to install it.

Is the only option the alternate install CD?

david

> **ianb72 said:**
> Yeah I am booting from the CD Rom drive as the Hard Drive is Blank, there is only one hard drive and one cd-rom drive in the system.

The first screen I get is the screen that asks you if you want to start and install Ubuntu 6.10 which I selected then it goes to the Desktop and then thats when it asks for the username/password, and no matter what I enterit always says it is incorrect!
SO no it has not even started to install yet alone finish installing, I don't get to enter where I live or any network or anything like that.

Ian

---

### Post by dstew on 2007-03-18
You mean the Live CD rolls through to the Window desktop?

---

### Post by dt71 on 2007-03-19
Yes, on the laptop the live CD rolls through to the Window desktop and allows me to use the OS from there.  On the PC it gets stuck on the request for username and password just before allowing me access to the Window desktop -- it counts down waiting for me to enter something, then begins loading the desktop, but then loops back to ask for username and password again.

(I now recall seeing a message along the way saying "failed to load RDST (??)" or something like that but I will have to try it again tonight to find the exact message)

thanks,

david

---

### Post by dt71 on 2007-03-19
Okay, the error message is:

ACPI: unable to locate RSDP

In following this problem on other threads in the forum, this error seems related to a variety of difficulties.  I will see if changing the ACPI settings in the BIOS helps.

---

### Post by dt71 on 2007-03-21
For the record, I entered "ubuntu" as username and did not enter a password.  This seemed acceptable as the "incorrect password" message did not appear.  Still, in reaching the desktop it began flashing on and off and then returns to the same username/password screen.

I will now turn to the alternate install CD.

---

