---
title: "Where should I install Grub?"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by nick24 on 2007-02-27
Here I go again :)

Okay I installed Ubuntu 6.10 on an internal secondary HD. Sometime during installation I was given a choice where to install Grub (default was hd0). I didnt want to install GRUB in the MBR of my first HD. So I typed hd1 instead. Installation went smoothly and I started my PC only to find out it wont boot Ubuntu. What am I doing wrong here? I did this with Mandriva before and everything worked. Is it not possible with Ubuntu? Please help. Thanking you ii advance.

---

### Post by skyhopper88 on 2007-02-27
Is the Secondary HD set to boot first?

---

### Post by nick24 on 2007-02-27
Currently it is set as secondary.

---

### Post by rusty4r on 2007-02-27
If you want to dual boot then grub will be the menu or device that allows you to choose which operating system to boot to. In that case I think grub will have to be installed in the mbr of hda. I assume you have Windows on hda?

---

### Post by nick24 on 2007-02-27
Thats correct Windows is installed in /hda. As we speak I am ready to install Ubuntu again, still want to install GRUB in my second HD not in the MBR of hda. I did this with Mandriva with out any problem. To give you guys a better picture I am pasting the whole screen and as you can see it the default is (hd0). During Mandriva installation I just chose hd1 and viola! it was working. Please help anybody. Thank you very much 

Language: English
 Keyboard layout: U.S. English - Dvorak
 Name: 
 Login name: 
 Location: America/New_York
 
[SIZE="2"][COLOR="Red"]GRUB will be installed to (hd0)
[/COLOR][/SIZE]

If you continue, the changes listed below will be written to the disks.
Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.

The partition tables of the following devices are changed:
 SCSI3 (0,0,0) (sdb)

The following partitions are going to be formatted:
 partition #1 of SCSI3 (0,0,0) (sdb) as ext3
 partition #5 of SCSI3 (0,0,0) (sdb) as swap

---

### Post by Drakkor on 2007-02-27
I have a dual boot on 2 drives......hda is XP,.....hdb is Edgy !
Edit: If you put grub on your second hdd, you will have to boot to the 
bios everytime,and select which drive to boot, kind of a pain !
I put grub on the mbr, and it allows me to select wihich OS at boot time.

---

### Post by rusty4r on 2007-02-27
OK the computer is set to boot to the primary drive so there must be something on the primary drive to reference the secondary drive or you will never have the option to boot the secondary drive. Windows alone will not do this. It can't recognize Linux. That's why I let Linux install grub to the mbr of the primary. Because Grub will recognize both Linux and Windows and give you the option of booting either one. If you don''t change what you already have on the primary partition then you will not be able to choose your boot options because windows will continue to boot as always.

Try this link I think it my help you
[http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/")

---

### Post by nick24 on 2007-02-27
rusty4r thank you for your instant reply I really appreciate it.

Yes I know hd0 is listed as primary. But then again I can always change its priority in BIOS, as I was doing with XP and Mandriva. When I want to boot to Mandriva I just go to BIOS and set hd1 as the primary disk and that solves the problem. When I need to boot in to Windows I simply change the priority and boot Windows. Its kindda annoying sometimes but it works. I guess Ubuntu does not support that or I something. Thanks again.

---

### Post by nick24 on 2007-02-27
> **Drakkor said:**
> I have a dual boot on 2 drives......hda is XP,.....hdb is Edgy !
Edit: If you put grub on your second hdd, you will have to boot to the 
bios everytime,and select which drive to boot, kind of a pain !
I put grub on the mbr, and it allows me to select wihich OS at boot time.

Thats exactly what I am trying to do despite the pain! :)  Can you shade some light on how you did that please ?

---

### Post by skyhopper88 on 2007-02-27
You shouldn't have to change the bios every time. I set my secondary that has grub on it as the first boot device and I can then boot to Ubuntu on the secondary or Windows on my primary from grub.

---

### Post by nick24 on 2007-02-27
> **skyhopper88 said:**
> You shouldn't have to change the bios every time. I set my secondary that has grub on it as the first boot device and I can then boot to Ubuntu on the secondary or Windows on my primary from grub.

Thats a good Idea Skyhopper88 and I will do that when I successfully install GRUB in the secondary HD. My question is how do I install GRUB in the secondary HD - NOT ON THE MBR? You see what am saying? I appreciate your reply and I will wait for more help before I go ahead and install it on the MBR.

---

### Post by rusty4r on 2007-02-28
I think that what your going to have to do is run the live install cd again but choose to update instead of install and when the grub option comes up it should allow you to install it to the secondary hard drive in it's boot sector. I tried to use Super Grub once before for a situation sorta like this but if there isn't any existing grub there it won't work so I used the live cd.

---

### Post by louieb on 2007-02-28
> **nick24 said:**
> So I typed hd1 instead... I did this with Mandriva before and everything worked. Is it not possible with Ubuntu? Please help. Thanking you ii advance.
Mandriva must be magical. I don't see how Grub  install on the 2nd drive would load if the 1st  drive is the boot drive in BIOS.  

As far a I know you have 3 options.

1. If your BIOS allows it boot the second drive first as skyhopper88 did.
2. See the reinstall grub link in my signature and Put GRUB in the MBR of the 1st drive. or try the Super Grub disk.   
3. Or if your brave and have lots of time get the windows boot loader to boot Ubuntu.

Lots of good info in the Dual Boot link in my signature.

---

### Post by confused57 on 2007-02-28
The OP found a solution in this thread:
[http://www.ubuntuforums.org/showthread.php?t=372550](http://www.ubuntuforums.org/showthread.php?t=372550)

---

### Post by rusty4r on 2007-03-01
> **confused57 said:**
> The OP found a solution in this thread:
[http://www.ubuntuforums.org/showthread.php?t=372550](http://www.ubuntuforums.org/showthread.php?t=372550)

Now I'm confused. Two threads same question same day

---

### Post by confused57 on 2007-03-01
> **rusty4r said:**
> Now I'm confused. Two threads same question same day
Please, allow me to confuse you even more...make that 3 threads:
[http://www.ubuntuforums.org/showthread.php?t=372121](http://www.ubuntuforums.org/showthread.php?t=372121)

I'm sure the OP realizes now that one thread is sufficient for a question...unless there's no answer or solution within a "reasonable" time period...

With my 20/20 "hindsight", I should have notified the moderators to merge the 3 threads...lesson learned, no harm done.

---

### Post by rusty4r on 2007-03-01
> Please, allow me to confuse you even more...make that 3 threads:
[http://www.ubuntuforums.org/showthread.php?t=372121](http://www.ubuntuforums.org/showthread.php?t=372121)


Sorry Confused57, But I'm not confused anymore, now I see the light.

Thank you

---

