---
title: "Starting all over again"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by gewitty on 2007-05-04
My first experience of Ubuntu was with Edgy. As I got used to it, I realised that I needed to add some codecs and also wanted to run some virtual machines. In my ignorance, I went for a couple of solutions that turned out not to be such a good idea - Easy Ubuntu and VirtualBox, neither of which are officially supported.

When I upgraded to Feisty, I started to experience some problems, mainly as a result of VirtualBox, which is currently preventing me installing any Ubuntu updates (I won't go into this here. It's being discussed in another forum).

It now looks as if the only way I can get back to a fully working system is to do a clean install. What concerns me though is that although all of my critical data is held on a separate hard drive, there are several apps that store important files within the Ubuntu file system. These are: Thunderbird (mail and address book); Firefox (favourites); GPass (encrypted passwords file)

Can anyone tell me where this data is stored and how best to back it up so that I can restore it after reinstalling Feisty. I am assuming that to get a clean install, I will have to completely reformat my hard drive and start again.

---

### Post by lakersforce on 2007-05-04
I am not sure, but I believe your personal files are stored in the dot (".") folders in your home directory.

---

### Post by viciouslime on 2007-05-04
If by "although all of my critical data is held on a separate hard drive" you mean that your home directory is on a separate partition/hard drive, then you don't have to do anything. Just reinstall ubuntu and during the install process tell it to mount the partition that your home directory is on as /home and of course make sure you don't tick the box to format that partition then when you boot your fresh install login and everything will be exactly as it was. Thunderbird, firefox, etc. don't write anywhere other than your home directory, no program that you run as yourself is allowed to write anywhere other than your home directory.

---

### Post by gewitty on 2007-05-04
Sorry. Should have made myself clearer. By 'critical data', I mean stuff such as photos, music, documents, etc. At the moment, my main hard drive is not partitioned, so everything (including Thunderbird, Firefox and GPass files are on the same drive as Feisty (hd0?). This is why I run the risk of losing them if they are not backed up before I reinstall.

---

### Post by TheWizzard on 2007-05-04
> **gewitty said:**
> Sorry. Should have made myself clearer. By 'critical data', I mean stuff such as photos, music, documents, etc. At the moment, my main hard drive is not partitioned, so everything (including Thunderbird, Firefox and GPass files are on the same drive as Feisty (hd0?). This is why I run the risk of losing them if they are not backed up before I reinstall.

back up your /home directory before you do anything!

---

### Post by vikram on 2007-05-04
I faced this problem when a few updates broke KDE. Fortunately I was saved because I had my home directory in a seperate partition. You should back up the /home directory as I did but I didnt need to restore after a clean install as all my data, KDE preferences, Kmail settings and believe it or not when I restarted firefox after a clean reinstall I got an option to restore my previous session (before the OS reinstall ) which worked !

second thing I recommend is creating an install script based on :
[http://users.piuha.net/martti/comp/ubuntu/install.html](http://users.piuha.net/martti/comp/ubuntu/install.html)

if you use an install script instead of using adept or synaptic bringing your system back on line is a snap.

third thing I recommend is to have backup script to copy major config files into a folder in the home partitionand place a link to the backup script into the /etc/cron.weekly folder so that all your major system config like samba etc can be restored after a clean reinstall.

if you have these in place - you can have scripts to restore your system just that way you had it after a clean install.

hope this helps.

---

### Post by gewitty on 2007-05-05
> **vikram said:**
> You should back up the /home directory.

Thanks for the tips Vikram. I checked your page notes on re-installing Feisty and whilst they are very comprehensive, they may be a bit beyond my current expertise. I'm quite new to Ubuntu and Linux, so command line stuff is still a bit daunting (although I'm learning all the time).

Is there any reason why I should not do a regular install from the disk image, using the graphical guide, and then replace the Home directory with my backup version to recover all my Thunderbird, Firefox and GPass data? I would feel more confident doing it this way, as long as I know it will work.

---

### Post by gewitty on 2007-05-08
I'm all ready to do the clean install, but am still not sure where my Thunderbird emails and address book are stored. Nor have I found where GPass stores its encrypted file of all my passwords, or where Firefox keeps its bookmarks file. 

It was suggested in an earlier post that all this user specific data is kept in the Home directory, but so far I haven't tracked it down, so I'm still reluctant to do the re-install. Can anyone give me an idea of exactly where these files are kept?

---

### Post by TheWizzard on 2007-05-08
if your name is harry, then all your settings are stored somewhere in the directory /home/harry
files for settings are normally stored in hidden files/directories. they start with a dot. e.g. firefox settings are stored in /home/harry/.mozilla/firefox

---

### Post by gewitty on 2007-05-09
Thanks for the info. I have successfully done a clean install and managed to recover all of my email, bookmarks and passwords, just by copying the specific folders back into the Home directory, rather than the entire thing. Things look a lot tidier now!

---

