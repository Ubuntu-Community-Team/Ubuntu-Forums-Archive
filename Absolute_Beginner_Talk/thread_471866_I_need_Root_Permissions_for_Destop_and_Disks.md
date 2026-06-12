---
title: "I need Root Permissions for Destop and Disks"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-06-12
Hi,
 I've asked about this before; I've also done searches and I ALWAYS get answers that do not work.  Pardon me for being so blunt. 

I'm in a Gnome desktop enviroment and I have a second hard drive which mostly functions as my Windows Data drive for my windows files.  Whenever I try to copy and/or paste files between that disk and my Ubuntu desktop, I get a window saying I have no permissions to do this. 

I've also tried to copy icons from my desktop to my user/share/pixmaps folder, and I get "root permissions denied".  Please understand that I want root permissions that will allow me to copy and paste THROUGH MY DESKTOP and NOT just from the terminal.  I'm limited in my knowledge of the terminal; I'm not scared to install and run things. It's just that I want to use my desktop enviroment for these things if possible. 

I've tried this command line:   sudo nautilus

And this too (paraphrasing from memory; it may be slightly off):   sudo -h -S

I appreciate any help clearing this up. 

Many Thanks, .....Frank B.

---

### Post by Cypher on 2007-06-12
If you were copying the files using the default gnome file manager, which is nautilus, running 'gksu nautilus' should have allowed you to do all of what you want without any issues.

But, in general you will be able to copy files from other locations into your home directory without any problems, but anything else will require you to SUDO them..

---

### Post by revealer on 2007-06-12
i think the only way to do this is under the terminal or using nautilus scripts but im not sure

---

### Post by starcraft.man on 2007-06-12
I see another example of problems with file permissions. In your case, I assume when the drive/partition was mounted it was assigned permissions only to be used by root which you are not when logged in. You also don't want to default yourself to root power, thats insecure as Win XP being administrator. This can be fixed easily, and at the same time you can learn about how file permissions work in general. 

> **starcraft.man said:**
> Ok, I think its just a minor problem with the permissions of the files. You can fix that easy and I have two guides for you to read that should get ya to solve it.

[Psychocats basic permissions]("http://www.psychocats.net/ubuntu/permissions")
[URL="http://www.linuxcommand.org/lts0070.php"]
Linux Command more complete explanation of permissions.[/URL]

I'm sure you'll be able to fix it easily after reading those two :).

I just quoted myself rather than retype it. Read both and then you'll understand why its saying that and they both also contain examples of how to change file permissions. If you have any questions, feel free to reply again with them and I or someone else will answer :).

"gksudo nautilus" should fix this by elevating the file browser to have root power, it is much more convenient for daily use to lower the permissions of those files/folders/partition to your user.

---

### Post by Brightbelt on 2007-06-12
I also just now realized I left out some vital information. When I try to copy files from my Ubuntu documents and paste them in my windows data drive, I GET NO PASTE OPTION THERE. 

I'm trying to copy some Text Editor files from Ubuntu and paste them with my Notepad files on the windows data disk.  And there is no paste option.

I'll try following your answers meanwhile. Many Thanks, Frank B.

---

### Post by lazyart on 2007-06-12
Is this an NTFS drive?  You might need the ntfs-3gs driver to allow you to write to it.

---

### Post by starcraft.man on 2007-06-12
> **Brightbelt said:**
> I also just now realized I left out some vital information. When I try to copy files from my Ubuntu documents and paste them in my windows data drive, I GET NO PASTE OPTION THERE. 

I'm trying to copy some Text Editor files from Ubuntu and paste them with my Notepad files on the windows data disk.  And there is no paste option.

I'll try following your answers meanwhile. Many Thanks, Frank B.

Yup, means that when you tried doing it you didn't have write permission on the partition/folder. By setting the permissions to your user via the information on the two links you will be able to paste again. Also after understanding how the permissions system works you can deal with all future situations yourself if it ever comes up again :).

Oh and one more thing, if it is a ntfs drive from windows you will need the ntfs-3g drivers. Search the forums and you will find at least one or two complete how tos for Feisty.

---

### Post by Bluecircle on 2007-06-12
If its an NTFS drive you need to do

```

sudo apt-get install ntfs-tools

```

then from the terminal run

```

ntfs-tools

```
and enable disk writing.

---

### Post by Brightbelt on 2007-06-12
Thanks to you all for your assistance. At least the writable part is fixed. I'm lucky Autimatix2 works well on my system, so I installed the NTFS writable thing through it.  

I've tried 'gksudo nautilus' and I'm not sure I have writing capability yet, but we'll see....

Thanks again, Frank B.

---

### Post by Brightbelt on 2007-06-12
Hey, since we're all still here (;)), I thought I should show you this. This is what I get when I run 'gksudo nautilus':

brightbelt@brightbelt-desktop:~$ gksudo nautilus
(nautilus:6359): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Initializing gnome-mount extension

And it still mounts my desktop, but it seems like something is wrong in there.

I appreciate any clarification on this. 

Thanks, ....Frank B.

---

