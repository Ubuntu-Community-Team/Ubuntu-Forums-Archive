---
title: "Just loaded ubuntu &amp; need help already!"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by mikkwan on 2007-01-22
Hi 

Only just found out about Linux the other day, uploaded the install Ubuntu CD last night, installed the applications this afternoon.  How do I get access to more applications?  	:confused: 

I have installed the following:

Mozilla Firefox
Mozilla Thunderbird
Abiword
Gaim
Gimp

Is Ubuntu desktop just supposed to load up when I install the ubuntu CD? :confused: 

Am I supposed to be able to use OpenOffice.org 2?  :confused: 

I appologise in advance if these questions are a bit basic but I am struggling at the moment!](*,)

---

### Post by Hagar Delest on 2007-01-22
Hi,

You have to install new applications with the package manager Synaptic (in menu System>Administration). Look for the OpenOffice.org package, check it for install and apply.

---

### Post by mikewhatever on 2007-01-22
Sorry, double post.

---

### Post by housam on 2007-01-22
You need to install ubuntu to get your internet connection activated. then you can get more applications through synaptic. system>>admin. >> synaptic.
Also you can get more bu downloading and installing Automatix2 ( installer with many programs inside) using the link [http://www.getautomatix.com/]("http://www.getautomatix.com/"). 
And you will be able to use every thing in ubuntu.

---

### Post by mikewhatever on 2007-01-22
Check the drop down menu fist. Firefox, Open Office etc are there already. To get more, right click on Applications, choose Edit Menu. To get even more use Synaptic Package Manager. All that assuming you have Ubuntu 6.10 version.
Since you've only just installed, you need to enable extra repositories, and update. See here [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by steve.horsley on 2007-01-22
You mean you installed those applications from the CD into Windows? If so, read on. If I'm wrong, ignore this post.

Although the Ubuntu CD comes with a few Windows installers for popular programs like thse you named, that is not the main purpose of the CD. The CD is a bootable CD (if you burn it properly). That means that you reboot the PC with the CD in the drive and the PC then boots from the CD instead of from the hard disk. To burn the CD properly, you must burn the image to disk **as an image** - most CD burning software has a special option for handling .iso image files.

After booting the CD, if you downloaded the live CD you should find youself in the Ubuntu desktop, with an icon near the left to install to the hard disk if you want. The "alternate" installer gives you a text-mode installer menu instead, and no GUI desktop. I suggest you try the live CD first, to see what the desktop looks like and see what you are in for.

Ubuntu is a different operating system to Windows- it's not a program that runs on top of Windows. The installer can either shrink the Windows partition to make room for Ubuntu as well (in which case you get a choice of which to load when the PC is turned on), or it can replace windows entirely.

Please make a backup of all your valuable data before attempting an install, just in case.

---

### Post by Tomosaur on 2007-01-22
Contrary to what housam stated:

Your internet connection should work with the LiveCD. That means, you burn the file you downloaded onto a CD (as an image), keep it in your CD drive, and reboot the computer. MOST computers will recognise the CD automatically and boot from it. Others may need to be told to use the CD, or they will just start loading Windows automatically. If your computer does not boot from the CD, you will need to:

[LIST]
Reboot your machine.
As it is starting up, look for something which says: "Press F2 to enter setup". The button may not be F2, it could be a different F button, or it may be the delete button, etc etc. Press the button.
A menu should appear. In very rare cases it may ask you for a password. If it does, you may be stuck - you need to know what this password is. In mot cases the menu should just appear. You need to look for something along the lines of 'Bootup Sequence', and it will have a list. Normally it will say something like 'Hard Disk, CD-Rom, Floppy Drive'. You need to change that list so the CD-Rom is first. Once you've done that, save and exit. Your computer will reboot.
Once the CD is loaded, select the 'Start Ubuntu or Install' option (or something very similar). Ubuntu will now load (very slowly, remember it's running off a CD. If you install Ubuntu, it is much, much faster). Once it's loaded, you SHOULD be able to use the internet, all of the programs etc etc. If something is not working, you may well have problems if you decide to install Ubuntu. A common cause for concern is wireless internet. It frequently does not work in the LiveCD. It can be solved however, after you install Ubuntu (in most cases. You may wish to research your particular wireless card for how to get it working with linux, or ask here).
[/LIST]

If you decide to install Ubuntu, you need to decide whether you want to keep Windows, or overwrite it. If you want to keep Windows, you will need to manually edit the partitions of your hard drive to make room for Ubuntu. There are lots of threads on the forum detailing how to do this.

Once Ubuntu is installed and running, you can click the Applications menu and select 'Add/Remove'. From there, you can choose programs to download and install (you don't need to look around the internet, or go out to a store!). There is a similar program in the System > Administration menu called 'Synaptic Package Manager'. This program is intended for more advanced users, and lists more software, but it too is fairly easy to use. You just click 'search' or select one of the categories, then click the box of the software you wish to install. When you click 'apply', the software will be downloaded auomatically and installed. Much easier than spending money or doing an internet search :)

Welcome to Ubuntu :)

---

### Post by crimesaucer on 2007-01-22
If you install Ubuntu instead of using the live CD, I would use the wiki page to install applications. And if the app you want isn't there, then use synaptic's search and install it in synaptic.

I just started using Ubuntu in October and instead of using Automatix2 or Synaptic, I just used the Terminal and the terminal code found in the Ubuntu wiki page to install programs and necessary things like java and flash.

Doing that taught me more about Ubuntu than just checking boxes of applications that I wanted to install.

This is the wiki page:

[http://ubuntuguide.org/wiki/Main_Page](http://ubuntuguide.org/wiki/Main_Page)

This is the wiki page's menu for edgy:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

this is the part where you add repositories for edgy on that same page:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)

---

