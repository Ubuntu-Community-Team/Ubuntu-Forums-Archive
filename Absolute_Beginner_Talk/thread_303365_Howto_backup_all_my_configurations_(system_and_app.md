---
title: "Howto backup all my configurations (system and applications?)"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by jo.angel on 2006-11-20
I need to do a re-install my dapper drake 6.06 , but I do want to keep all the settings and preferences after the re-install.

Ok, so I backed up my home directory, but which files do I nee dto backup up to keep my system and applications configurations? I mean the settings of my shell, the log in window and all the orther nice settings I set up in long hours for all kinds of applications (and system)

So which are these, and , after re-install, can I just copy and overwrite the default with these?

Your help is greatfully appreciated

j

---

### Post by Tomosaur on 2006-11-20
It changes depending on the application. If you did a proper backup of your home directory, then its likely that much of your custom stuff is already backed up, since programs use hidden files there. Type 'ls -a' to see these files.

Other settings may need to be reconfigured unless you can find the specific config file.

---

### Post by xyz on 2006-11-20
[This is just one of the ways to do it...]("http://ubuntuforums.org/showthread.php?t=81311&highlight=backup+windows+drive")

---

### Post by jo.angel on 2006-11-21
Great! And many thanks.
I´ll figure it out.
Greetinx from Gerrmania

Jo

---

### Post by LinuxConvert on 2006-12-02
Hi guys

I have a desktop and a laptop at home, and I recently just reinstalled Ubuntu Edgy on my desktop (via Linux Mint, I really like this project, check it out if you love Ubuntu but dislike having to set up all your multimedia and stuff manually - or even using scripts like Automatix).

Anyway I was wondering if theres a way to copy over all my user settings and all my installed apps (with their respective settings) from my laptop to my desktop without messing with the system stuff (like my hardware configuration, because they are obviously very different hardware).

Any help would be greatly appreciated.

Thanks in advance guys.

---

### Post by quarkhirad on 2006-12-02
Hey if u installd packages by using synaptics then all u do is back up the folder /var/cache/apt/archives/ . This folder /archives contaains all the packages that u download. After installing ur fresh copy of linux just open terminal and type the following command

sudo cd /var/cache/apt/archives/ 
then type
sudo cp -r /media/backup/archives/* .
Note 
1)There is a full stop to denote the destination directory i the present  working directory.
2)/media/backup/archives is where i backed up my archives . Please replace it with the path to the directory in wich u put ur backup of the forlder archives .

---

### Post by LinuxConvert on 2006-12-02
Thanks quarkhirad! Will try that

---

### Post by quarkhirad on 2006-12-07
> **LinuxConvert said:**
> Thanks quarkhirad! Will try that

dear linux convert 
please note that whenever synaptic pakage manager searches whether the packages have been downloaded or not it searches the folder /var/cache/apt/archives. Hence while copying do make sure that your archives go into the folder /var/cache/apt/archives .It should NOT make another folder and hence put your ur archives in /var/cache/apt/archives/archives this will not work.

---

### Post by ]Nbx*cmD[ on 2006-12-07
I recommend using two partitions, one for /home directories and the other for the system (/). This way when you reinstall ubuntu or change to other gnu/linux distributions you'll save both your configs and data :)

---

