---
title: "How to move a file from an OS to another?"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by VoXoM on 2007-01-01
Say I saved something on Linux and want it on Windows?

---

### Post by kepos on 2007-01-01
boot windows and install ext3 drivers for windows

---

### Post by VoXoM on 2007-01-01
Care to explain a little more please?

---

### Post by meng on 2007-01-01
[www.fs-driver.org](www.fs-driver.org)

---

### Post by kepos on 2007-01-01
> Care to explain a little more please?

Using ntfs under linux to write is not advised, because it is not secure and you could lose data (in most cases no, but you might be the lucky one). However, using ext2 or ext3 partitions on windows is much safer. So upgrading windows kernel to understand linux partitions will do the job. consult the following page:
[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)
download that program and install it on windows. Then you will be able to see linux partitions on windows, and also transfer files between them. Remember that all your personal files on linux partition are in direcotry /home/yourusername

And, when you install these driver, and try to acces linux swap partition he will say that partition is not formated, and will ask you would you like to do that now. DON'T DO IT!!!!! Don't acces that parition at all. There is nothing useful there.
Anything else?

---

### Post by VoXoM on 2007-01-01
NVM, i got it. thanks.

---

### Post by VoXoM on 2007-01-01
First time I installed everything I tried by myself and formatted 1 drive by mistake. Now I have 4 drives, 1 for normal windows, 1 for linux, and 2 others are useless, how can i remove them? sorry if thats dumb.

---

### Post by Tenicus on 2007-01-01
I assume you mean partition and not drive.

To delete a partition, you should be able to use the gnome partition device.
Its under System -> Admin-> Gnome Partition Editor

Be sure not to delete the wrong partitions

---

### Post by hoges on 2007-01-01
Wow, I never realised you could do this in xp. Good pickup kepos!

---

### Post by VoXoM on 2007-01-01
> **Tenicus said:**
> I assume you mean partition and not drive.

To delete a partition, you should be able to use the gnome partition device.
Its under System -> Admin-> Gnome Partition Editor

Be sure not to delete the wrong partitions

Theres no "Gnome Partition Editor" in System -> Admin

---

### Post by debiannerd on 2007-01-01
> **VoXoM said:**
> Say I saved something on Linux and want it on Windows?

Many Options

Get a USB key, format it FAT32... there u go
Have a FAT32 partition / or NTFS why not!
Save it on an FTP server

---

### Post by kepos on 2007-01-01
> Theres no "Gnome Partition Editor" in System -> Admin
It is aveilable only in version 6.04 and lower because it was unstable. i'm not shure how we are supposed to do that now :(

but if you have dualboot with xp, do it from there. start -> control pannel -> administrative tools -> disk or something like that, i don't remember any more.

> Have a FAT32 partition

bad idea. FAT32 don't supports files larger than 2GB.

---

### Post by inkybutton on 2007-01-01
Right, I think you need to install it :) People just assume what they have is what everyone has.

To install it: (this is the graphical way of installing it, I hate geeks who think everyone needs to use terminal)

1. Open System > Administration > Synaptic Package Manager
2. Type in your password
3. Click on "search", enter "gparted", then press enter.
4. Right click on the option "gparted", select "Mark for Installation", then click on "Apply" on the toolbar.
5. Click "Apply"
6. Wait until it says "Installed gparted", close the window and exit Synaptic Package Manager.
7. Click on System -> Admin-> Gnome Partition Editor

If the above doesn't work, try the geeky (but fast) version.
1. Open Applications > Accessories > Terminal.
2. Type in sudo apt-get install gparted
3. Type in password.
4. Follow onscreen instruction.

Kk done. Anymore questions just ask.

---

### Post by debiannerd on 2007-01-01
> **kepos said:**
> It is aveilable only in version 6.04 and lower because it was unstable. i'm not shure how we are supposed to do that now :(

but if you have dualboot with xp, do it from there. start -> control pannel -> administrative tools -> disk or something like that, i don't remember any more.



bad idea. FAT32 don't supports files larger than 2GB.

Duh...

because you've got doc files > 2GB... u can still chunk them

---

### Post by debiannerd on 2007-01-01
> **inkybutton said:**
> Right, I think you need to install it :) People just assume what they have is what everyone has.

To install it: (this is the graphical way of installing it, I hate geeks who think everyone needs to use terminal)

1. Open System > Administration > Synaptic Package Manager
2. Type in your password
3. Click on "search", enter "gparted", then press enter.
4. Right click on the option "gparted", select "Mark for Installation", then click on "Apply" on the toolbar.
5. Click "Apply"
6. Wait until it says "Installed gparted", close the window and exit Synaptic Package Manager.
7. Click on System -> Admin-> Gnome Partition Editor

If the above doesn't work, try the geeky (but fast) version.
1. Open Applications > Accessories > Terminal.
2. Type in sudo apt-get install gparted
3. Type in password.
4. Follow onscreen instruction.

Kk done. Anymore questions just ask.

guys.. seriously what is it with the GUI

apt-get install gparted

geeeez

---

### Post by meng on 2007-01-01
> **debiannerd said:**
> guys.. seriously what is it with the GUI
apt-get install gparted
geeeez
Or for the non-debian users of Ubuntu:
sudo apt-get install gparted
geeeeez :D

---

### Post by kepos on 2007-01-01
thanks inkybutton.

> because you've got doc files > 2GB... u can still chunk them
It is easier if you don't have to worry how large your files will be. And i'm using torrents and video editing tools, which often results with files larger than 2GB.

Ofcourse, if that is not your case, it will be simplier to use FAT.

---

### Post by ron999 on 2007-01-01
Hi
I thought that they had removed GParted from System > Administration because it was supposed to be run from a CD.
I've now installed it, but it won't let me alter the partitions. There are padlocks on all the drives.
What gives? :-k

---

### Post by meng on 2007-01-01
It's better to download the latest GParted Live CD and use that to repartition.

---

### Post by rocknrolf77 on 2007-01-01
> **ron999 said:**
> Hi
I thought that they had removed GParted from System > Administration because it was supposed to be run from a CD.
I've now installed it, but it won't let me alter the partitions. There are padlocks on all the drives.
What gives? :-k

You can't access the partitions if they are mounted.

---

### Post by ron999 on 2007-01-01
> **rocknrolf77 said:**
> You can't access the partitions if they are mounted.

Yes, that figures.
Thanks :) :cool:

---

