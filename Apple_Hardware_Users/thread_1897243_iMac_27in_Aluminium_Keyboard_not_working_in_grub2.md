---
title: "iMac 27in Aluminium Keyboard not working in grub2"
date: 2011-12-18
forum: Apple Hardware Users
---

### Post by phillat5dock on 2011-12-18
I have successfully set up my 3.6GHz dual core i5 iMac with Lion, Windows 7 and Ubuntu 11.10. All 64 bit. I have a 2TB hdd and 12 GB ram. The hdd is partitioned as a "hybrid" gpt and mbr. Windows 7 has to have the MBR to boot. (Boot Camp etc). 

I must say that I am VERY very impressed with Ubuntu. I have gradually been solving various issues but one issue is just out of my grasp.

When Ubuntu 11.10 is up a running my wired USB aluminium keyboard works great. All the Apple buttons do as they are supposed to ... volume up and down, eject CD, brightness control, number pad and so on.

However, often when booting through** grub2,** the_ keyboard does not work._ Other times it does work.

The only way I have been able to get Windows 7 to boot reliably is to use grub2 as the boot loader, and using the cursor keys to arrow down to Windows 7 loader in the grub menu.

 I have been through all the steps to reinstate Windows after installing Ubuntu... Booting into Windows 7 DVD , executing Bootrec.exe/FixMbr, which then hoses grub so I have to use a LiveCD or Disk-Repair or Super-Grub to get Grub to boot Ubuntu (which then wipes out the Windows boot!).

The problem is this Apple Keyboard not working in grub sometimes. I then have to reboot with a PC keyboard (without the Apple key functions like CD eject etc) just to be able to boot Windows.

I just can't work out why, when i do update-grub from within Linux the drivers for the keyboard don't automagically get added to the grub boot images.

When grub boots Ubuntu (after it times out!) the keyboard works perfectly.

Any help would be especially appreciated.

---

### Post by Buntumatic on 2011-12-18
phillat5dock,

I see you are slightly confused. Grub is no part of Linux, it is a bootloader, which by definition does its job before **any OS** loads. Whether your keyboard functions or not is between your BIOS and Grub.

---

### Post by phillat5dock on 2011-12-19
> **Buntumatic said:**
> phillat5dock,

I see you are slightly confused. Grub is no part of Linux, it is a bootloader, which by definition does its job before **any OS** loads. Whether your keyboard functions or not is between your BIOS and Grub.

Yep. I realise that. 

Macs do not have a bios. That is the problem. Ubuntu Oneric seems to have all the drivers required to run perfectly on my iMac.
But grub is needed first, in order to load Ubuntu. The trouble is I can't work out how to get grub to load the keyboard drivers, or whatever they are, so that I can move the curser up or down the grub menu.

I don't see this as a bug.
Just my noob lack of knowledge. I am climbing up a steep learning curve here.

---

### Post by phillat5dock on 2011-12-27
> **phillat5dock said:**
> Yep. I realise that. 

Macs do not have a bios. That is the problem. Ubuntu Oneric seems to have all the drivers required to run perfectly on my iMac.
But grub is needed first, in order to load Ubuntu. The trouble is I can't work out how to get grub to load the keyboard drivers, or whatever they are, so that I can move the curser up or down the grub menu.

I don't see this as a bug.
Just my noob lack of knowledge. I am climbing up a steep learning curve here.

UPDATE 28/12/2012
I added the following to grub.
insmod ohci 
insmod usb_keyboard

The Aluminiun keyboard works fine in the boot selection screen in Grub now.

---

### Post by badouwes on 2011-12-29
I have a 17" White iMac, and the same problem.

Where exactly did you add those two ' insmod'  commands? From what I understand, adding these to the grub.cfg file, will have them overwritten and still my question is: where in the file exactly?

Thanks!

---

### Post by phillat5dock on 2012-01-01
> **badouwes said:**
> I have a 17" White iMac, and the same problem.

Where exactly did you add those two ' insmod'  commands? From what I understand, adding these to the grub.cfg file, will have them overwritten and still my question is: where in the file exactly?

Thanks!

I think I added them to /etc/default/grub. I probably used Grub Customizer.
It seems that iMacs use the ohci protocol. Well that is what I thought after lots of research.

The peculiar thing is that some time after I modifed default/grub with those lines I trashed my system and had to reinstall Ubuntu.
After the reinstall the keyboard works perfectly. So it is a complete mystery what I actually did. I doubt now whether adding those lines actually did what I thought.

It is a steepish learning curve, but you know what? The more I learn tweaking Ubuntu the more awe inspired I am about how well Mac OS X works. I keep asking myself " If this works this way in Linux, how does it work in Mac OS X?" It is like I am learning more about Mac OS X by delving into GNU/Linux.

---

