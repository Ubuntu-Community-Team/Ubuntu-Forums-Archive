---
title: "Grub question"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by englishmen on 2006-10-09
I have XpPro and ubuntu duel booting of the same HD(80gb split 60/20) and i need to reinstall xp because of a problem i have caused :-(. I was hoping to reformat and xp partition and reinstall xp, will i still get the grub menu at boot up?

Thanks.

---

### Post by Kateikyoushi on 2006-10-09
Windows will overwrite your MBR but you can restore it with the ubuntu live disc.

[Restore grub from live cd.]("http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub")

---

### Post by podunk on 2006-10-09
I told my XP install that if even thought about messing up it was gone. Dead, formated, kaput! It's been running very nicely since. :-D Maybe you could wave your Ubuntu live CD at your XP? If not - kill the poor thing and put it out of it's misery.

---

### Post by seshomaru samma on 2006-10-09
A _much faster_ way of resoring Grub is using [[COLOR="Red"]this[/COLOR] e]("http://www.sysresccd.org/Main_Page")xcellent System Rescue CD (Gentoo based) 
the commands are the same as in Kateikyoushi's link except that you don't need sudo in the first command , just :
```
grub
```

---

### Post by jd65pl on 2006-10-09
There is a page on the ubuntu wiki for this problem [click here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by englishmen on 2006-10-10
Thanks for the help everyone, on the link jd65pl supplied it has a  section called

"Using the Alternate/Install CD and Overwriting the Windows bootloader"

can someone please confirm that is what i need to do?

Thanks

---

### Post by Kateikyoushi on 2006-10-10
Yes, that will do.

---

### Post by englishmen on 2006-10-10
Thanks Kateikyoushi.

---

### Post by wieman01 on 2006-10-10
> **jd65pl said:**
> There is a page on the ubuntu wiki for this problem [click here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")
Definitely. Have used it a number of times. Eventually got rid of Windows, however. That was the smartest move so far.

---

### Post by englishmen on 2006-10-11
Does anyone know if its possible to install GRUB to a USB flash stick and set my bios to boot from the stick? This way when i want to play a game on windows all i have to do is not insert the stick and my PCs bios will just continue to boot from the HD.

I also wont have to worry about reinstalling GRUB again because i do reinstall windows quite a bit.

Thanks.

---

### Post by bulldog on 2006-10-11
Reinstalling GRUB with the live cd is a done in minutes.

Copy the following in a text file and store it on your computer so you have it always nearby.

Boot into the live Ubuntu cd. This can be the live installer cd or the older live session Ubuntu cds.

When you get to the desktop open a terminal and enter. 


```
sudo grub
```


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands


```
find /boot/grub/stage1
```

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)


```
root (hd?,?)
```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr


```
setup (hd0)
```

Finally exit the grub shell


```
quit
```

That is it. Grub will be installed to the mbr.

---

### Post by gn2 on 2006-10-11
> **englishmen said:**
> Does anyone know if its possible to install GRUB to a USB flash stick and set my bios to boot from the stick? This way when i want to play a game on windows all i have to do is not insert the stick and my PCs bios will just continue to boot from the HD.

I also wont have to worry about reinstalling GRUB again because i do reinstall windows quite a bit.

Thanks.

It is possible to have a Linux OS and Grub on a USB flash drive or hard drive.

PCLinuxOS has a fully automated installer for doing so.

With Ubuntu installing to USB is much more difficult.

If you have a desktop PC and can add a second hard drive, there is another option. You can install Ubuntu and Grub on second hard drive after having first disconnected the Windows drive.

To select which OS to boot, press F8 (or whatever key depending on your BIOS) to bring up the Boot Device Selection List.

You can change the BIOS boot order to have the desired default OS boot first.

If taking this option with IDE drives, Windows > Master, Ubuntu & Grub > Slave.

When installing (or re-installing) each OS, make sure the other drive is disconnected.

This completely avoids any Grub hassle with re-installing XP or after Ubuntu updates.

---

### Post by ReaderRat on 2006-10-11
> **seshomaru samma said:**
> A _much faster_ way of resoring Grub is using [[COLOR="Red"]this[/COLOR] e]("http://www.sysresccd.org/Main_Page")xcellent System Rescue CD (Gentoo based) 
the commands are the same as in Kateikyoushi's link except that you don't need sudo in the first command , just :
```
grub
```

Thank you for your link to System Rescue CD. I had heard of it, but did not know where to get it.

---

### Post by .t. on 2006-10-11
A better way with the stick is to format it in Windows, copy over C:\ntldr and C:\ntdetect.com and C:\boot.ini onto it, then set it up so that you only boot to Windows when you have the stick in! You'll start to forget, and end up using Ubuntu more. This is a *good* thing!

---

### Post by englishmen on 2006-10-15
Thanks for all the help everyone, Ive decided to make it even easier and just install ubnut on my laptop which Ive done and it works great.

One question tho even tho Ive only got ubuntu installed, GRUB still launches at start up. Granted it just boots ubuntu with out delay but i thought GRUB was a app for multiple OS boot machines or is it needed for something else? If not can i improve start up by removing it?

Thanks

---

### Post by Kateikyoushi on 2006-10-15
You use it to launch different kernels, not just to select the OS.
Change the timeout in menu.lst if it bothers you.

---

### Post by Bigbluecat on 2006-10-15
Grub is a generic bootloader used by Ubuntu. Do not remove it or Ubuntu will not boot.

Grub just happens to be a better boot loader than Windows and copes very well with multiple OS's.

---

### Post by .t. on 2006-10-15
GRUB is important to Linux and to other operating systems.

The Linux kernel is 32-bit binary image and is more than one sector big (512 bytes). When the system first boots, it is in 16-bit mode and the BIOS loads and executes the first sector of the boot device. GRUB (stage 1) sits in that sector, ready to load stage 2. When stage 2 is loaded, it enables the A20 gate, allowing access to more memory, and switches to 32-bit mode. This allows for all the system's memory and CPU functions to be used. Then, it loads the kernel image from the disk and is now ready to execute it. Without it, the kernel cannot be executed directly, and so your system will not boot.

These drawbacks have been around since the early days of computing, and are what EFI is designed to combat. With EFI, you don't really need a bootloader.

---

