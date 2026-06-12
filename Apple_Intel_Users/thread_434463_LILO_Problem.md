---
title: "LILO Problem"
date: 2007-05-06
forum: Apple Intel Users
---

### Post by The_Giver on 2007-05-06
I'm trying to install LILO since so many are talking about it but I haven't found a guide for moving to lilo from grub.


Here is the error I get when I try liloconfig:

Your /etc/fstab configuration file gives device                           &#9474;  
 &#9474; UUID=2ea2f11f-dfb5-47ed-9ebd-2aaf7051735e as the root filesystem device.  &#9474;  
 &#9474; This doesn't look to me like an "ordinary" block device. Either your      &#9474;  
 &#9474; fstab is broken and you should fix it, or you are using hardware (such    &#9474;  
 &#9474; as a RAID array) which this simple configuration program does not         &#9474;  
 &#9474; handle.


THIS IS FOR THE MACBOOK PRO C2D

I have OSX on the first partition, Linux on the second and Last is Windows Xp

---

### Post by Chrisj303 on 2007-05-06
Check this out : [http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu)

Just scroll down a little, to were it gives instructions on LILO.

You will need to completely remove GRUB first though. I did it via synaptic - search for GRUB then remove anything it shows as installed. I had to login as root (control-alt-delete) and delete the GRUB folder located in /boot, as well.

Once you deleted it - DO NOT REBOOT! Follow the guide i linked to.

Remember to sync your mbr/guid tables with the rEFIt partition tool when you do reboot.

I have exactly the same setup as you (but a macbook) - LILO is a much better choice, i'm sure it will make you happy!

---

### Post by The_Giver on 2007-05-06
Could someone else verify this  too please?

I heard I needed to use eLILO   also.... how exactly do I sync/ the mbr/guide tables since I didint do this before I don't know what that means.... Will I need to modify anything in the lilo config file?

MY specs:

- MacBook Pro C2D
- Feisty
- Triple Booting

---

### Post by Chrisj303 on 2007-05-06
> **The_Giver said:**
> Could someone else verify this  too please?

I heard I needed to use eLILO   also.... how exactly do I sync/ the mbr/guide tables since I didint do this before I don't know what that means.... Will I need to modify anything in the lilo config file?

MY specs:

- MacBook Pro C2D
- Feisty
- Triple Booting

No, you won't have to use eLILO - i don't know were youve read that, but for our setups this is not true.

I am running :
Macbook c2d
Triple Boot : OSX/UBUNTU (Feisty 7.04) / XP

I am using rEFIt 0.9 (the current version) and LILO.

When you boot, and you enter the rEFIt menu, the partition tool is found on the second row of options - it is clearly marked. Select it by pushing enter - it will then anaylize your tables, it they are out of sync it will let you know, and offer to sync them for you.

cheers,
chrisj303

---

### Post by The_Giver on 2007-05-06
Damn I'm already half way there but did you add the Edgy crap ?

---

### Post by The_Giver on 2007-05-06
I'm completely SCREWED all that work... went to waste... I did everything you said and now I get this error:


"GRUB GRUB Hard Disk Error" DAMN!!!!!!!!!!!!!!

I am sure I removed everything grub related.. DAMN IT... also  there is like a clone of the ubuntu now called partition 3... DAMN IT!!!!!!!!!!


I know i never should never have trusted that guide.

---

### Post by Chrisj303 on 2007-05-06
> **The_Giver said:**
> I'm completely SCREWED all that work... went to waste... I did everything you said and now I get this error:


"GRUB GRUB Hard Disk Error" DAMN!!!!!!!!!!!!!!

I am sure I removed everything grub related.. DAMN IT... also  there is like a clone of the ubuntu now called partition 3... DAMN IT!!!!!!!!!!


I know i never should never have trusted that guide.



That guide is great, i followed it completley to get my system up and running - you'll see it linked a lot regarding his subject.

When i installed feisty, unlike edgy, GRUB did not crash during the install.

So i did what i told you - deleted as much of it as i could via synaptic, then logged in as root and got rid of the GRUB folder found in /Boot.

You installed lilo, via the terminal, yes?

You configured the lilo.conf, as descibed in the guide ?

After this you updated LILO, by using : 'sudo lilo'   - in the terminal ? (again as described in the guide)?

The fact that you are getting a GRUB error indicates that you have not got rid of it completley - which is vital, as LILO will not work until it is completley gone.

I would not feed you, or anybody for that matter information that i have not had first hand experiance with.

---

### Post by The_Giver on 2007-05-06
It's okay.. I guess I'll just have to reinstall.

---

### Post by Chrisj303 on 2007-05-06
NO, you have a functioning ubuntu install - it is just your bootloader that is borked. You can restore GRUB from the live cd.

You can also 'chroot' into your ubuntu install from the LIVECD - to make changes to your current install. Boot from your CD, open a terminal and :

sudo su -
 mkdir /mnt/ubuntu
 mount /dev/sda3 /mnt/ubuntu
 mount -t proc none /mnt/ubuntu/proc
 mount -o bind /dev /mnt/ubuntu/dev
 chroot /mnt/ubuntu /bin/bash

I do this one line at a time. 

After this, you will be in a root terminal enviroment that is linked ("chrooted") to your current install. From here you can re-install GRUB.

To re-install GRUB from terminal, you will have search around  - it is not something i have done myself, as i don't use it. But i'm certain it will be easy.

---

### Post by Chrisj303 on 2007-05-06
> **The_Giver said:**
> Damn I'm already half way there but did you add the Edgy crap ?

What were you refering to?

---

### Post by The_Giver on 2007-05-06
I did everything in the guide except for the edgy stuff... also.... I deleted my boot/grub dir via "sudo rm -R "

maybe that was my mistake?

---

### Post by The_Giver on 2007-05-06
> **Chrisj303 said:**
> What were you refering to?


Edgy users need to use "sudo parted /dev/sda" instead of "sudo parted". This should be executed in a normal terminal

---

### Post by Chrisj303 on 2007-05-06
> **The_Giver said:**
> Edgy users need to use "sudo parted /dev/sda" instead of "sudo parted". This should be executed in a normal terminal

Yes, i followed the instructions for edgy users.

---

### Post by Chrisj303 on 2007-05-06
> **The_Giver said:**
> I did everything in the guide except for the edgy stuff... also.... I deleted my boot/grub dir via "sudo rm -R "

maybe that was my mistake?

This from the guide :

 apt-get install lilo lilo-doc linux-686-smp linux-restricted-modules-2.6.15-23-686 linux-kernel-headers

If you are using the CD version of edgy, you will need a network connection to install the above packages. Edgy users should do this in the chrooted terminal. UPDATE: Edgy users dont need to do this download. Follow this guide which is super easy and uses grub. [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) You will need to run instead of the above:

 apt-get update
 apt-get install lilo lilo-doc linux-686-smp linux-restricted-modules-686 linux-kernel-headers



So yes, i followed the bottom set of commands.

I removed the grub folder, located in /boot, by logging out (ctrl-alt-delete), then looging back in as root. Then i located the folder and trashed it.From here i installed and configured LILO as the guide says.

---

### Post by The_Giver on 2007-05-06
Hey I got my ubuntu back .. but grub doesnt give me that menu anymore... with the menu to select which OS i want to boot from.. someone mind posting the contents of their /boot/grub/menu.lst

---

### Post by The_Giver on 2007-05-06
I'll try and see how it goes again..

---

### Post by The_Giver on 2007-05-06
So when i am on step : 
parted
set 3
boot
on

I get "Unable to mount the volume 'EFI'

and the Macintosh HD pops up in the File browser

---

### Post by Chrisj303 on 2007-05-06
From the guide, directly below the part you are refering to :

Edgy users need to use "sudo parted /dev/sda" instead of "sudo parted"


Are you doing this?

I did:

sudo parted /dev/sda
set 3
boot on
on
quit

Then i did : sudo lilo    

My partitions are (in case your interested):

/dev/sda2 - mac osx
/dev/sda3 - ubuntu
/dev/sda4 - XP

---

### Post by The_Giver on 2007-05-06
Now, once I type "sudo lilo" i get "Warning: Partiton 3 on /dev/sda is not marked Active

---

### Post by The_Giver on 2007-05-06
Still it didnt work... oh well... I think i'll just stick to grub... 

There is something you forgot to tell me because i remove grub both via the command line and via the graphical interface

---

### Post by Chrisj303 on 2007-05-06
From the very bottom of the guide :

See the Talk page if you just get a blank screen when trying to boot Edgy. 


Which contains a link to this :
[http://wiki.onmac.net/index.php/Talk:Triple_Boot_via_BootCamp_Ubuntu](http://wiki.onmac.net/index.php/Talk:Triple_Boot_via_BootCamp_Ubuntu)

---

### Post by The_Giver on 2007-05-06
Wait a minute.. when you say "remove /boot" you dont mean rm -R /boot do you?

---

### Post by Chrisj303 on 2007-05-06
NO

I removed the GRUB folder from within the /boot directrey.

Please DO NOT REMOVE your /boot !

Like i said before, i removed all trace of GRUB from system, then installed and configured LILO.


This is a screenshot of my desktop, showing my /boot dir  - notice the GRUB folder, or anything to do with GRUB is not there. To remove the GRUB folder from /boot i had to login as root (ctrl-alt-delete).

[IMG]http://i178.photobucket.com/albums/w268/chrisj303/Screenshot-1.png[/IMG]


To the left is my LILO config file.

---

### Post by The_Giver on 2007-05-06
Hey maybe you missed this but did you get the two following errors:

** "Unable to mount the volume 'EFI' **(during the sudo parted section)

and 
[B][B]""Warning: Partiton 3 on /dev/sda is not marked Active" 
[/B][/B]right after typing in "sudo lilo"

---

### Post by Chrisj303 on 2007-05-06
> **The_Giver said:**
> Hey maybe you missed this but did you get the two following errors:

** "Unable to mount the volume 'EFI' **(during the sudo parted section)

and 
[B][B]""Warning: Partiton 3 on /dev/sda is not marked Active" 
[/B][/B]right after typing in "sudo lilo"

I DID NOT get the first error

I DID get the second error - it made no difference to my setup, i'm triplebooting fine.

Have you got rid of that GRUB folder? Have you followed ALL the steps regarding LILO, in that guide i linked? 

If so you *should* be triple booting.

If you are thrown back into an error like before, read the guide i linked last : [http://wiki.onmac.net/index.php/Talk:Triple_Boot_via_BootCamp_Ubuntu](http://wiki.onmac.net/index.php/Talk:Triple_Boot_via_BootCamp_Ubuntu)

 - This is perfect for that situation.

---

