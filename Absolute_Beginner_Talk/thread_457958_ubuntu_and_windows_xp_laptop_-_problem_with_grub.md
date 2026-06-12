---
title: "ubuntu and windows xp laptop - problem with grub"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by lochstar360 on 2007-05-29
Hi,
I only downloaded Ubuntu LiveCd yesterday and loved it, so i double click the install icon and installed it onto a usb Disk (5gb). I have also Windows Xp on the laptop hard drive. So everything works fine, but if the usb is not plugged in when the computer is at GRUB it says error and refuses to do anything else. I want to be able to use My Windows Xp installation even without the usb plugged in. Is it possible to get rid of grub and for it to work. I was hoping (and i read somewhere) that if you just do the simple installation to a usb from the LiveCD all you have to do is plug it in to other computers and select it as the boot device and off it goes. Instant Ubuntu. Please help me.

---

### Post by Bachstelze on 2007-05-29
You need GRUB. If you don't have it, your Ubuntu won't boot. Your problem is that one part of it was installed on the MBR of your internal hard drive, and the other on the external, so when GRUB starts, it searches for the file son the external, doesn't fin them and throws an error. Here's what to do :

1) Restore the MBR of your internal drive using a Windows CD.
2) Install GRUB on the MBR of your external drive.
3) Setup your BIOS to boot the external first. If the external is plugged in, it will boot from it and run GRUB. If not, it will ignoe it silently and boot from the internal.

---

### Post by lochstar360 on 2007-05-29
thanks but i really have no idea what is an mbr and how do i get it off the windows disk. I can still access both systems perfectly but the USB HAS to be plugged in.

---

### Post by seshomaru samma on 2007-05-29
> 
1) Restore the MBR of your internal drive using a Windows CD.
2) Install GRUB on the MBR of your external drive.
3) Setup your BIOS to boot the external first. If the external is plugged in, it will boot from it and run GRUB. If not, it will ignoe it silently and boot from the internal.

1) boot from a Windows cd - choose option 'r' (rescue or recovery or whatever they call it)
  when you get the command prompt ,go
```
fixmbr
```
2) not 100% but it should be something like:
boot from a live Cd
open a terminal
Type "grub" which makes a GRUB prompt appear.
then
```
find /boot/grub/stage1
```You'll get a response like  "(hd0,3)". Use whatever your computer spits out for the following lines:
```
root (hd0,3)
```
(replace hd0,3 with whatever the output was for the previous command.)
next,
```
setup (hd0,3)
```
(again replace hd0,3 with whatever the output was for the previous command)
```
quit

```
3) this depends on your BIOS , i guess you can figure this out yourself

as i said - not 100% sure about the 2nd step - hope someone can correct me

---

### Post by nutz on 2007-05-29
See this post...

[http://ubuntuforums.org/showthread.php?t=458003&highlight=ubuntu+on+usb+hard+drive](http://ubuntuforums.org/showthread.php?t=458003&highlight=ubuntu+on+usb+hard+drive)

I have done this on quite a few systems now and ran into this problem. That is why I go for the method of completely disabling the internal drives. 

Here is how I fixed my windows drive...

Use a windows startup disk that will provide a DOS command prompt. Use the following command at said command prompt...

fdisk /mbr

Then reboot and it should boot windows just like normal...

Now try the external drive install with my method described in the post above.

---

### Post by Duck2006 on 2007-05-29
> setup (hd0,3)

This sould read some thing like 

setup (hd1)

whatever your computer spits out

---

