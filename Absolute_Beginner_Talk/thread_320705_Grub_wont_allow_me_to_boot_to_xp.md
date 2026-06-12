---
title: "Grub wont allow me to boot to xp"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by sean150 on 2006-12-17
Ok here is the problem. I have one raid0 setup that xp is installed on and a sata250gig drive that I have ubuntu installed to.

When I boot up GRUB cant recognize XP so it automatically boots to Ubuntu. 

Does anyone know how to fix this problem?

---

### Post by louieb on 2006-12-17
When the machine first boots and you see the screen say grub loading press escape. That should get you to the grub menu. 
If you get to the menu you should see and XP option.
Press down arrow till XP option is highlighted.
Press enter and let me know what it does.

---

### Post by xyz on 2006-12-17
Hi,
If when you boot up GRUB can't recognize XP,then do this in a terminal:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
gksudo gedit /boot/grub/menu.lst

```
The first command line "sudo cp..." makes a copy of /boot/grub/menu.lst so that, in case of pbm, you can restore it safely to the way it was before.

The second command line will open: /boot/grub/menu.lst which you'll want to edit by adding at bottom: (Save the edited file)
> title		Microsoft Windows
root		(hd0,0)
savedefault
makeactive
chainloader	+1
Adding this to this file will allow you to choose between booting Windows or Ubuntu.

---

### Post by sean150 on 2006-12-17
Well I rebooted to try and see if xyz's idea would work. But now my desktop is currently bricked because I get this error when booting. 

 > GRUB Loading Stage1.5.


GRUB Loading, please wait...
Error 21


I had to get out my laptop to post this message. I would like to resolve this issue quickly as I need my desktop back.

---

### Post by dbbolton on 2006-12-17
is windows not on hda1 ?

---

### Post by sean150 on 2006-12-17
well Ill tell you what I know based on m current understanding. I seem to remember it showing my two raid drives as hd0 and hd1, ubuntu's hardware manager shows the second drive as recognizing an NTFS partition so I'm going to guess and say that its on hd1. During the Ubuntu installing process it choose to install GRUB on hd0.

---

### Post by OMRebel on 2006-12-17
So now you're having problems loading either Ubuntu and XP?  Whenever Grub loads up, you can edit it on the fly to play around with your drive settings.  I have 2 SATA, with Ubuntu on one and XP on another.  On the line that has root for XP, if you have (hd0,0), try changing it to hd1,0 and see if that works, and vice versa with your Ubuntu listings in Grub.

---

### Post by sean150 on 2006-12-17
Well, windows is currently installed on two sata drives in a raid0 I have a 3rd drive which is by itself which ubuntu is installed on. When Grub begins to load it gives me that error, I cannot access windows or ubuntu. The live cd still works. I'm unsure how to edit grubs list, can I do it from the live cd?

---

### Post by sean150 on 2006-12-17
Iv been reading on other forums that Error 21 is caused because grub cant find the proper HD. All my bios settings seem to be correct, windows recognized all 3 drives before I installed ubuntu. My theory is that it cant recognize my raid.

---

### Post by Littleweseth on 2006-12-18
Suggestion : Use the Super GRUB disk to bootstrap your computer to usable state so you can restore menu.lst or whatever else needs doing.

[http://adrian15.raulete.net/grub/](http://adrian15.raulete.net/grub/)

It's a small (couple of meg) .iso, burn and boot. Helped me boot my computer after a windows reinstall helpfully nuked my bootloader.

---

### Post by superoo on 2006-12-18
Hey, i'm not sure if this helps but if you just want to get windows back then reinstall Ubuntu, you can boot from a windows boot floppy and run
fdisk /mbr
you will not be able to run Ubuntu after this as it will erase GRUB from your master boot record but windows should work fine...

---

### Post by Littleweseth on 2006-12-18
the Super GRUB Disk works very well for restoring GRUB in case of fsckup :) IIRC it actually has a wizard intended to restore GRUB in the case of MBR corruption, menu.lst b0rkups, and kittens clogged in the pipes.

fdisk /mbr is a much more blunt instrument in comparison :)

---

### Post by sean150 on 2006-12-18
Super GRUB boot disk is allowing me to boot to windows which i'm very happy about.:) 
But when I ask it to fix the linux/gnu it goes through its processes and says that it was unsuccessful.

Windows was installed first then ubuntu. I think my raid has something to do with. last week I broke my raid and I was able to install and dual boothat winh without any trouble. I now want to get my raid to have xp and the second drive to have ubuntu. My friend has nearly the same hardware that I do and he gets the same problem with Error 21.

UPDATE: I have discovered that Ubuntu is installed on HD2. When I install ubuntu and it gives me the option of where to install grub(default hd0) should I change it to hd2 to match where ubuntu is? If you wish to chat with me in person my aim name is swgamerx140.

---

### Post by Littleweseth on 2006-12-18
IANAE, but the bootloader should still live on hd0. The bootloader is just the first thing the computer looks for after it POSTS; the bootloader should, if operating correctly, then point to an operating system somewhere else.

By the way, you can make your linux filesystems visible from Windows by installing the Ext2IFS filesystem driver - that way, you can mess around with things on your linux partition from windows, which is what I had to do a few times to solve my own GRUB problems (hint : it's a Really Good Idea to keep a backup of menu.lst before you go and delete half of it by accident :p)

Not directly helpful, but maybe useful (if not now, definitely in the future :) )

---

### Post by sean150 on 2006-12-18
I'm not sure how I would edit that grub boot list though. If it was only a problem of it not finding windows i'm sure the solution would be the change the list. but Grub cant even find the drive that ubuntu is on. I'm afraid I may just have to wait for Feisty Fawn to come out in march and hope that they have this problem fixed in that release. 

If I decide to give up is there a way for me to totally get grub off my machine. Im guessing that the boot loader cd you told me about can restore my windows booter.

---

### Post by Littleweseth on 2006-12-18
Reality check : when the computer POSTS, does it list that 250gb drive as present? You've dismantled your computer and checked for bad contacts/loose plugs?

Might be worth checking to see if the drive 'really isn't there'..... aren't hardware issues masquerading as software issues fun? :)

---

