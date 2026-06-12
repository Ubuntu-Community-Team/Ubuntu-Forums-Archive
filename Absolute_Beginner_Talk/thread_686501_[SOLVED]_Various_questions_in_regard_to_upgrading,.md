---
title: "[SOLVED] Various questions in regard to upgrading, backup, home partition and synapti"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by the8thstar on 2008-02-03
Hello,

I have several questions to ask about backing up data, the /home partition and whether I should perform upgrades or clean installs. So here it goes...

**1. Data backup**

I have set Ubuntu 7.10 to have a separate /home partition. It has been recommended several times on the forums so I took the advice. This partition runs on the same disk as the rest of the filesystem and my Vista partition too. Just in case, is an incremental backup of /home a good option? Is it worth doing since we're talking about the same disk here (80Gb)? Should I get an external USB2.0 drive?

**2. Home partition**

My home partition contains work documents, and folders that set some of the aspect and behavior of Ubuntu (look and feel mostly). When I upgrade or perform a clean install, will these settings remain the same or will they be erased? How can I make sure I'm not going to zap my /home partition when I use a liveCD to perform a fresh install?

**3. Using synaptics or a "harvest" script**

Instead of backing up the data and the programs I have installed, I was wondering if there is a command on the CLI or a GUI app that could make a list for me and bundle it as a script if I need to reinstall everything. Ideally the list would contain all the info in the wget http: and/or apt-get form. It could be linked to synaptics. Is this doable?
[B]
4. Fine tuning the system... can this be saved too?[/B]

In order to make myself clear, I'll use a few examples. Let's say I want to set the usplash screen with a resolution of 1280x800 instead of the 1024x768, I want the processor to run "on demand" to save power, I want xorg.conf to recognize my s-video port and I want to use the "no-writeback" option on my ext3 partitions... Can these settings be saved? If so, how?

Thank you very much in advance. As always, I hope that my questions will answer other users' concerns too.

---

### Post by bwhite82 on 2008-02-03
1) Yes, you should backup to external media.

2) When you upgrade, the settings *should* remain intact, but because we don't live in a perfect world, refer to number 1. After the upgrade, simply restore the /home.

3) In Synaptic this option is sort-of built-in. But as far as I can tell, it needs to be done when you are first installing packages. (I could be wrong on that) Anyways, open Synaptic goto: File>Generate Package Download Script

4) Backup the relevant files.

-Cheers

---

### Post by the8thstar on 2008-04-13
> In Synaptic this option is sort-of built-in. But as far as I can tell, it needs to be done when you are first installing packages. (I could be wrong on that) Anyways, open Synaptic goto: File>Generate Package Download Script

I wasn't able to make this work. It asks me to save a file without extension and with zero data in it. Can someone elaborate please?

---

### Post by Moop on 2008-04-13
Take a look at QuickStart. I haven't used it but it could be what you're looking for. 
[http://ubuntuforums.org/showthread.php?t=613462&highlight=backup+solution](http://ubuntuforums.org/showthread.php?t=613462&highlight=backup+solution)

---

### Post by the8thstar on 2008-04-13
Thanks **Moop**. I'll check the link out.

----

Ok, I checked it. Awesome!

---

### Post by mister_pink on 2008-04-13
I know this is marked as solved but I thought I'd give a bit of a how to seeing as I just reinstalled and have a separate home.

You'll want to do a manual partion bit, and select your current disk, setting its mount point as /. Then select your home partion and tell it to mount to /home and check that is definitely not set to format it. 

I think its much easier to do it at this stage than to try and move your home once its all installed. It seems like you do know what you're doing though anyway. Once I reinstalled everything looked just like it did before. 

If you want to get a list of packages you've manually installed, see this thread: [http://ubuntuforums.org/showthread.php?t=748372](http://ubuntuforums.org/showthread.php?t=748372) I asked that question for this reason exactly! You could probably automate the whole thing with some clever shell scripting...

---

