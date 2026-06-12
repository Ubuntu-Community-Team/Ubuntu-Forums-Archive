---
title: "restore deleted system files"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by bandito40 on 2007-08-17
Hi all,

I am new to Ubuntu and all seams well until I delete a bunch of system files by mistake.  I was trying to move the mysql datadir folder to a larger drive and accently ran the following command **sudo rm -rv /var/lib/mysql**.  Can anyone tell me how to restore the missing files?

Thanks,

Carl

---

### Post by Hobo Joe on 2007-08-17
Have you checked the trash?


There is a program called photorec that will do its best to recover lost files.

```

sudo aptitude install photorec

```

---

### Post by bodhi.zazen on 2007-08-17
You can try re-installing mysql

If you *need* the data, see this link : 

[https://answers.launchpad.net/ubuntu/+question/2178](https://answers.launchpad.net/ubuntu/+question/2178)

---

### Post by bandito40 on 2007-08-17
Unfortunately two of the files in the /var/lib folder that I delete is needed to install Photorec.  I was hoping that there was a command to restore the files form the live cd or something along those lines.

bandito@bandito2:/var/run/mysqld$ sudo aptitude install photorec
Reading package lists... Done
Building dependency tree... Done
E: Could not open lock file /var/lib/aptitude/lock - open (2 No such file or directory)
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "photorec"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
**E: Lists directory /var/lib/apt/lists/partial is missing.**
**E: Could not open lock file /var/lib/apt/lists/lock - open (2 No such file or directory)**
E: Couldn't lock list directory..are you root?

---

### Post by bodhi.zazen on 2007-08-17
Do you have another process like synaptic or add remove programs running ? If so, close them.

Also, first thing you should do is power off. You need to do data recovery attempts from a live CD (or you risk overwriting your files)

---

