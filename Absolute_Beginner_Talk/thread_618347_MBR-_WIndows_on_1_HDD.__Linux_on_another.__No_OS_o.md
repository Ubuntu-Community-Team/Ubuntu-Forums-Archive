---
title: "MBR- WIndows on 1 HDD.  Linux on another.  No OS option on bootup"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by Tdukes on 2007-11-20
How do I do this?

I installed Ubuntu 710 on a seperate SATA HDD.  So I have windows on HDD1, and Linux on HDD 3

I am not getting an OS selection screen unless I pull up a boot screen by hitting F8 when my Bios is loading up.  after that loads I have to select the Linux HDD and then select the Linux OS from the list.  THis is a pain in the you know what.

I just want to turn the computer on and be given "either or" option.

Thanks for any input

---

### Post by Duck2006 on 2007-11-20
You will have to install grub to the mbr of the first hard drive.

[http://users.bigpond.net.au/hermanzone/p15.ht](http://users.bigpond.net.au/hermanzone/p15.ht)

---

### Post by Tdukes on 2007-11-20
How exactly do I do that?

---

### Post by ukripper on 2007-11-20
Follow this tutorial [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Tdukes on 2007-11-20
> **ukripper said:**
> Follow this tutorial [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I followed the TUTORIAL but I really dont think it directly applies to my problem.

Its wierd, I am given the option of windows and linux.....but if I select linux, it pulls up the loader screen but is searching for the CD Rom to install ubuntu.

I need to go into windows and edit the MBR to add the Linux HDD but I dont know how to do it

---

### Post by happysmileman on 2007-11-20
> **Tdukes said:**
> I need to go into windows and edit the MBR to add the Linux HDD but I dont know how to do it

You can install GRUB on a hard-drive with Windows only, and it's usually easier than changing the MBR settings AFAIK.

It will allow you to chose either Windows or Linux, and will boot from the correct hard-drive either way

---

### Post by Tdukes on 2007-11-20
> **happysmileman said:**
> You can install GRUB on a hard-drive with Windows only, and it's usually easier than changing the MBR settings AFAIK.

It will allow you to chose either Windows or Linux, and will boot from the correct hard-drive either way

I just need to know how to do this, thats all

---

### Post by happysmileman on 2007-11-20
> **Tdukes said:**
> I just need to know how to do this, thats all

Ah sorry, misunderstood, I think it's ```
sudo grub-install /dev/hda
``` replacing "/dev/hda" with whatever your Windows drive is.

---

### Post by Tdukes on 2007-11-20
> **happysmileman said:**
> Ah sorry, misunderstood, I think it's ```
sudo grub-install /dev/hda
``` replacing "/dev/hda" with whatever your Windows drive is.

Does sudo grub-install /dev/sdb1 sound right?

heres a screeny of my Windows HDD

[IMG]http://img.photobucket.com/albums/v618/Tommydukes/Screenshot--dev-sdb-GParted.png[/IMG]

---

### Post by Tdukes on 2007-11-20
ok, tried it and am gonna reboot....wish me luck

dukes@dukes-desktop:~$ sudo grub-install /dev/sdb1
Searching for GRUB installation directory ... found: /boot/grub
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc

---

### Post by Tdukes on 2007-11-20
DID NOT WORK.

Now I cant even open windows.  I cant fix the MBR because I cant get to a commannd prompt.  It just sits there, frozen, and says GRUB

SHITTY

---

### Post by Duck2006 on 2007-11-20
Try using the super grub disk.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by Tdukes on 2007-11-20
> **Duck2006 said:**
> Try using the super grub disk.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

I cant even get my windows cd to open up so I can Fix the MBR on my windows drive.  what the hell.

---

### Post by Duck2006 on 2007-11-20
From the ubuntu live cd can you boot from the first hard disk on startup?
That should get you into windoze.

---

### Post by Tdukes on 2007-11-20
> **Duck2006 said:**
> From the ubuntu live cd can you boot from the first hard disk on startup?
That should get you into windoze.

Its not even searching for the CD.  just stalls at grub, I can ctrl alt del but thats it

this is wierd

---

### Post by Duck2006 on 2007-11-20
> **Tdukes said:**
> Its not even searching for the CD.  just stalls at grub, I can ctrl alt del but thats it

this is wierd

Is this the live CD?

---

### Post by Tdukes on 2007-11-20
> **Duck2006 said:**
> Is this the live CD?

yea,  I am setting bios to read the cd rom first but it isnt seeing the Live CD or the Windows  CD either.

Looks like I am gonna have to do a complete system wipe even though I never wanted to

---

### Post by Tdukes on 2007-11-20
any way I can mess with windows MBR from linux?????

---

### Post by Duck2006 on 2007-11-20
This may help with your clean install.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Duck2006 on 2007-11-20
> **Tdukes said:**
> any way I can mess with windows MBR from linux?????

Not sure if that can be done. The only way i know is from a live CD.

---

### Post by ukripper on 2007-11-21
in this case I 'd personally rename menu.lst to something else using Live cd and then reboot and use XP cd to  fix my MBR as i showed you tutorial before and then i boot into live cd again after I have fixed my MBR. Then rename back my menu.lst and then reboot to acces my installtion.

---

### Post by Bartender on 2007-11-21
Another idea - you've got nothing to lose now anyway.

Disconnect the Windows HDD.
Re-install Ubuntu to the Linux drive.  Let Ubuntu auto-install to the entire drive.  With SATA, you may have to jack the Linux HDD into the #1 SATA port on the motherboard.  Not sure about that.
When you've got that working, plug in your Windows drive and see if you can at least rescue your personal data to a thumb drive or DVD's. 

Also - wait, let me think about this - try disconnecting the Linux HDD.  If you have or can borrow a genuine Windows CD of the same vintage as what's on your PC, find some directions online for fixing the MBR from the Recovery Console (I've done it a couple of times so it's not that hard), boot from the CD and fix MBR.  You should be able to get Windows back.  I don't think it's been erased.  

Don't panic.  

If you get Windows back and decide to try this Linux thing again, make sure that Ubuntu installs GRUB to the correct HDD.  If you use a LiveCD, click on the little tiny "Advanced" button at the last step of the installation routine.  That's where you find out where GRUB is going to install.  If you want the typical GRUB window asking which OS to start up, GRUB has to be installed to hd0.  Assuming of course that Windows is on the first HDD!   

I think they should make that GRUB step clearer :(

---

