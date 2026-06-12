---
title: "A few questions"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by Einherjer on 2007-03-08
Hi!

I get an error when i boot up:

There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

I'm going to install Ubuntu on my mom's computer, an upgrade from mandrake hehe But since it's a P3 500mhz ..i was wondering which graphical interface i should install since it's a slow system.

I installed the ATI drivers, since then performance is much worse than before ...i followed the steps at [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) so i went to the verify install and i do the $fglrxinfo command in the console and nothing happens.

How can i access my second HDD? It's NTFS formatted but has no OS on it, it's my backup drive.

I have a sound problem, my mobo is an asus nvidia nforce2 with AC97 sound. But the only sound i hear is when i boot ubuntu ..the rest like gaim will make my pc speaker beep! How can configure my sound output?

---

### Post by x1a4 on 2007-03-08
> **Einherjer said:**
> Hi!

I get an error when i boot up:

There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

What did you do before this error showed up?

> How can i log in as root in the console? i do su and enter my pass auth failure ..uh?

Enable the root account by setting a password for it.  

*sudo passwd root*

> I'm going to install Ubuntu on my mom's computer, an upgrade from mandrake hehe But since it's a P3 500mhz ..i was wondering which graphical interface i should install since it's a slow system.

Xfce, FluxBox, BlackBox or WindowMaker.  I recommend Xfce.  

> I installed the ATI drivers, since then performance is much worse than before ...i followed the steps at [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) so i went to the verify install and i do the $fglrxinfo command in the console and nothing happens.

If you followed the directions in that link then *fglrx* module is disabled.

> How can i access my second HDD? It's NTFS formatted but has no OS on it, it's my backup drive.

Since your second drive is empty, why not just reformat to a Linux filesystem?  

To read and write to a ntfs file system, install *ntfs-3g* and *FUSE* then mount the ntfs file system with ntfs-3g

[HOWTO: NTFS with read/write support using the ntfs-3g (easy & safe method)](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g+howto)


> I have a sound problem, my mobo is an asus nvidia nforce2 with AC97 sound. But the only sound i hear is when i boot ubuntu ..the rest like gaim will make my pc speaker beep! How can configure my sound output?

Use the GNOME Control Panel to configure sound.

---

### Post by Einherjer on 2007-03-08
1. i installed the ATI drivers.

2. and 3. Thanks!

4. i don't understand... :(

5. it's not empty, has my windows software and most importantly, my mp3s hehe so i want to be able to get there and listen to my mp3 when in ubuntu. Thanks i'll follow those steps.

6. call me total newb ..and thats what i am but where is the gnome control panel?

Thanks!

---

### Post by x1a4 on 2007-03-08
> **Einherjer said:**
> 1. i installed the ATI drivers.

Post this question separately and someone will surely be able to help you.  

> 2. and 3. Thanks!

You're welcome.  

> 4. i don't understand... :(

One of the steps in the link you provided asks to disable *fglrx*.  BTW when you ran *fglrxinfo* did you include the $ sign?  The $ sign denotes a user prompt and is **not** a part of the command.  Run *fglrxinfo* without the $ sign.  You only use the $ sign when referring to variables.  

To enable *fglrx* edit _/etc/default/linux-restricted-modules-common_

and remove fglrx from the list of disabled modules.  You'll have something like this.

**DISABLED_MODULES="fglrx,*module2*,*module3*..."**

remove **fglrx** from this list.  If **fglrx** is the only thing there, remove the whole line or comment it out by placing a # in front of it. 


> 5. it's not empty, has my windows software and most importantly, my mp3s hehe so i want to be able to get there and listen to my mp3 when in ubuntu. Thanks i'll follow those steps.

If you have enough space on your Ubuntu drive, I recommend you copy all your files from the ntfs partition to it, reformat the ntfs file system to a Linux one, then move your files to it.  

> 6. call me total newb ..and thats what i am but where is the gnome control panel?

My bad, it's the GNOME Control Center. 

I don't use GNOME so I don't know exactly where in the menu it is, but you can just run *gnome-control-center* from a terminal, OR, 

System > Preferences > Sound 

> Thanks!

You're welcome.

---

### Post by Einherjer on 2007-03-08
Alright but Beryl still crashes, i was told to disable composite for that.. hmm

---

