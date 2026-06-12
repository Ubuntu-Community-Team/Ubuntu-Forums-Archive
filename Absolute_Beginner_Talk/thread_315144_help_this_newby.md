---
title: "help this newby"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by bandreasen on 2006-12-08
I'm new to ubuntu although I've been using other linux distributions with GUI interfaces. I think the big difference is not having root access through the GUI.  So far I've got a few problems that are are making my life difficult.

1. I want to edit system files such as menu.lst to make grub boot into my other OSs.  (There's other system files I also want to edit)  What I've read in the forums uses gedit but my system doesn't recognize gedit.  Where do I get it and how do I install it?

2. I have all my data files on other partitions of my computer.  How do I access those files and use them?  Those partitions are generally fat or fat32 partitions.

3. I've also found out that I can't copy data to the removeable media.  How can I get information or data I've generated in ubuntu into my data files that are elsewhere.  

I realize that after a while it'll be old hat to me but right now I feel like I'm trying to swim without any arms - difficult but not impossible.  Unfortunately I think I'm sinking.  Ubuntu is not intuitive and learning the command line is not easy.

---

### Post by shanepardue on 2006-12-09
the command line is nice to have learned, but if you install automatix ([www.getautomatix.com)](www.getautomatix.com)), there's a package called "nautilus scripts" that lets you have root access from nautilus (gui).

---

### Post by igknighted on 2006-12-09
> **bandreasen said:**
> I'm new to ubuntu although I've been using other linux distributions with GUI interfaces. I think the big difference is not having root access through the GUI.  So far I've got a few problems that are are making my life difficult.

1. I want to edit system files such as menu.lst to make grub boot into my other OSs.  (There's other system files I also want to edit)  What I've read in the forums uses gedit but my system doesn't recognize gedit.  Where do I get it and how do I install it?

2. I have all my data files on other partitions of my computer.  How do I access those files and use them?  Those partitions are generally fat or fat32 partitions.

3. I've also found out that I can't copy data to the removeable media.  How can I get information or data I've generated in ubuntu into my data files that are elsewhere.  

I realize that after a while it'll be old hat to me but right now I feel like I'm trying to swim without any arms - difficult but not impossible.  Unfortunately I think I'm sinking.  Ubuntu is not intuitive and learning the command line is not easy.

I use nano, its a terminal text editor that is much simpler than vi.  To edit menu.lst, just type 'sudo nano /boot/grub/menu.lst'.  gedit is another choice, but istead of sudo use gksudo (this is only for gnome).  If you are in KDE use 'kdesu kate /file/to/edit' (kwrite is another fine choice, if you are familiar w/ kde you might know kedit as well, but it does not come with kubuntu standard).  If you use xubuntu, the text editor is mousepad.  I dont know the special gui sudo command, so just try 'sudo mousepad /file/to/edit'.  Another option for editing via GUI is to open nautilus (or thunar or konqueror, depending on your DE) as root, using the sudo command (ie, 'gksudo nautilus')

---

### Post by quarkhirad on 2006-12-09
2. I have all my data files on other partitions of my computer.  How do I access those files and use them?  Those partitions are generally fat or fat32 partitions.

Just have a look at the following hread i have given a detailed way of mounting ur windows partitions.Note if u have more than 2 partitions then use the mkdir command that many no of times. Same with the mount command. 

[http://ubuntuforums.org/showthread.php?t=310590&goto=newpost](http://ubuntuforums.org/showthread.php?t=310590&goto=newpost)

---

