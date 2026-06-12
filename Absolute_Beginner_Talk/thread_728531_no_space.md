---
title: "no space"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by theRightNee on 2008-03-18
yeah..so i'm running ubuntu on a 20 GB hard drive (small i know) and i keep on hearing things about how it gets messy when you get low on space...what happens exactly?:confused:

---

### Post by RealPSL on 2008-03-19
It is funny how today we refer to 20GB hard drives as small. Anyway I am not sure I understand your question. However if all you install was Ubuntu from the LiveCD and you do not download new software or generate a lot of data you should have ample storage for a long time. Generally we run out of space when we start processing music and video files or downloading ISO images of other distros.

---

### Post by timjohn7 on 2008-03-20
I'm also running Gutsy with all updates on a 20Gb partition and having downlooaded some new software (Firefox3b4, Opera, Kallery and some other smaller stuff: no music, video or other space hogging data) I am down to 256Mb free!  Performance is down, remaininng space is almost useless, and I am extremely concerned!  I'm on the verge of deleting the WinXP partition whiich would obviously help, but I still need to test some Win software in VirtualBox.
Disk Usage Monitor indicates that numerous full and incremental backups are being made and I have deleted some of those, and I've transferred some large data files (photos and documents) to an ext HDD, but there appears to be something wrong somewhere.
I also get frequent "Low Disk Space" warnings.

Please help!

---

### Post by RealPSL on 2008-03-22
To help you narrow down the source of the problem the following outputs will be helpful.

1. df -h 
2. swapon -s
3. Assuming that you installed under the Ubuntu default of all under / then "sudo du -xk / | sort -rn | head" will help narrow down to the directory what it using all this space.

You can run all the above commands in the terminal.

---

### Post by bruce89 on 2008-03-22
```
sudo apt-get autoclean
```

would clean a lot of space (it deletes all obselete debian package files). Otherwise,

```
sudo apt-get clean
```

would remove all cached debian packages.

Neither of these affect what programs are installed.

---

### Post by tvtech on 2008-03-22
check out the man page for apt and see all the wonders it can do 

in terminal run 

user@localhost:~$man apt-get

read the man pages before executing things!

---

### Post by Berean on 2008-03-22
Alternatively, if you want to increase the partition you have Ubuntu on (without deleting the Windows partition) you could use GParted and resize WITHOUT losing anything.  Hope this helps.

---

### Post by timjohn7 on 2008-03-23
I am quite happy to repartition my Windoze partition having discovered VBox and tested the few Win software packages that are essential to me (no Ubuntu equivalents... no games)
My problem is that running the LiveCD to run GParted, I get the infamous black screen.
Ii had a torrid time installing Ubuntu due to my Intel Video driver on a Fujitsu Siemens laptop and althoughh I found the fix, it was some time ago and I cant remember wwhat I eventuallly did.
If you can help with that....

---

### Post by timjohn7 on 2008-03-23
Thanks for these.  Could you help me cler the obviously large dirs?
Here's the output:

tim@tim-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              19G   18G  117M 100% /
varrun                248M  208K  248M   1% /var/run
varlock               248M     0  248M   0% /var/lock
udev                  248M   80K  248M   1% /dev
devshm                248M     0  248M   0% /dev/shm
lrm                   248M   34M  214M  14% /lib/modules/2.6.22-14-generic/volatile
/dev/sdb1             234G   21G  214G   9% /media/Ext1
/dev/scd0              11M   11M     0 100% /media/cdrom0
tim@tim-laptop:~$ swapon -s
Filename                                Type            Size    Used    Priority
/dev/sda5                               partition       907632  473832  -1
tim@tim-laptop:~$ sudo du -xk / | sort -rn | head
18181014        /
11160800        /root
11160008        /root/.Trash
3388144 /home
3388124 /home/tim
3147320 /root/.Trash/2008-03-13_07.35.46.852823.tim-laptop.ful
2926632 /root/.Trash/2008-03-05_07.35.22.932301.tim-laptop.ful
2849812 /usr
2730264 /home/tim/.VirtualBox
2730092 /home/tim/.VirtualBox/VDI

Thanks

---

### Post by plumstead21 on 2008-03-23
> **timjohn7 said:**
> 11160008        /root/.Trash
There's your problem - 11GB in root's trash directory.  Check there's nothing you need in there and if not, delete the contents (you'll need to use sudo).

Another good way of seeing where all your disk space has gone is to run the Disk Usage Analyzer utility in Ubuntu (in the Accessories menu) on the filesystem.

---

### Post by Berean on 2008-03-23
i don't know how important it is for you to keep Windows, but for the one application I had to keep in XP I chose to run in a virtual machine, and once I knew it worked deleted the Windows partition.  I understand this is not an option for everyone, however.  I use VMware for a theological library (Logos) and then run a smaller (MS) bible application in Wine.  Perhaps you could investigate whether your Windows apps. can run in a virtual machine.  Alternatively, once you've emptied your trash you'll have oodles of space and will perhaps be happy to continue dual booting.  Good luck with whatever your decision.  Regards.

---

### Post by timjohn7 on 2008-03-23
I plan to do exactly that.  I am running VirtualBox 90% successfully... still struggling to get the XP Guest to see my wireless card which is my only Internet connection, and my USB Ext Drive, but the software I need, Working Artist (an Access Database) works fine.
Once I've got the networking sorted out, goodbye dualboot and hello an extra 20Gbs of HDD space.

---

