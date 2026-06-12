---
title: "Problem with mounting?"
date: 2005-12-10
forum: Absolute Beginner Talk
---

### Post by Singachea on 2005-12-10
Can anyone explain me briefly what [COLOR="Blue"]mounting[/COLOR] is?

I just know mounting is kinda showing another partition of another os. I followed ubuntuguide.com by the following code:

[COLOR="Red"]sudo mount /dev/hda5 /media/windows/ -t ntfs -o nls=utf8,umask=022[/COLOR]

When i code this, i can see my Windows partition (NTFS). However, when i restart my pc and log in Linux again, i can't see my Windows partition.

Do we have any method to mount that Windows partition forever?

---

### Post by towsonu2003 on 2005-12-10
for the autmounting, try reading this one: [http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

---

### Post by Singachea on 2005-12-10
[QUOTE=towsonu2003]for the autmounting, try reading this one: [http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)[/QUOTE]

Do you mean we should follow this step?



e.g. Assumed that /dev/hda1 is the location of Windows partition (NTFS)
     Local mount folder: /media/windows



[COLOR="Red"]sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab[/COLOR]

Append the following line at the end of file

/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

Save the edited file

---

### Post by towsonu2003 on 2005-12-10
[QUOTE=Singachea]Do you mean we should follow this step?



e.g. Assumed that /dev/hda1 is the location of Windows partition (NTFS)
     Local mount folder: /media/windows



[COLOR="Red"]sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab[/COLOR]

Append the following line at the end of file

/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

Save the edited file[/QUOTE]

oh yes, sorry - after those steps, ```
sudo mount /media/windows
``` one last time, and then your ntfs should get mounted automatically after every boot.

As for mounting: To mount a file system, in computer science, is to make it ready for use by the operating system, typically by reading certain index data structures from storage into memory ahead of time. Devices may be mounted automatically (generally called automounting) depending on the operating system (en.wikipedia.org)

---

### Post by Singachea on 2005-12-10
Hm... sometimes, I just follow the code, but I really don't understand what it means.

For example:


[COLOR="SeaGreen"]sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab

/dev/hda1 /media/windows ntfs nls=utf8,umask=0222 0 0[/COLOR]

I don't understand what [COLOR="Red"]sudo, cp, etc, gedit, umask, nls, utf8[/COLOR] mean...
I would appreciate it if you can explain some of them.

---

### Post by Danielle on 2005-12-10
hi, i followed those steps above yesterday and they worked perfectly. my XP C drive is automatically mounted at boot. :cool: 

just now i did it the other way around - got access to my Ubuntu drives from XP. if you want to try it i used the software from [here](http://www.fs-driver.org/) here's a screenshot of my Ubuntu files from XP with the mouse pointer showing the file system. it's really clever :D 

if you are going to try it make sure you read all the instructions, you have to asign two drive letters - your main Ubuntu drive and the swap partition too, i made the swap z because i don't think i'll be accessing it and the main drive G because i have other partitions :smile: 

BTW mounting means reading some files to gain access to a drive.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

[[IMG]http://img236.imageshack.us/img236/6096/linuxfiles9xy.th.jpg[/IMG]](http://img236.imageshack.us/my.php?image=linuxfiles9xy.jpg)

---

