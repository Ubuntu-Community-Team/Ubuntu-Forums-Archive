---
title: "Application installs and updates in Ubuntu"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by MutantsForNukes on 2006-08-03
Hi all, first post.  I'm thinking about chucking windows and going with Ubuntu.

The last desktop linux exposure I had was with Mepis on a dual boot at home, and that was some time ago.  I liked it, but the main thing I'm looking for to make the switch the easiest for me is ease of install and update for the apps I'll use.  With Mepis I used apt-get and a gui front end, synaptic I think.  I had various degrees of success with this, but found it harder than I wanted.  Can anyone give me a quick rundown of how app installs and updates are handled in the Ubuntu/Linux world these days and your opinion of how smooth it is?  Thanks.

---

### Post by tzulberti on 2006-08-03
Hi. It uses the same system as Mephis: apt-get. You have a front end called Synaptic. I have been using it, and it is very easy. I recomend you to use the backport and universe sources...

---

### Post by ewl1217 on 2006-08-03
Installs you'll have to use Synaptic (which I find really use to use, by the way), apt-get, etc. for, but upgrades are much easier. You'll be notified of avaliable upgrades by an icon in the system tray. Just click on it, enter your password, and it'll show you what's being upgraded with a button to click to apply the updates. If a reboot is required (for kernel upgrades mainly), it'll remind you that you have to reboot for it to take effect. It's that easy.

---

### Post by zasdarq on 2006-08-03
I'm just starting to use Ubuntu also (installed it on my laptop last night), after a lot of work I was able to actually get wireless to work :)  However, despite how many times I've seen on the forums to use it, apt-get never works for me.  It just says "package not found."  Do I have to set it up to work before hand or something?  Sorry for the completely newbie question :-/

Thanks so much, this forum is amazing,
Matthew

---

### Post by Dr. Nick on 2006-08-03
you have to know the exact name of the package for apt-get, If you use synaptic then you can search for it. Not all applications are installable via apt-get however, Alot are if you enable the extra repositories though.

---

### Post by zasdarq on 2006-08-03
(If this is considered hijacking the thread, I'll happily repost, I just thought it was on subject and he was done)

I've tried

sudo apt-get install network-manager-gnome
sude apt-get install network-manager
sudo apt-get install xorg-driver-fglrx

all of which were suggested on the forum, and I know the last one existed since I ended up using the synaptic to install that exact thing.  Regardless it gives the same message "package not found."

Thanks again,
Matt

---

### Post by Dr. Nick on 2006-08-03
Well I tried installing with the exact commands you posted and it appeared to work fine. Ill post a few general tips that are helpfull to everyone, If they dont help you then you may put up a new thread to increase exposure to your specific issue

apt-get relies on the sources.list file located in /etc/apt/sources.list

here is a link discussing the sources.list file
[http://ubuntuforums.org/showthread.php?t=185758](http://ubuntuforums.org/showthread.php?t=185758)

If your file is empty then you will not get any programs to install using apt-get, before trying to install anything it is always a good idea to update apt-get by using

sudo apt-get update

that will re-download the list of avaible packages so you can be sure you are trying to install the newest versions that exist on the server. If nothing seems to install I would check to make sure your sources.list file looks like the one in the link above and that apt-get update has been run.

To upgrade the entire system via command line it is 

sudo apt-get dist-upgrade

However the new auto-update notify feature sort of replaces this, I have always had smooth updates using either method. 

I have never used mepis, but I know the apt-get system for me is much easier then the rpm based systems like mandriva and suse

---

### Post by MutantsForNukes on 2006-08-03
No hijack worries, this thread is very helpful.  I guess I was hoping for a major revolution in apt-get or something, but everything that's been said here is encouraging.  So the Ubuntu upgrade notification system is for both applications and kernel updates?  Very nice.  I'll check out the live cd tonite and look through my system for any windows apps I can't live w/o.  Thanks all.

---

### Post by popkid on 2006-08-03
Heya... just a quick one... the main repositories actually seem to be down at the moment (for me anyway) it may be worth just waiting till tomorrow and retrying commands then, as that maybe why you can't find some stuff using commands that have worked for others.

pK

---

### Post by Dr. Nick on 2006-08-03
> **MutantsForNukes said:**
> No hijack worries, this thread is very helpful.  I guess I was hoping for a major revolution in apt-get or something, but everything that's been said here is encouraging.  So the Ubuntu upgrade notification system is for both applications and kernel updates?  Very nice.  I'll check out the live cd tonite and look through my system for any windows apps I can't live w/o.  Thanks all.


Yes the upgrade system will notify of kernels update aswell, it will not how ever remove files, if updating something requires removal of something else I think it makes you do it manually in synaptic, Someone correct me if I am wrong, thats just what I have noticed.

If you are not really thrilled with apt get then look at aptitude, very similar syntax but a bit more powerful

[http://www.psychocats.net/ubuntu/aptitude.php](http://www.psychocats.net/ubuntu/aptitude.php)

I have heard that the package management may change some in edgy, or later versions, Guess we will wait and see

---

