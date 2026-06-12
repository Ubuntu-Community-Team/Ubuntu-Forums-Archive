---
title: "How can I access /home(/dev/hda2) partition?"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by i-m-p on 2006-10-11
Hi

I've made a /home partition during the installation.
How can I access it? There is a hda1(windows partition) on desktop as well as on Place>Computer so I can access files.
But no hda2.:confused: 

Thanks

---

### Post by Frak on 2006-10-11
You have to mount it yourself, the instructions are in system documentation.

---

### Post by tonyr1988 on 2006-10-11
To mount it, use this:

> sudo mount -t file_system something somewhere

For example, if you want your ext3 /dev/hda2 mounted to /home, use:

> sudo mount -t ext3 /dev/hda2 /home

However, that will only be mounted until you shut down your computer. To make it permanent:

> gksudo gedit /etc/fstab

And add a line for /dev/hda2 (or, if it already exists, edit the line). The file should be self-explanatory. If it's not, feel free to ask questions about it.

---

### Post by meng on 2006-10-11
Hang on a minute - how do you know it's not already mounted?
If you assigned it to the /home mountpoint during installation, it's probably automatically mounted at boot-time. So you access it by going to /home. It is not going to show up separately on your desktop as hda2.
To verify that it is already mounted, you can type this in the terminal:
df -h
and show us the output.

---

### Post by i-m-p on 2006-10-12
Cheers, This is the result of df -h

> Filesystem            Size Used Avail Use% Mounted on
/dev/hda3              15G  2.6G   12G  19% /
varrun                125M   88K  125M   1% /var/run
varlock               125M  4.0K  125M   1% /var/lock
udev                  125M  108K  125M   1% /dev
devshm                125M     0  125M   0% /dev/shm
lrm                   125M   19M  107M  15% /lib/modules/2.6.15-27-386/volatile
/dev/hda2              29G  197M   28G   1% /home
/dev/hda1              25G  1.4G   24G   6% /media/hda1

Also it looks like I can access /dev/hda2 from System>Administration>Disks.
It says that it is accesible and I could browse what's in there. So it looks like it is mounted already doesn't it?

Perhaps what I should know is what the /home partition does or/and how should I use. What it does I thought was I can store any files in the /home
 partition so that next time ,for some reasons, when I want to re-install the system. I don't have to worry about loosing any of my files. Wrong? or many more reasons?
There should be some documentation on the web somewhere. I tried to find it 
 though not succesful so far. If you something please let me know.

One more thing. This is my second instllation of ubuntu. Why this time suddenly ,without anything done, windows /dev/hda1 icon appears on my desktop?

I really appreciate your help.

---

### Post by i-m-p on 2006-10-12
It would be quite nice if I can make -hda2 /home- partition appear on desktop and on Places menu like -hda1 windows- partition does.

---

### Post by BLTicklemonster on 2006-10-12
I have a nice tutorial on mounting listed in my sig.

---

### Post by meng on 2006-10-12
Your df -h confirms that your /dev/hda2 is indeed mounted on /home, and so you read/write to it by reading/writing to /home. I'm going to guess that you've become accustomed to the Windows idea of separate drives, so you're still stuck in that mindset. With Linux, you can mount a partition anywhere in the directory tree, which completely avoids the old Windows (98?) problem when everything went to C:/My Documents by default, devaluing the concept of a D: for data.

Actually, there is a shortcut to Home in Places, and if it isn't already on the desktop it should be easy to put one there. So stop thinking about hda2! Think about home! and thank your lucky stars that you have a separate home partition, it will come in really useful if you ever upgrade/overwrite your root Linux partition.

---

### Post by i-m-p on 2006-10-12
To Meng,

Thanks I didn't notice that my home folder has a home icon on it (or this doesn't matter whether you have a /home partition or not) and I checked the property of my folders in my home directory they are all located in /home partition.

> I'm going to guess that you've become accustomed to the Windows idea of separate drives, so you're still stuck in that mindset. With Linux, you can mount a partition anywhere in the directory tree

Good guess and good explanation about the directroy tree. When I look at property of the home directory in the file system  it is located in the / partition(hda3) then when I open it to look those folders inside and they are located in the /home partion(hda2). Damn! It still 
 baffles me. I've got lots to learn.

I thank for your patient.

---

### Post by bulldog on 2006-10-12
> **i-m-p said:**
> Hi

I've made a /home partition during the installation.
How can I access it? There is a hda1(windows partition) on desktop as well as on Place>Computer so I can access files.
But no hda2.:confused: 

Thanks

Your home folder should use this space automaticly.

If you're not sure go to administration-->disks and select your disk and see if there's a different /home partition.

You should see a / partition and a swap **and** a /home partition.

---

