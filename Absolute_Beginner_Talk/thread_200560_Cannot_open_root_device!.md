---
title: "Cannot open root device!"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by Kuraboy on 2006-06-20
hi!

I too downloaded the linux and initrdg.gz and typed

loadlin linux initrd=initrd.gz vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --

and I got the same problem:

VFS: Cannot open root device "rd/0" or unknown-block(0,0)
Please append a correct "root=" boot option
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

I tried vmlinuz instead of linux and typed:

loadlin vmlinuz initrd=initrd.gz root=/dev/ram0

but still smae problem, any help apriciated!!! and need please!

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(1,0)

---

### Post by encompass on 2006-06-20
What the heck are you doing?  Please be more descriptive...:)

---

### Post by Kuraboy on 2006-06-20
Hi!

sorry... my fault.. when you get into things you think everyone knows what your saying.. sorry again ^_^;;;

from the start:

I want to install Xubuntu on my laptop, which have a broken CD-rom... 

so I searched and found some toturials on how to instal it by booting from dos.. I have Win98 on my laptop... 

I downloaded linux and initrd.gz and loadlin...

type in the commands above.. but I got the error message saying to append correct "root=" boot option

why didnt it work? 

I followed this: [https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

it is a slow PC so I thought Xubuntu is better than Ubuntu for it... 

thnx for your reply :)

---

### Post by Kuraboy on 2006-06-20
Hi again!

just an update: I tryed GrubForDos instead of Laodlin... and the installation program worked for both kernels... linux and vmlinuz...

linux: the installation stopps when it is starting up the partitioner at 52%

while vmlinuz: it want an installer ISO... what is that?

I downloaded Xubuntu, xubuntu-6.06-desktop-i386.iso... but when it searched for an installer ISO it couldnt find anything..

please any help!! This is getting really messy ](*,)

---

### Post by user1397 on 2006-06-20
the guide down in my signature labeled "downloading and installing ubuntu" is exactly what it says, but i think it can help you with xubuntu, as long as you replace the ubuntu parts with xubuntu.  its basically the perfect guide on that subject.

---

### Post by Kuraboy on 2006-06-20
Hi!

thnx... but my laptops cd-rom is broken as I meantioned... thats the big problem...

basicly I want to install from HDD without booting from CD-rom... what to do?

---

### Post by user1397 on 2006-06-20
[quote=Kuraboy]Hi!

thnx... but my laptops cd-rom is broken as I meantioned... thats the big problem...

basicly I want to install from HDD without booting from CD-rom... what to do?[/quote]do you have a usb flash drive handy?  here in the forums there's a thread about someone successfully installing ubuntu using a usb stick, let me see if i can find it...

---

### Post by Kuraboy on 2006-06-20
Hi!

I dont have USB flash ... but thnx... maybe if everything fails I will get one... :)

but what I am trying to do is this..

[http://www.archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/hd-media/](http://www.archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/hd-media/)

if you go to that site, you will find that there are two files, vmlinux and initrd.gz in the hd-media folder...

I want to use them.. now I downloaded xubuntu iso file.. but the installation program asks me for an installer ISO... what is that?! 

thnx for your time :)

---

### Post by user1397 on 2006-06-20
[quote=Kuraboy]Hi!

I dont have USB flash ... but thnx... maybe if everything fails I will get one... :)

but what I am trying to do is this..

[http://www.archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/hd-media/]("http://www.archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/hd-media/")

if you go to that site, you will find that there are two files, vmlinux and initrd.gz in the hd-media folder...

I want to use them.. now I downloaded xubuntu iso file.. but the installation program asks me for an installer ISO... what is that?! 

thnx for your time :)[/quote]that's not the way to install ubuntu, the real way is the little asterisk after "downloading and installing ubuntu" in my signature

---

### Post by Kuraboy on 2006-06-20
Hi!

I visited your site... but it want me to burn a CD.. and I have... that is how I have Ubuntu on my main PC... but my laptop's cdrom is broken... and if I lose win98 from it, I dont know what to do.. so I tried installing it in another way... but not working :(

---

### Post by user1397 on 2006-06-20
[quote=Kuraboy]Hi!

I visited your site... but it want me to burn a CD.. and I have... that is how I have Ubuntu on my main PC... but my laptop's cdrom is broken... and if I lose win98 from it, I dont know what to do.. so I tried installing it in another way... but not working :([/quote]well i don't know how to install linux without using any removable media,  so unless you can't get another cd/drive and connect it to your laptop, i don't really know what else to tell you.

---

### Post by richbarna on 2006-06-20
[QUOTE=Kuraboy]hi!

I too downloaded the linux and initrdg.gz and typed

loadlin linux initrd=initrd.gz vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --

and I got the same problem:

VFS: Cannot open root device "rd/0" or unknown-block(0,0)
Please append a correct "root=" boot option
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

I tried vmlinuz instead of linux and typed:

loadlin vmlinuz initrd=initrd.gz root=/dev/ram0

but still smae problem, any help apriciated!!! and need please!

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(1,0)[/QUOTE]

Take a look at this guide, maybe your commands were typed wrong ?
[http://www.theonelab.com/files/mirrors/win2linstall.html#loadlin]("http://www.theonelab.com/files/mirrors/win2linstall.html#loadlin")

---

### Post by user1397 on 2006-06-20
[quote=richbarna]Take a look at this guide, maybe your commands were typed wrong ?
[http://www.theonelab.com/files/mirrors/win2linstall.html#loadlin]("http://www.theonelab.com/files/mirrors/win2linstall.html#loadlin")[/quote]wow i didn't know this was actually possible!

---

### Post by Kuraboy on 2006-06-20
thnx guys...

@richbarna: I have followed this guide, and many others... I get a new problem for each time... 
because now I can begin the installation process if I load linux kernel... but it hangs

and vmlinuz wants something called 'installer ISO image'???!?!?!

thnx guys... I give up for now... will try tomorrow...

edit:-----------
@erik1397: not for me... atleast not today ;)

---

