---
title: "Ever wondered how to upgrade to feisty. I did it without a hitch."
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by kpkeerthi on 2007-04-18
For those who are wondering what it takes to "upgrade" to feisty, here is my story...

1. First and the most important 
	[INDENT]- Backed up my entire root partition using partimage. I wanted to be able to restore the entire setup the way it was if the upgrade process ruins my system.[/INDENT]
	[INDENT]- Also backed up my $HOME just incase if I have to restore some of the files from $HOME like .config files and documents.[/INDENT]

2. Removed packages I installed from external repos and source files. I was not sure whether I have to do this but I still did this to avoid any incompatibilities:
	[INDENT]1. Uninstalled wine I had from a svn repo.[/INDENT]
	[INDENT]2. Uninstalled nvidia driver using envy. Switched to open source "nv" driver in xorg.[/INDENT]
	[INDENT]3. Purged envy. envy does not support feisty yet.[/INDENT]
	[INDENT]4. Purged beryl and emerald and dependencies I installed from beryl repository.[/INDENT]
	[INDENT]5. Also removed the debs I installed from [www.getdeb.net](www.getdeb.net). I have had exaile and f-spot installed.[/INDENT]
	[INDENT]6. Removed K3B 1.0. I have had k3b 1.0 and dependencies compiled from source. I used checkinstall so it was easy for me to restore back to Edgy's version. [/INDENT]

Then I ran gksudo "update-manager -c -d". It took about 4 hours to complete the download and upgrade process.
The update manager automatically disabled third party repositories I had in my sources.list. Cool.
Rebooted, checked wireless, audio, video, my documents, preferrences and hardware. Everything looks great 
so far. I then removed external repos from sources.list that were still pointing to Edgy. Then I Installed 
nvidia-glx-new and nvidia-kernel-common from the repo. OpenGL worked just fine. 

This is my first ubuntu upgrade and it was almost painless. Though it took longer than a fresh install, the
process was almost automatic except for a couple of confirmation prompts. And most of all, it saved me a lot
of time by restoring all the "personlizations" and additional packages I had before. I do not have redo that once again.

I still don't have beryl installed yet. But I'll wait till feisty final is released tommorrow. sudo aptitude dist-upgrade should take me from beta to final.

---

### Post by BoneKracker on 2007-04-18
That's a smart process!  Thanks for sharing.

---

### Post by vitalik on 2007-04-18
> **BoneKracker said:**
> That's a smart process!  Thanks for sharing.

I decided to be lazy and did the upgrade right away. The only thing I did is change all repos from edgy to feisty, the is a command for it rename real fast, I just don' remember it. Crossed my fingers and after couple hours was up and running. 

P.S. Don't be lazy and do your homework, it won't be always this easy.

---

### Post by earobinson on 2007-04-18
Thanks!

---

### Post by kpkeerthi on 2007-04-19
[updates]

Its been two days now... so far so great. I've got beryl (official, not SVN) installed and working today. I should say it runs much better in feisty than it did in Edgy. Nothing unusual memory or CPU usage. So looks like a good upgrade. I would  recommend anyone try upgrade first before doing clean install.

---

### Post by Michl on 2007-04-24
This isn't much of a recommendation for upgrading, IMHO.  I might as well do a clean install if you have to find, purge and uninstall all that, and then reinstall it.  Maybe I'm not understanding how you can restore the old packages without reinstalling if you uninstalled them.  Can you say more about that?

Thanks!
Michl

---

