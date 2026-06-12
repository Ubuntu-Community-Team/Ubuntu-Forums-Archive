---
title: "How can I boot the USB uing Grub2 in the hard disk?"
date: 2012-04-13
forum: Apple Hardware Users
---

### Post by HotForLinux on 2012-04-13
How can I boot a linux system in an USB memory stick that uses the  syslinux bootloader in an Apple MBP3,1 machine that has rEFIt and Grub2 installed. Maybe instructing Grub to do so?. First I choose the system in a menu presented by rEFIt and after choosing Ubuntu, Grub2 displays a menu.

When I boot with the USB plugged in, there's an icon for each system  installed: MacOS, Ubuntu ,.. and an icon for the USB (Tux with an USB  drive). But I cannot boot the system in the USB choosing that option because a message says  that booting with external devices is not supported.

I still don't know if this happens always but after playing with Grub at  boot time, trying to boot the system in the USB, and then choosing to  boot the Ubuntu in the HD, Ubuntu started with the pointer (cursor) frozen. Only after  unplugging the USB (no need to reboot) I could use the touchpad to move the pointer around.

Inside the USB:

 ```

casper/
    filesystem.size
    filesystem.squashfs
    initrdf.gz
    initrd.gz
    initrds.gz
    vmlinuz

isolinux/
    boot.cat
    memtest
    isolinux.bin
    isolinux.cfg
    vesamenu.c32

ldlinux.sys
preseed/
README.diskdefines
syslinux/
    boot.cat
    memtest
    syslinux.bin
    syslinux.cfg
    vesamenu.c32


```This is similar to the problem I posted here:
[http://ubuntuforums.org/showthread.php?t=1956218](http://ubuntuforums.org/showthread.php?t=1956218)


When I choose the Icon that represents the st of Ubuntu, Grub2 starts. Grub2 is installed in that partition and presents a menu to choose among the different systems:  Linux with different kernels, memtest and MacOs in its 32 and 64 bit versions. But they don't work well. The MacOs options start the boot process in text mode  (the text flowing in the display) but stops suddenly, shortly after.
Can these symptoms be fixed?
Are these symptoms an indication that unless I change something I won't be able to boot a system located in the USB?

---

### Post by mhgsys on 2012-04-13
perhaps you could use some PLOP to get your usb booting, if I understand your question correctly, you have a problem getting the pc to boot from usb..

in that case read the plop instructions I posted here.. 
if you read the entire thread, you'll know everything about it
[http://ubuntuforums.org/showthread.php?t=1749260](http://ubuntuforums.org/showthread.php?t=1749260)

---

### Post by HotForLinux on 2012-04-13
> **mhgsys said:**
> perhaps you could use some PLOP to get your usb booting, if I understand your question correctly, you have a problem getting the pc to boot from usb..

in that case read the plop instructions I posted here.. 
if you read the entire thread, you'll know everything about it
[http://ubuntuforums.org/showthread.php?t=1749260](http://ubuntuforums.org/showthread.php?t=1749260)

This is an Apple.
Nobody gave me a solution on how to use plop for what it is supposed for 

(" that's what's plop is for... It's for machines without the usb booting option in BIOS.")

in a PC, in the thread I mentioned above.

---

### Post by mhgsys on 2012-04-13
erh , well... @ least I just told you..and pointed you to the info>
Don't know if it works for you on your apple though... but it's worth a shot isn't it?

or did I just completely misunderstood your above "comment"?

---

### Post by HotForLinux on 2012-04-13
> **mhgsys said:**
> erh , well... @ least I just told you..and pointed you to the info>
Don't know if it works for you on your apple though... but it's worth a shot isn't it?

or did I just completely misunderstood your above "comment"?


To the info? To what info? I don't see how plop can help in the case I mentioned when I started this tread, nor in the case I mentioned in the other thread. _Do you_?

---

### Post by mhgsys on 2012-04-13
I pointed you to the info on how to use PLOP and what PLOP is for ... 

Like I _asked _before; 
> 
perhaps you could use some PLOP to get your usb booting, if I understand your question correctly, you have a problem getting the pc to boot from usb..


You could use grub2 to boot plop, and boot (to) the usb with Plop.
You could point grub2 to boot plop, and have a different grub installed on the usb , pointing to whatever you want to boot on there...
Perhaps I'm not understanding your problem correctly...
Then again;
Your not being very clear imo, and I'm not really sure if I like the "tone" in your reply..

---

### Post by HotForLinux on 2012-04-13
As I said before, I know that grub and plop are excellent tools for booting systems, but I opened this thread because I still don't see _how_  these tools can help me in this case, nor in the similar case I mentioned in the thread I started before, for a similar problem.

[http://ubuntuforums.org/showthread.php?t=1956218](http://ubuntuforums.org/showthread.php?t=1956218)

In that thread another person also came sending me to study and learn about plop but giving no clue as to how it can solve the problem posed there. Moreover it seems, and he hasn't proved the contrary, that neither plop nor anything, can solve the problem. Have you checked that?

> **mhgsys said:**
> "Perhaps I'm not understanding your problem correctly...Maybe. I don't know. What is not clear?"

---

### Post by Lithaerien on 2012-04-14
In my experience you cannot boot a "Legacy" device from an external device (USB Stick/HDD) on an Apple computer, meaning no Linux or Windows on an external. You can boot another copy of Mac OS X from an external though.

You would have to somehow use an EFI version of GRUB, if that's even possible.

---

### Post by pindar on 2012-04-14
> **Lithaerien said:**
> In my experience you cannot boot a "Legacy" device from an external device (USB Stick/HDD) on an Apple computer, meaning no Linux or Windows on an external. You can boot another copy of Mac OS X from an external though.

You would have to somehow use an EFI version of GRUB, if that's even possible.
I boot linux from an external USB hard disk on my iMac, with grub-efi. Setting it up wasn't too hard. But since the OP finds it cumbersome to read documentation, I assume he must be looking for paid support, which I can't deliver.

---

### Post by HotForLinux on 2012-04-14
> **pindar said:**
> I boot linux from an external USB hard disk on my iMac, with grub-efi. Setting it up wasn't too hard. But since the OP finds it cumbersome to read documentation, I assume he must be looking for paid support, which I can't deliver.

Yes, pindar, often things are easy once you know how to. Nowadays, even a kid can solve third degree equations easily.
Would you please also explain us how did you set it up?

---

### Post by HotForLinux on 2012-04-15
Plop: [http://forum.plop.at/index.php/topic,1157.0.html](http://forum.plop.at/index.php/topic,1157.0.html)
--------------

If there is any chance to boot a linux system out of an USB drive in an Apple, I think that the first try should be to boot the system in the usb from instructing Grub2 to do it. If it works, then add the entry in grub's menu configuration.

How would this be done with Grub2  (with grub1 it didn't work in a compatible PC).

---

### Post by HotForLinux on 2012-04-17
I downloaded plop and booted plop from grub2, like this:

```
    set root=(hd0,3)
    linux16 /home/toni/Desktop/plpbt-5.0.14/plpbt.bin
```

 It looks like star wars but I can't boot the system in the USB and it gives me less info than grub2, which at least says that it doesn't know the geometry (C/H/S) to boot the USB. Actually I don't see what can you do with plop that you can't with grub2.

---

### Post by damodamo on 2012-05-26
(on my Macbook Air 3.1)
to make it simple
on your usb key
create 1 primary partition format it (FAT32 + bootable flag)
(this partition has to be the 1st one)
 use the "Startup *Disk Creator*" to built the usb key
reboot 
press Alt
you now can see another orange icon
select it
and you get into a grub2 menu
select the 1st entry
it will start the live ubuntu

N.B.: Refit isn't necessary to boot from a live USB

keep in mind that NOT ALL OF THE ISOs WILL BOOT!
for exemple 
       kubuntu 12.04 amd64 works
       kubuntu 12.04 amd64+mac doesn't work
       MultiSystem doesn't work
       ubuntu 12.04 amd64 not tested

to make to the +mac version bootable (on the macbook air)
 use the "Startup *Disk Creator*" to built the kubuntu 12.04 amd64+mac usb key
then copy the folders "efi" and "boot/grub" from kubuntu 12.04 amd64
and paste on the kubuntu 12.04 amd64+mac usb key
the efi folder and its content provide the orange icon mentioned above
the boot/grub folder and its content provide the grub folders for boot sequence

NB: on my PC the same usb key uses syslinux boot components (not grub2) and displays the typical Kubuntu blue screen 
        on my macbook it uses grub to display the grub menu 
Hope this helps

---

