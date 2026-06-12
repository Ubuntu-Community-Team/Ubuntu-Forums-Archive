---
title: "Can't create bootable USB"
date: 2013-08-17
forum: Apple Hardware Users
---

### Post by GoggleEyedSalmon on 2013-08-17
Now, I know this is the most basic part and I have actually done this many times before. I've created bootable USB sticks for Fedora recently (using the same USB stick) and in the past for Ubuntu using the instructions here [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx), but for some reason it doesn't seem to be working for ubuntu 13.04. I am using sudo dd to create the disk but as soon as it's finished I get a warning saying "this disk is unreadable", and it doesn't boot.

Unetbootin doesn't create a disk that is bootable on a mac and I have no optical drive so this is my only option. Any ideas what I might be doing wrong?

Thanks in advance

---

### Post by GoggleEyedSalmon on 2013-08-17
Obviously the action of writing out a forum post has helped. I seem to have a working disk. 

In case it helps anyone else, I changed the filename from "ubuntu-13.04-desktop-amd64.img" to "ubuntu1304.img" and the path from "/Users/Sam/..." to "~/..."

---

### Post by GoggleEyedSalmon on 2013-08-17
Scratch that, I'm back to an unreadable, unbootable disk again.

Any ideas?

---

### Post by Mk32 on 2013-08-17
I've done it before, and I did not convert the disk image. I just fed it straight with the .iso.

---

### Post by mateo14 on 2013-08-17
I think this program can help you solve a problem:


[http://sevenbits.github.io/Mac-Linux-USB-Loader/](http://sevenbits.github.io/Mac-Linux-USB-Loader/)

---

### Post by GoggleEyedSalmon on 2013-08-19
mk, I tried that but still get an unbootable USB.

mateo, that's great, thanks. This has got me further than before, but now when I boot from the disk I get a grub boot prompt (grub>). Any ideas what I do from here?

---

### Post by bennett2 on 2013-09-12
I used [This]("https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick") link and found I was unable to create a USB stick on mac after converting .iso to .img with 10.10 (supposedly a "out of the box" working solution for my 7.1 macbook pro).  However the exact same steps (followed exactly) worked perfectly when converting 13.04 and 12.04 ISO to .img.  Both were installed from the same USB (I used disk manager to reformat MS-DOS every time before placing a new release on the USB).  I found that at the end of loading the 12.04 and 13.04 image I was greeted by a mac error somewhat along the lines of "disk unreadable" and this denoted a correct mount to me, as the install worked every time afterward.  The 10.10 release NEVER resulted in that message so I eventually went back to the originals, now I am trying to figure out wireless and graphic driver issues :/...

---

### Post by Quackers on 2013-09-14
I spent about 5 hours two nights ago trying to create a persistent bootable live usb and failed.
All the usual suspects failed in an epic way - Unetbootin, USB-creator/Startup Disk Creator and dd from inside Ubuntu. They even failed with the same errors you've been getting. I used 2 different makes of USB stick and still nothing.
In the end I tried doing it manually and that got closer than anything else did.
After all that I decided to give up for the night and just made a non-persistent (normal) Live USB.  They all failed at that too.
The iso is good so I don't know what went wrong.

In the end all I did was use dd from inside Mac OS X and the stick worked right away!

We also must remember that Macs (if that's what you're using) can be very finicky about booting from USB sticks - or so I found.

In the end I installed 13-04 to another USB stick so I can effectively have persistence using that full system install as a live USB.
I have to say though that the installed system on the USB runs quite slowly but as it's only going to be used for repairing my base system it will do.

---

### Post by sudodus on 2013-09-14
Good to know that the result might be different if you use dd from inside Mac OS X and dd in another computer :-)
[COLOR=#696969]But I can't understand what could the different.

-o-
[/COLOR]
Look at this link that discusses the speed of USB pendrives

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

---

### Post by Quackers on 2013-09-14
Yes, I don't know whether it's my choice of usb sticks or the computer.
Having said that, one of my usb sticks is old - it's an Integral 2GB which for some reason (firmware I suspect) has a 1.5MB first partition which cannot be deleted.
This has worked ok for a normal live usb before though.
I have also tried 4GB and 8GB Sandisk Cruzer Blades and none of those was bootable unless I dd'd the image from within my MacBook Pro.
All very odd, though the Mac can be a little flaky about booting from usb sticks occasionally, or even about picking them up at all.

---

### Post by sudodus on 2013-09-14
Some year ago a bought a ten-pack of 4 GB Sandisk Cruzer Blades, and although they are slow, they have been very reliable for me and good for dd-cloned isos. But I have no Mac. I use USB3 pendrives for portable installed systems. Even in USB2 ports they are 5-6 times faster than the Cruzer Blades.

Would it be possible that 'Mac dd' writes something else too, something behind the curtains of the drive (where I think hdparm can write) using calls to proprietary software? The image of the iso file should be the same.

How does a pendrive 'cloned in Mac' work in standard PCs with a standard bios and an intel/amd system?

---

### Post by Quackers on 2013-09-14
Lol, I really don't know. There shouldn't be any difference doing a dd in Ubuntu and doing one in OS X. All I can say is that in my experience it's only working for a live usb if I run it in a Mac. It's all very odd.

---

### Post by Quackers on 2013-09-17
Aha! Some success!
[http://ubuntuforums.org/showthread.php?t=2174630]("http://ubuntuforums.org/showthread.php?t=2174630")

---

### Post by Mk32 on 2013-09-17
I don't know if this would help or not but I simply installed 10.04LTS onto a thumbdrive and it is persistent and fully bootable. Actually it's an 8GB SanDisk Cruzer Glide (hate the design) with a 1.9GB FAT32 volume (first partition) and 6GB Ubuntu partition. Works marvellously. Has Netatalk, Filezilla, Audacity, the works.

---

