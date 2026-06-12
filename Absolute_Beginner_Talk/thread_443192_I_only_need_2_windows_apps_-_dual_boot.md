---
title: "I only need 2 windows apps - dual boot?"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by MartyNg on 2007-05-14
Hello, I have two windows apps that I cannot get rid of. I have a windows install on a 40 gig drive, and just obtained a 120 gig drive I planned on installing ubuntu on. I'm a linux noob, so what's the EASIEST way to set this up? Should I try a dual boot on separate hard drives?  Or would it make sense to just begin a Ubuntu install, and then shoot for some kind of Windows emulation?

The programs are for backing up my PS2 games if it matters - WinHIIP and DVDDecrypter.

Thanks for any assistance!

---

### Post by eyelessfade on 2007-05-14
you might try wine for your programs yes. But there is a number of substitutes for dvddecrypt in linux. You might look at that at least :)

---

### Post by mattmole on 2007-05-14
Hi,

I would say you have three options:

1st would be to do as you say and install Ubuntu to one drive and leave windows on the other. On install Ubuntu should be able to see the other drive with windows installed and let you boot from it.

2nd would be to install ubuntu and wipe windows. Personally, although I hate windows I would not do that. It is good in the VERY odd times that I break my Ubuntu or need to try something out for my family who use windows.

3rd would be to wipe everything, install Ubuntu and then run windows under a virtual machine. Again, if you got rid of windows entirely you may find at somepoint you wish you hadnt (please noone shoot me for saying this! I really do hate windows and use Ubuntu 100% of the time!)

Of course you can try a combination, install Ubuntu, if it does all you want then remove windows. Your programs may work using WINE under ubuntu, but I am not sure.

Personally, do the dual boot!

Matt

---

### Post by zvacet on 2007-05-14
As you are just starting to use linux it is good idea to keep windows.Why?Maybe you will not be satisfied with linux and you will regret deleting your windows.Even if you like Ubuntu keep windows and when you know more about Ubuntu make your decision.I did it that way(if that is important),because I felt unsecure in the begining and didn´t want to end without any OS.Now,I don´t have windows anymore.I have separate home partition and Ubuntu Cd if something goes wrong.

---

### Post by newlinux on 2007-05-14
there is enough disk spaces for both OSs. There is really no need to delete the windows partition, and there are good reasons to keep it around (I still have one computer that is dual boot windows, which I use once in a blue moon, but it is for "Just in case" and a couple programs. However, I have found myself over time shrinking how much space I have allocated to the windows partition...). there is nothing wrong with using windows. I prefer Linux and Ubuntu, but windows has its uses. As for DVDDecryptor, as already mentioned, you can do what it does with native linux apps (I don't know about all the features, as I don't use it). K3b, gnomebaker, dvd::rip, etc. try some of the linux apps out...

---

### Post by Ianman on 2007-05-14
Yep, just start out with dual boot. You may not even like Ubuntu or Linux for that matter! Thats what I did in the beginning. I find myself using Linux a lot more these days though. 

My biggest "problem" is the fact that I am a gamer so until most games only come out on Windows I will stay dual boot. Or I should get an Xbox360 or PS3 for gaming and remove windows altogether. Hmmm..

---

### Post by MartyNg on 2007-05-14
> **mattmole said:**
> 

1st would be to do as you say and install Ubuntu to one drive and leave windows on the other. On install Ubuntu should be able to see the other drive with windows installed and let you boot from it.

Matt

I got antsy and kicked off the ubuntu install a few minutes ago as the only drive in the machine. Should I cancel the install, and put the windows hard drive back in so the Ubuntu installer picks it up? Or can it pick it up later? (I don't care about any user settings transferring over)

---

### Post by MartyNg on 2007-05-14
> **Ianman said:**
> Yep, just start out with dual boot. You may not even like Ubuntu or Linux for that matter! Thats what I did in the beginning. I find myself using Linux a lot more these days though. 


Actually, I've been using Ubuntu for a while off and on with a LiveCD and have liked it a lot.

The ironic thing is that I am a Windows software developer. Obviously, I will need to keep my primary machine on Windows since I need Visual Studio 2005 and SQL Server Management Studio!  ;)

---

### Post by brennydoogles on 2007-05-14
The great thing about linux is that it will happily dual boot from the second drive (which windows will refuse to do). Although Linux outperforms windows in many ways, it still has a few areas in which windows beats it out (such as hardcore PC gaming ease of installing device drivers, not to mention driver availability). If you are used to a 40 GB drive, you will have more than enough space on the 120GB drive if linux does become your primary operating system (like it did for me :O) ), so go for it. My only advice is to make sure that when you are using the partitioning tool during your linux install that you install to the second hard drive by using the little device selector in the upper right hand corner of the partitioning tool. That will avoid disaster for you. Good luck!!!

---

### Post by aeiah on 2007-05-14
> **MartyNg said:**
> I got antsy and kicked off the ubuntu install a few minutes ago as the only drive in the machine. Should I cancel the install, and put the windows hard drive back in so the Ubuntu installer picks it up? Or can it pick it up later? (I don't care about any user settings transferring over)

yes, put your windows hdd in. its the set up i have, and it'll be easier to let linux see it on setup so you dont have to fiddle with fstab (a file that mounts hard drives and partitions on boot).

just make sure you install ubuntu to the correct hard drive (you'll be able to read its size), and in bios, make sure you set it to boot from your ubuntu hdd first. grub, ubuntu's boot loader, will give you the option of booting into windows. if you dont set the ubuntu hdd to boot first then the windows one will, and you wont have the option of booting into ubuntu.

---

### Post by brennydoogles on 2007-05-14
> **MartyNg said:**
> I got antsy and kicked off the ubuntu install a few minutes ago as the only drive in the machine. Should I cancel the install, and put the windows hard drive back in so the Ubuntu installer picks it up? Or can it pick it up later? (I don't care about any user settings transferring over)

For ease of install I would go ahead and put the windows drive back in as the master drive... like I said in my previous post Linux will play nicely :O) .

---

### Post by aeiah on 2007-05-14
as mentioned, dvddecryptor has many linux alternatives. i use acidrip, but there are many more. as for WinHIIP, you may still need windows. there is some talk of it running under wine from a quick search (a program that enables some windows software to run in linux) but i couldnt find anything concrete. there are other options too. i think there's another program that makes it possible but you'll have to google around. if not, you can either dual boot or see if it'll run in a vmware virtual windows desktop. (it'll run windows xp in a window on linux, although there is a performance hit and no direct x support, not that dx would matter for that purpose).

---

### Post by MartyNg on 2007-05-14
> **brennydoogles said:**
> For ease of install I would go ahead and put the windows drive back in as the master drive... like I said in my previous post Linux will play nicely :O) .

I removed my Ubuntu HD and put ONLY my XP hard drive in the new ubuntu machine to make sure it worked, and it doesn't! The drive is detected properly, but won't get into windows whether I use slave, master, or cable select! All I get is a flashing underscore character. 

If I put both hard drives in (XP-master/UBuntu-slave) with a boot into the ubuntu drive, I see grub for a second, and then Ubuntu loads right up, with no mention of an XP drive. However, once Ubuntu is booted up, I can access the filesystem on the XP drive.

I DID move the XP hard drive back to its original machine, and it works fine there.

Any ideas?

---

### Post by brennydoogles on 2007-05-14
> **MartyNg said:**
> I removed my Ubuntu HD and put ONLY my XP hard drive in the new ubuntu machine to make sure it worked, and it doesn't! The drive is detected properly, but won't get into windows whether I use slave, master, or cable select! All I get is a flashing underscore character. 

If I put both hard drives in (XP-master/UBuntu-slave) with a boot into the ubuntu drive, I see grub for a second, and then Ubuntu loads right up, with no mention of an XP drive. However, once Ubuntu is booted up, I can access the filesystem on the XP drive.

I DID move the XP hard drive back to its original machine, and it works fine there.

Any ideas?

I believe that your grub timeout may be too short. I am typing this from a windows laptop, so I may be wrong, but if you edit your menu.list
```
sudo gedit /boot/grub/menu.list
```
You should be able to set the timeout to any number of seconds that you would like (I recommend between 10 and 30 depending on how often you will be booting windows). If that still doesn't work, just reply back and we'll keep working on it!!

---

### Post by neodarksaver on 2007-05-14
Try wine first... and read the compatibility list for crossover. If they dont work, dual-boot, or VMware.

---

### Post by MartyNg on 2007-05-14
> **brennydoogles said:**
> I believe that your grub timeout may be too short. I am typing this from a windows laptop, so I may be wrong, but if you edit your menu.list
```
sudo gedit /boot/grub/menu.list
```
You should be able to set the timeout to any number of seconds that you would like (I recommend between 10 and 30 depending on how often you will be booting windows). If that still doesn't work, just reply back and we'll keep working on it!!

Cool - I tried that and had enough time to get into the grub menu now, but there are no windows entries. Just ubuntu.

This probably has nothing to do with Ubuntu since the XP drive doesn't work when it's the ONLY hard drive in my new ubuntu box. I've never had a problem transferring an XP hard drive between machines before!

For future readers of this post, I should point out that the correct command to run is

sudo gedit /boot/grub/menu.lst   (no 'i' in list)

---

### Post by newlinux on 2007-05-14
> **MartyNg said:**
> Cool - I tried that and had enough time to get into the grub menu now, but there are no windows entries. Just ubuntu.

This probably has nothing to do with Ubuntu since the XP drive doesn't work when it's the ONLY hard drive in my new ubuntu box. I've never had a problem transferring an XP hard drive between machines before!

For future readers of this post, I should point out that the correct command to run is

sudo gedit /boot/grub/menu.lst   (no 'i' in list)

When using graphical apps you should actually use gksudo instead of sudo...
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

That is a bit odd, you might still be able to get grub to boot to it however by manually listing it in menu.lst

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_boot_into_Windows_installed_on_a_seperate_SATA_drive](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_boot_into_Windows_installed_on_a_seperate_SATA_drive)

Might help

---

### Post by MartyNg on 2007-05-14
> **newlinux said:**
> When using graphical apps you should actually use gksudo instead of sudo...
That is a bit odd, you might still be able to get grub to boot to it however by manually listing it in menu.lst


No luck there. I got some error about invalid executable.

I know I am brand new to the Linux world, but wouldn't it make sense to troubleshoot the XP hard drive and get that booting properly in the new machine before even messing around with Ubuntu? Ubuntu couldn't have screwed anything up in the BIOS, could it?

---

### Post by newlinux on 2007-05-14
> No luck there. I got some error about invalid executable.

Did you type?

```
gksudo gedit /boot/grub/menu.lst
```

It's not a big deal, but it can cause problems if you don't replace sudo with gksudo in some cases with graphical apps.

> I know I am brand new to the Linux world, but wouldn't it make sense to troubleshoot the XP hard drive and get that booting properly in the new machine before even messing around with Ubuntu? Ubuntu couldn't have screwed anything up in the BIOS, could it?

Not a bad idea, and it is highly unlikely Ubuntu did anything to the BIOS. However, since you state that ubuntu can see the XP drive, it might not hurt to try and get grub to be able to boot to windows before troubleshooting the hard drive, since that is ultimately what you will end up doing anyway, and you could just try it out real quick to see if it works now.

---

### Post by Big_Croc7 on 2007-05-14
umm one question, just to clarify... you're taking the HD with XP on from another machine and putting it into this one?

although you say you haven't had problems doing that before, it sounds like you've been very lucky!!!  Unless the hardware is nearly identical I wouldn't expect that to work at all.  It won't be loading any of the right drivers, nevermind having to worry about windows activation nasties, even with a volume licence key.

If you want this HD to stay in this machine and not the other one, try booting from a windows CD, with just the windows HD connected, and running windows recovery option - once that's working, then try adding the Ubuntu HD and booting XP with grub.  It sounds very much like a windows error to me!

---

### Post by MartyNg on 2007-05-14
> **newlinux said:**
> Did you type?
```
gksudo gedit /boot/grub/menu.lst
```

It's not a big deal, but it can cause problems if you don't replace sudo with gksudo in some cases with graphical apps.

Not a bad idea, and it is highly unlikely Ubuntu did anything to the BIOS. However, since you state that ubuntu can see the XP drive, it might not hurt to try and get grub to be able to boot to windows before troubleshooting the hard drive, since that is ultimately what you will end up doing anyway, and you could just try it out real quick to see if it works now.

I typed with the 'gk', exactly like you said. I ended up formatting and reinstalling XP over itself, and it seems to work now, but I still can't get grub to boot into XP, still that **error 13 "Invalid or unsupported executable format"**.

---

### Post by MartyNg on 2007-05-14
I finally got it working. After reinstalling windows on one hard drive, and then reinstalling ubuntu on the slave drive, GRUB picked up the Windows XP boot as an option automatically!

Lesson of the day:
If you want to dual-boot, make sure you have an XP drive as your master drive first!

---

