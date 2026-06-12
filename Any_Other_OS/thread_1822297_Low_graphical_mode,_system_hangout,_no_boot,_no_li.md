---
title: "Low graphical mode, system hangout, no boot, no live CD boot..."
date: 2011-08-10
forum: Any Other OS
---

### Post by vasiauvi on 2011-08-10
Hello all,
I have a Linux Mint 11 instalation (until some months ago I had Ubuntu 11.04) and since yesterday I have different problems. Let's explaine in steps:

- I had updated my system (I can't say what files were installed)

- restarted and the system entered in "low graphic mode" but no options from menu are working. I have made a video (bad quality but to get the idea) [here]("http://www.youtube.com/watch?v=34KCYmIO2rI").

- I have made Bootable USB stick with different distributions like Puppy, DSL, Fedora, Ubuntu also tried with Live CD (Ubuntu) but I get errors and the system remains in "standby". Here I have made pictures of the errors:
     [Linux Mint editing the grub]("http://i.imgur.com/jlQiH.jpg")
     [Fedora live USB]("http://i.imgur.com/SLJZG.jpg")
     [Ubuntu Live CD]("http://i.imgur.com/lacAt.jpg")

- **conclusion until now** is that I can't manage to boot with LiveCD or USB stick although with Puppy Linux it worked but I couldn't mount the ext4 drives but the ntfs drives were mounted corectly.

- the tty doesn't work that means that I can't write something like: sudo dpkg-reconfigure xserver-xorg

- I have dual boot with WinXP. Entered here and installed Ext2explore and Ext2fsd at least to back up my files from /home.

When entering on /root partition with Ext2fsd is asking me if I want to format it. I didn't continued but as final resort can I format the /root and try again to install from scratch a new distribution? My /home partition will remain untouched hopefully.

Someone knows a reason why I can't boot or why even the Live CD gives errors? I have used more than one live cd and more than one bootable usb stick.

Thanks and sorry for the mistakes in writting this topic...

EDIT: a forgot to mention that I don't se on my system file /etc/X11/xorg.conf but is xorg.conf.failsafe. Here you have an archive where I managed to save xorg.0.log and other files: [link]("http://dl.dropbox.com/u/1518616/xorg.tar"). If you can please tell me what other files are relevant to save to place here maybe it's shows clues why this is happening...

---

### Post by Mark Phelps on 2011-08-10
If you're still running Mint, you should really be going to their forums with your questions -- because Mint incorporates customizations that make it somewhat different from the standard Ubuntu install.

Also, they have their own support community and they can provide you more detailed help.

---

### Post by vasiauvi on 2011-08-10
> **Mark Phelps said:**
> If you're still running Mint, you should really be going to their forums with your questions -- because Mint incorporates customizations that make it somewhat different from the standard Ubuntu install.

Also, they have their own support community and they can provide you more detailed help.

Yes, I also made a topic there but the base of the system I think that is the same. Linux Mint is different than Ubuntu by some visual things. I don't think that they have changed something in the basic files like xorg.conf...

I have tried here because I've used 4 years Ubuntu and I know that there are people who can help me with an advice no matter that I am using Mint or Ubuntu.

---

### Post by Perfect Storm on 2011-08-10
Moved to Other OS/Distro Talk.

---

### Post by vasiauvi on 2011-08-20
I've resolved this problem installing from scratch Ubuntu 11.04 :)

---

