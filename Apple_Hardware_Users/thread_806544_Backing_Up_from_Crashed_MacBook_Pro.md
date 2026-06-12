---
title: "Backing Up from Crashed MacBook Pro"
date: 2008-05-25
forum: Apple Hardware Users
---

### Post by muna580 on 2008-05-25
I have a MacBook Pro here that has crashed. Everytime I start my Mac, it works at first and then freezes. I am trying to backup all my dad from the HD without having to remove the HD and connecting it to an enclosure case. 

Can I use Ubuntu to backup my data to an external? I have a Ubuntu 7.10 CD and I put it in but it didn't boot. What do I do? 

I am new to both Mac and Ubuntu. YES, I am new to a Mac, so please help me through the proceess of running the live CD and backing up my data. 

Thank You

---

### Post by frog_pilot on 2008-05-25
You dont need to remove your had and dont need ubuntu for backing up.

Hold the T-key during startup. The macbook will start in Target-mode. This means, its like an external firewire drive. Connect it to any computer which is able to read hfs+ file system, backup valuable data.

Voila...

---

### Post by muna580 on 2008-05-25
I don't have another Mac or a firewire wire with me. How do I do it with Ubuntu?

---

### Post by frog_pilot on 2008-05-25
In OSX there is also the option to do a clean install of the os and keep your userfiles untouched. If you dont choos to perform a clean install. An other option is to archive the old system and install osx again.

with ubuntu you also need a second hard drive and a network connection.

start from the ubuntu cd. search by name via synaptic for "hfs*". You will find 2 packages: hfsplusutils and hfsplus (i dont exactly remember the names, but it is something similar).

Install these 2 packages.

Attach a external hd (best would be with ext3 file system). it will mount automatically.

Mount your osx-drive (you can do it by clicking on it in nautilus (ubuntus finder))

To access your user-profile subfolders in osx you need root privileges. To start nautilus as root, execute in a terminal ```
gksu nautilus
```

In the appearing nautilus-window you have root privileges. Do your copying inside this window. If you also want to keep your settings/mail etc also copy ~/Library

reinstall OSX

install ext2fsx to access the ext3-hd.

---

### Post by muna580 on 2008-05-25
> **frog_pilot said:**
> In OSX there is also the option to do a clean install of the os and keep your userfiles untouched. If you dont choos to perform a clean install. An other option is to archive the old system and install osx again.

with ubuntu you also need a second hard drive and a network connection.

start from the ubuntu cd. search by name via synaptic for "hfs*". You will find 2 packages: hfsplusutils and hfsplus (i dont exactly remember the names, but it is something similar).

Install these 2 packages.

Attach a external hd (best would be with ext3 file system). it will mount automatically.

Mount your osx-drive (you can do it by clicking on it in nautilus (ubuntus finder))

To access your user-profile subfolders in osx you need root privileges. To start nautilus as root, execute in a terminal ```
gksu nautilus
```

In the appearing nautilus-window you have root privileges. Do your copying inside this window. If you also want to keep your settings/mail etc also copy ~/Library

reinstall OSX

install ext2fsx to access the ext3-hd.

I am completely lost about what you said. 

I want to play it safe and don't want to do a clean install of OS X. I am trying to do it with Ubuntu only. I have an extra external HD here which I am going to backup my files to.

So now, what is the producrue to run the live cd? Can't I just put the CD in and reboot and it runs automatically like in Windows? Cause I can't really browse through any of the files in this Mac, it freezes right from the moment it restarts.

---

### Post by pxwpxw on 2008-05-25
1. To boot from the Ubuntu 7.10 i386 Desktop CD -
 with CD in slot, restart and hold down the Option key until CD icon appears (called "Windows"). Start that to get into the Ubuntu desktop. Then you will need further help to access Macosx partition and files.

2.If you have the Apple MacosX dvd you should be able to boot from that to confirm that the MacBook Pro is usable, without reinstalling.

---

### Post by muna580 on 2008-05-26
> **pxwpxw said:**
> 1. To boot from the Ubuntu 7.10 i386 Desktop CD -
 with CD in slot, restart and hold down the Option key until CD icon appears (called "Windows"). Start that to get into the Ubuntu desktop. Then you will need further help to access Macosx partition and files.

2.If you have the Apple MacosX dvd you should be able to boot from that to confirm that the MacBook Pro is usable, without reinstalling.

OMG thank you so much. OPTION key was the magic word I was looking for the whole time. Was just trying to figure out how to boot from CD. Now I know, unlike Windows which boots from CD automatically, in Mac you have to hold down the Option key. 

I am now inside Ububntu. Just trying to figure out where are all the main user files located. For example in Windows everything is located in C:/Users (Vista). Where do I go in Mac?

Also when I try to ascess folders, it says I don't have the persmission. How do I get myself the permission to acess the folders.

---

### Post by cyberdork33 on 2008-05-26
> **muna580 said:**
> OMG thank you so much. OPTION key was the magic word I was looking for the whole time. Was just trying to figure out how to boot from CD. Now I know, unlike Windows which boots from CD automatically, in Mac you have to hold down the Option key. 

I am now inside Ububntu. Just trying to figure out where are all the main user files located. For example in Windows everything is located in C:/Users (Vista). Where do I go in Mac?

Also when I try to ascess folders, it says I don't have the persmission. How do I get myself the permission to acess the folders.
you have to be root because the system sees those files as not belonging to you. ```
 sudo nautilus
``` will open a browser with root privs.

In OSX, the user home directories are in /Users

---

### Post by muna580 on 2008-05-26
> **cyberdork33 said:**
> you have to be root because the system sees those files as not belonging to you. ```
 sudo nautilus
``` will open a browser with root privs.

In OSX, the user home directories are in /Users

I can't access my Mac HD when I do *sudo nautilus*. It just opens up a windows with the filesystem files of the Ububntu. 

Can someone please give me step by step procedure in order to access my files and have them trasnfers to my external.

---

### Post by cyberdork33 on 2008-05-26
> **muna580 said:**
> I can't access my Mac HD when I do *sudo nautilus*. It just opens up a windows with the filesystem files of the Ububntu. 

Can someone please give me step by step procedure in order to access my files and have them trasnfers to my external.

you have to mount the filesystem first, then navigate to the folder it is mounted on in your root-enabled nautilus window. Usually filesystems are mounted on folders in /media in Ubuntu.

If you want an easier (and safer) solution, why don't you install OSX to the external, boot from it and copy the files you want from your internal drive, then reinstall on your internal.

---

### Post by muna580 on 2008-05-26
Can you please give me step by step procedures on how to do the mounting. I don't udnerstand how to do anything. I am both new to Ubuntu and Mac. 

How do I mount to fix system? 

So far the only thing I understand how to do is boot the live Cd by holding on to the Option button. Once I get into Ubuntu, I don't know what to do.

---

### Post by pxwpxw on 2008-05-27
I  would strongly advise using a temporary  macosx installation on the external hard drive as suggested by Cyberdork33 as the easiest/safest option if you are new to both macosx and linux. 

 However if you must use ubuntu - the story so far - 

Running ubuntu 710 desktop cd on a MacBook

Assuming you have a 2 button mouse.

```

From the Ubuntu desktop -

1. Open a  file browser as ordinary user "ubuntu" )

 Select Places from desktop main menu bar.
    Select Computer to get a File Browser showing all volumes
         Right click on your macosx volume, select "mount volume"

Leave this file  browser open.

2. Get a second file  browser with root privileges   -
 
Open a terminal from Main menubar/Applications/Accessories 

    sudo nautilus


 Then in the root browser 
     Select  File System/ Media

```

That should show the macosx volume you mounted, and allow read access to the /Users folders

Warning - As root user, you are unprotected against accidental deletions or other accidents.
Your root user status only applies the the root browser window.

---

### Post by muna580 on 2008-05-27
Thank you SO MUCH, seriously, I really appreciate you guys helping me. It worked and I was able to backup all the files :)

---

