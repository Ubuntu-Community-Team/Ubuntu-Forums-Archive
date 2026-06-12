---
title: "EFI and Grub"
date: 2012-05-07
forum: Apple Hardware Users
---

### Post by xxi on 2012-05-07
I debated which sub forum would be to best to make this post in, and considering this is most general questions about setting up a full EFI grub system, I decided that it would be best in the general help section rather then the apple section (even though the system I'm using is a macbook pro). I apologies if i did not place this in the right section. 

I have been having difficulties properly installing and using grub on my machine. 

First the details of my setup and what I think I should be able to do:
I am using a MacBookPro8,1 which contains EFI 2.7 firmware (see macbook pro 13in early 2011 [http://support.apple.com/kb/HT1237?viewlocale=en_US&locale=en_US](http://support.apple.com/kb/HT1237?viewlocale=en_US&locale=en_US))
I am trying to set up a multi boot environment that uses only grub to select between linux, mac os 10.7, and windows 7.
I wish to make my setup a full UEFI boot which should be ok considering my systems firmware version.
I have properly setup an ESP and wish to use it to hold grub and any components grub requires to boot. 
At the moment I have Ubuntu installed on my hard drive in its own partition, but I broke it because I removed the hybrid protective master boot record (again because I wish to use a full EFI boot).

Here is roughly the steps I have used to try and install grub. I start by booting into an Ubuntu live CD, I then mount my Ubuntu partition to /mnt/ubuntu. With my linux system mounted, I mount the ESP to /mnt/ubuntu/boot/efi and mount the special file systems (proc, dev, sys). Once I have finished mounting the required parts of my system I chroot to /mnt/ubuntu

(Please excuse this if it is wrong i'm doing this from memory)
Now this is where I am confused. As I understand, grub-install cannot be used to install an efi version of grub so I use:
grub-mkimage -d /usr/local/lib/grub/x86_64 -p /boot/efi/efi/grub -o /boot/efi/efi/grub/grub.efi -O x86_64 `cat <file that contains a list of all the modules with out .mod>`

After running the grub-mkimage command I have an efi binary in my ESP that I am able to boot. When I boot into grub I am printed with a grub command prompt and I am able to load a grub config file (I used grub-mkconfig to make this file and it seems to have detected all of my operating systems but I still am not able to use it to boot any of my systems, also I am familiar with bash scripting so I expect to either modify this file at some point or make my own config) 
At the grub command prompt I am able to try some other commands but again I am unable to boot any of my operating systems.

I don't really know very much about grub (only what I have read in the grub manual or online) and did not ever install grub legacy by myself. I believe the following are my most direct questions (but i would appreciate any extra help to kinda give me better footing with grub and the rest of this):

-Where can I learn about the grub modules that I can load and figure out which ones I need?

-What is the format for loading grub modules? (I noticed the folder I point to in the mkimage command has the module files that end in (dot)mod, can i use a command like `ls *.mod` to load all the modules or does the .mod need to be removed from the name?)

-Are there more modules that I may need to load that are not in the grub folder? (are these modules like kernel modules? if so, do i need to load some specific kernel modules?)

-Once I have grub booting, how do i boot the operating system I wish to boot? Is there more information about the required commands? What steps do I need to use to get my mac system to boot? Is there a document, site, etc that I could use to get a better understanding of booting systems from grub? (again I read the manual and i was confused because the parts about booting were either incomplete or over my head)

Is anything in grub like grub legacy? I know there is a lot of information about the previous version of grub, would it be worth my time to read any of it or are the two too different?

Thanks for your time and I'm sorry if this post is a little confusing, if there is anything unclear or something more I can add to help you guys help me please let me know.

---

### Post by xxi on 2012-05-08
Also would any of you have any other suggestions of where to post my question? I have made this post on the grub help mailing list, as well this form and the linux.org form and haven't gotten much feed back. I don't mind asking someone else if any of you think it might help

---

### Post by oldfred on 2012-05-08
I know nothing about Macs, and little about efi, although I have tried to help some users with efi installs.

It is my understanding that Apple's efi is not the full implementation of the current standard and makes it difficult or impossible to use directly to efi boot.

If you want, I can move your thread to the Apple sub-forum as they may know more.

Some general efi references:

[https://help.ubuntu.com/community/UEFIBooting#Chainloading%20Windows%20x86_64%20UEFI-GPT]("https://help.ubuntu.com/community/UEFIBooting#Chainloading%20Windows%20x86_64%20UEFI-GPT")
How boot a (U)EFI system natively (without BIOS CSM) using GRUB 2
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
Grub recompile not required.

[https://bbs.archlinux.org/viewtopic.php?pid=910369#p910369](https://bbs.archlinux.org/viewtopic.php?pid=910369#p910369)
[https://wiki.archlinux.org/index.php/GRUB2](https://wiki.archlinux.org/index.php/GRUB2)
[https://github.com/skodabenz/Misc_Linux_Shell_scripts/blob/master/grub2/grub2_efi.sh](https://github.com/skodabenz/Misc_Linux_Shell_scripts/blob/master/grub2/grub2_efi.sh)
EFI System Partition Subdirectory Registry
[http://www.uefi.org/specs/esp_registry](http://www.uefi.org/specs/esp_registry)
All linux distro installers (Ubuntu included) assume EFISYS partition to be mounted at /boot/efi.

EFI boot loader information - srs5694 & skodabenz
[http://ubuntuforums.org/showthread.php?t=1849160](http://ubuntuforums.org/showthread.php?t=1849160)
[http://www.rodsbooks.com/bios2uefi/](http://www.rodsbooks.com/bios2uefi/)
[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

There was a post by this site on testing where he said he uses Ubuntu in Virtual install on his Mac as then he gets longer battery live and a direct boot.
[http://www.phoronix.com/scan.php?page=home](http://www.phoronix.com/scan.php?page=home)

---

### Post by xxi on 2012-05-09
Thanks oldfred for your replay, I will look through your links and see if there is any information i may have missed. Also I would like to take you up on the offer to move my post, maybe I can find some more specific information in a new sub forum. Thanks again for you time!

---

### Post by oldfred on 2012-05-09
Moved to Apple forum.

---

### Post by xxi on 2012-05-11
Hey, since my post was moved I thought I would post in it one more time and see if I couldn't get any help.

---

