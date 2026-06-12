---
title: "How do you install Ubuntu on a Mac?"
date: 2006-09-02
forum: Apple PPC Users
---

### Post by private_idaho on 2006-09-02
Hi
I've downloaded the Ubuntu installer and I have a clean hard drive to install it onto. However, there is nothing in the Ubuntu image that looks like an installer or responds like an installer program, and I have no idea what to do with it now.

I've searched the Ubuntu site and I can't find any installation instructions. How can this be? Aren't installation instructions normally the first thing you look at when you install new software? 

How do you install Linux if you're not running Linux? Do I need to reinitialize my hard drive, and if so, to what? What file do I click on to install the software? What happens after I install it? Do I relaunch my machine in Linux? Will I ever be able to boot off Mac OSX again (on my other hard drive)? Can I choose my start drive, for example, as I can now in Mac OS X?  

These are really basic questions, and I don't see them answered. This web site looks really cool and user friendly until I actually look for beginner's information...

Here are my specs: I have a Mac G4 desktop ("Digital Audio," circa 2001) running OS X 10.3.9. 933 mhz/1.2 gigs of RAM.

I have a new serial ATA hard drive, over 150 gigs, ready to go with a Linux install (preferably partitioned so I can use half of it for storage of OS X files)...if only I knew how to get started. The supplied icons in the installer, when clicked on, open up text files. It's daunting enough to try something this new on my trusty machine. Clear instructions are essential! Where are they?

Thanks for your help. If clear instructions live on the web somewhere for us newbies, please point me there.

---

### Post by APU on 2006-09-02
Basically it is the same as for MacOS - Just boot from the Install CD. To boot from a CD you have to press and hold the "C" button on your keyboard when you start the computer.

That´s it

---

### Post by pomfrey_ml on 2006-09-02
I dont know..

---

### Post by jhemono on 2006-09-02
Hello,
First, note **I'm not a mac-user** so i'm only giving you some tips.
Second, I'm not speaking good english ... 
So, First you won't install ubuntu from within Mac os x by an installer : You install ubuntu by booting on the ubuntu live cd, this will boot an ubuntu sytem from the cd where you can try ubuntu then you can install it by launching "install" on the desktop.
I think you didn't search the wiki, I found it :
[https://wiki.ubuntu.com/Installation/PowerPC](https://wiki.ubuntu.com/Installation/PowerPC)
This page describe the installation of an older version of ubuntu, But I read it and it looks like there is no issue in the installation of ubuntu on mac powerpc "newWorld" (as seem to be your mac) :
You burn the ubuntu **desktop ppc** cd using the disk utility, you insert it in your drive then you reboot.
At rebooting hold the "c" to boot on the cd, You reach a screen where you can select language (english set by default) your keyboard by pressing function keys as described at the bottom of the screen. Then you're done select "start ubuntu live cd" (something like this) and hit enter : Ubuntu starts and you reach the desktop. Here you can try ubuntu and see if ubuntu is working well on your mac. Then Launch "Install" on the desktop and do what's said. At partitionning select your second hard disk then select manually partitionning. You reach partionning utility. Here partion your disk with swap and ubuntu partition (as described in pc tutorials) and keep the free space you want for your your mac os x partition (you will make it with the disk utility of mac os X). When you're done Hit Ok and continue.
In fact the problem is in the boot manager :
If you have the choise install it on the second drive : I think (i never used a mac) that the real boot manager will detect the ubuntu boot loader so at the real boot manager, you will select the second drive and after you will select the ubuntu system in the ubuntu boot manager. So you're mac os x system won't be bothered by ubuntu. If you don't have the choise, i don't know whever ubuntu will install the boot manager on your first or second hard disk in both cases id don't think you will be unable to boot mac os x.
Then the installation process begin. When it's done reboot and see what's happening.

But I think you **should** wait answer from mac-users and, why not, ask your question on a mac specific forum too. And don't forgot to search using a search engine : all the ubuntu help isn't only on the ubuntu website.

---

### Post by hajk on 2006-09-02
I think the OP might also benefit from checking the following link: [http://www.ubuntuforums.org/showthread.php?t=63315]("http://www.ubuntuforums.org/showthread.php?t=63315")

---

