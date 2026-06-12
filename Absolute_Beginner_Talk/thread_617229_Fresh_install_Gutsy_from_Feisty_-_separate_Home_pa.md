---
title: "Fresh install Gutsy from Feisty - separate Home partition"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by neotasic1 on 2007-11-19
Hi all, just a newbie question regarding retaining my settings with a fresh install of 64 bit Gutsy.  I  currently have Feisty installed with a separate home partition.  If I do a fresh install of Gutsy, will most of my desktop settings survive (Currently using Metacity with Mac4Lin appearance.)  Also, if the installation goes pear shaped, can I reinstall Feisty and recover to where I am at the moment.

One more quick question - running the LiveCD version of Gutsy there appears to be no indication of  Compiz Fusion being present - nor do there appear to be any configuration options (Cube, emerald themes etc).  Are these available after installation?

---

### Post by urk_nono on 2007-11-19
If you choose to **upgrade** none of your current settings will be changed. After having installed Gutsy you should be able to switch on Desktop effects under "Appearences". 

Urk

---

### Post by Arthur Archnix on 2007-11-19
Gnome 2.2 has some changes, especially with respect to mac4lin. If you go to their site now you'll notice they've created a separate package for it. So even if you upgrade you may have some tweaking to do to get it back to where you are now.

---

### Post by neotasic1 on 2007-11-19
> **urk_nono said:**
> If you choose to **upgrade** none of your current settings will be changed. After having installed Gutsy you should be able to switch on Desktop effects under "Appearences". 

Urk

I thought I would go down the fresh install path, as I lack confidence that the upgrade will be trouble free, and I don't really mind if I have to reconfigure later if I have to.  There seems to be 2 schools of thought as to which method is better, so I will try the fresh install first on my desktop and maybe the upgrade on my laptop if all goes well.

---

### Post by neotasic1 on 2007-11-19
> **Arthur Archnix said:**
> Gnome 2.2 has some changes, especially with respect to mac4lin. If you go to their site now you'll notice they've created a separate package for it. So even if you upgrade you may have some tweaking to do to get it back to where you are now.

Yes I had noticed the differences, and so downloaded both sets of tarballs for just such an occasion. I suppose I will find out in about 30 minutes.

---

### Post by daengbo on 2007-11-19
Since your /home is on its own partition, just about everything from a user standpoint should be the same. I believe the Mac4Lin theme uses a patched GTK to get the panel menu, so that will obviously have to be recompiled. As long as your extra themes are installed in your home directory, though, you should be golden. I used to always have a /home partition so that I could switch or reinstall with no loss of data / preferences.

---

### Post by natehatewindows on 2007-11-19
i would do a fresh install

---

### Post by dimeotane on 2007-11-19
Anyone who's done this, please can you describe the 'work flow' stages that you had to follow?

I've had a nice run on my Ubuntu system .. which started at Dapper-upgraded to feisty--upgraded to Gusty... But I've been frustrated with the gusty upgrade being problematic.... so I think it may be time for a fresh install from CD. 
As with the first posting, my /home directory is on a separate partition. 
In order to do this fresh install, I imagine theres a few important things to consider.


1) All applications will need to be reinstalled.  I can easily 'apt-get install' most of them, but there are a few others that I compiled manually and/or installed .deb files from other repositories.  Will they need to be manually re downloaded, and reinstalled or is there another option?

2) All user accounts will need to be restored --> manually?

3) The fstab will need to be edited to restore access to the other partition for my /home directory. 

4)  All the other unforseen issues to consider to restore my system back to it's current 'setup' ... 



Anyone know of a FAQ/How2 that outlines this process?

---

### Post by philinux on 2007-11-19
1. Used psychocats to move home to separate partition.

2. Backup /home to usb drive

3. Installed gutsy from live cd - not format home partition

---

### Post by neotasic1 on 2007-11-22
> **dimeotane said:**
> Anyone who's done this, please can you describe the 'work flow' stages that you had to follow?

I've had a nice run on my Ubuntu system .. which started at Dapper-upgraded to feisty--upgraded to Gusty... But I've been frustrated with the gusty upgrade being problematic.... so I think it may be time for a fresh install from CD. 
As with the first posting, my /home directory is on a separate partition. 
In order to do this fresh install, I imagine theres a few important things to consider.


1) All applications will need to be reinstalled.  I can easily 'apt-get install' most of them, but there are a few others that I compiled manually and/or installed .deb files from other repositories.  Will they need to be manually re downloaded, and reinstalled or is there another option?

2) All user accounts will need to be restored --> manually?

3) The fstab will need to be edited to restore access to the other partition for my /home directory. 

4)  All the other unforseen issues to consider to restore my system back to it's current 'setup' ... 



Anyone know of a FAQ/How2 that outlines this process?

I have completed this a couple of days ago.  You have identified most of the problems you will come across.  I would probably make a backup of my home partition, and also of the /usr directory.  

Most of it has gone smoothly.  Because I had a Mac4Lin desktop setup I had to reconfigure some of it, and recompile AWN, but it was all worth it.  Everything works as it should although I did experience the slow boot bug and have employed the workaround.  

I also had trouble getting DVDs to play - the solution to which is in  another of my posts and refers to a post by mdpalow which I believe should be stickied, but I don't know to whom this should be proposed.  Any moderators reading this?  The thread concerned is [http://ubuntuforums.org/showthread.php?p=3774207#post3774207](http://ubuntuforums.org/showthread.php?p=3774207#post3774207)

Hope this helps good luck.

One other thing - make sure you don't overwrite your home partition during the fresh install, as you will have to arrange the partitioning manually.  Its a good idea to identify it first - it will be in your current fstab where you redirected to your home partition.

---

