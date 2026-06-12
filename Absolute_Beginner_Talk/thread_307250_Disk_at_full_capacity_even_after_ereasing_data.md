---
title: "Disk at full capacity even after ereasing data"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by solracarevir on 2006-11-26
hi, I have the following issue, just a few hours after installing Beagle my hard disk was at full capacity (a small disk, only 10 Gb) quickly I imagined the guilty was beagle so i made a search, exactly, the .beagle folder was taking 6.6Gb so I erased the folder and un-installed beagle, but the disk keeps reporting that it have only 50mb available
```

carlos@wonder:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             8.9G  8.4G   49M 100% /
varrun                315M  100K  315M   1% /var/run
varlock               315M     0  315M   0% /var/lock
procbususb             10M  132K  9.9M   2% /proc/bus/usb
udev                   10M  132K  9.9M   2% /dev
devshm                315M     0  315M   0% /dev/shm
lrm                   315M   18M  298M   6% /lib/modules/2.6.17-10-generic/volatile

```

can anyone help with this issue?

---

### Post by ThrashJazzAssassin on 2006-11-26
Have you tried emptying the deleted items folder?

---

### Post by taurus on 2006-11-26
Are you sure you have deleted the .beagle directory?  Sometimes, you also need to empty the Trash Can as well...

---

### Post by solracarevir on 2006-11-26
yes i emptied my trash can, and my disk still appears as full capacity
Here is a screenshot of my Disk usage analyzer utility
[IMG]http://static.flickr.com/112/306651031_c925ebbe6d_o.png[/IMG]

---

### Post by taurus on 2006-11-26
Maybe you need to clean out the cache from apt-get/aptitude.

```
sudo aptitude clean
-or-
sudo apt-get clean
```
Then, look in your $HOME directory to see which directory is taking up a lot of space with

```
du
```

---

### Post by solracarevir on 2006-11-26
cleaned the aptitude/apt-get cache, now i have 628 mb free on my disk.  after runing the command   "du"
 this are the major offenders, all of them small quantities compared to almost 6 Gb of disk lost on the twilight zone...
```

171100  ./Music
65832   ./Pictures
257492  .

```

still wondering what happens.....

---

### Post by AgenT on 2006-11-26
There are two ways of "deleting" files:
1) real delete
2) trash can
You delete files for real when you use the command rm. There is a "Delete" option in GNOME menu which uses rm. If you use "Move To Trash"  then all your files are moved to ~/.Trash/ which means they are NOT deleted. You have to "Empty Trash" which just uses rm to delete everything in the trash folder.

When you are using du, it is best to use:
```
du -sh 
```
That will give you more information as well as making the information easier to understand.

And you should know that 2.1GB for /usr sounds about right. Here is my output:
```
sudo du -sh /usr
2.1G    /usr
```

Details:
```
sudo du -sh /usr/*
130M    /usr/bin
1.3M    /usr/games
13M     /usr/include
954M    /usr/lib
76K     /usr/lib64
284K    /usr/local
8.9M    /usr/sbin
930M    /usr/share
81M     /usr/src
308K    /usr/X11R6
```

---

### Post by Irony on 2006-11-26
Type;

[PHP]gksudo nautilus[/PHP]

and then delete anything in;

[PHP]/root/.Trash[/PHP]

and

[PHP]/.Trash-root[/PHP]

---

### Post by solracarevir on 2006-11-26
The real issue here is that the .beagle folder was consuming 6 GB of space and after deleting it the disk did freed up that space and there is no trace of any beagle file on the computer
```

carlos@wonder:~$ du -sh /usr/*
89M     /usr/bin
200K    /usr/etc
40K     /usr/games
740K    /usr/include
880M    /usr/lib
100K    /usr/local
5.9M    /usr/sbin
759M    /usr/share
81M     /usr/src
28K     /usr/X11R6

```
i have ubuntu installed on a small disk (8.8 Gb) so 6 Gg missing is an issue. Just wondering, could it be a bug of the filesystem I'm using? (ext3)

---

### Post by taurus on 2006-11-26
What's the output of this command then?

```
ls -la
```
p.s.  Ext3 is not the problem.  The problem is you have way too many mp3s in ~/Music and something else is taking up the space...

---

### Post by Irony on 2006-11-26
Did you do what I said?

---

### Post by bollix47 on 2006-11-26
Try unchecking Allocated space and see if that's your difference.

---

### Post by solracarevir on 2006-11-26
ls -la
```

total 680
drwxr-xr-x 35 carlos carlos   4096 2006-11-26 14:42 .
drwxr-xr-x  3 root   root     4096 2006-11-25 13:07 ..
drwx------  8 carlos carlos   4096 2006-11-25 15:02 .amsn
drwx------  2 carlos carlos   4096 2006-11-25 15:01 amsn_received
drwxr-xr-x  4 carlos carlos   4096 2006-11-25 18:03 .aMule
drwxr-xr-x  2 carlos root     4096 2006-11-26 14:46 .automatix
drwxr-xr-x  2 carlos root     4096 2006-11-26 14:45 .automatix_bleeder
-rw-------  1 carlos carlos    142 2006-11-26 11:49 .bash_history
-rw-r--r--  1 carlos carlos    220 2006-11-25 13:07 .bash_logout
-rw-r--r--  1 carlos carlos    414 2006-11-25 13:07 .bash_profile
-rw-r--r--  1 carlos carlos   2227 2006-11-25 13:07 .bashrc
drwx------  4 carlos carlos   4096 2006-11-25 15:41 .config
drwxr-xr-x  2 carlos carlos   4096 2006-11-26 12:43 Desktop
-rw-------  1 carlos carlos     26 2006-11-25 13:40 .dmrc
drwxr-xr-x  2 carlos carlos   4096 2006-11-25 15:45 Documents
-rw-------  1 carlos carlos     16 2006-11-25 13:40 .esd_auth
drwxr-xr-x  5 carlos carlos   4096 2006-11-25 15:47 .exaile
-rw-r--r--  1 carlos carlos 483359 2006-11-25 15:16 .fonts.cache-1
drwx------  4 carlos carlos   4096 2006-11-26 10:51 .gconf
drwx------  2 carlos carlos   4096 2006-11-26 14:48 .gconfd
drwxr-xr-x  8 carlos carlos   4096 2006-11-26 10:59 .gdesklets
-rw-r-----  1 carlos carlos      0 2006-11-26 14:44 .gksu.lock
drwxr-xr-x  3 carlos carlos   4096 2006-11-25 13:40 .gnome
drwx------ 11 carlos carlos   4096 2006-11-26 11:27 .gnome2
drwx------  2 carlos carlos   4096 2006-11-25 13:40 .gnome2_private
drwxr-xr-x  2 carlos carlos   4096 2006-11-25 15:35 .gstreamer-0.10
drwxr-xr-x  2 carlos carlos   4096 2006-11-26 14:43 .gtkpod
-rw-r--r--  1 carlos carlos     88 2006-11-25 13:40 .gtkrc-1.2-gnome2
-rw-------  1 carlos carlos    159 2006-11-26 10:51 .ICEauthority
drwx------  3 carlos carlos   4096 2006-11-25 15:16 .macromedia
drwx------  3 carlos carlos   4096 2006-11-25 13:40 .metacity
drwx------  3 carlos carlos   4096 2006-11-25 13:41 .mozilla
drwxr-xr-x  4 carlos carlos   4096 2006-11-26 03:37 Music
drwxr-xr-x  3 carlos carlos   4096 2006-11-26 10:49 .nautilus
drwx------  2 carlos carlos   4096 2006-11-25 15:46 PDF
drwxr-xr-x  3 carlos carlos   4096 2006-11-26 12:43 Pictures
-rw-------  1 carlos carlos    567 2006-11-26 03:37 .recently-used
-rw-r--r--  1 carlos carlos   1826 2006-11-26 03:37 .recently-used.xbel
drwxr-xr-x  2 carlos carlos   4096 2006-11-26 11:06 .serpentine
drwx------  3 carlos carlos   4096 2006-11-26 04:30 .songbird
-rw-r--r--  1 carlos carlos      0 2006-11-25 13:41 .sudo_as_admin_successful
drwx------  5 carlos carlos   4096 2006-11-26 03:37 .thumbnails
drwxr-xr-x  3 carlos carlos   4096 2006-11-25 15:38 .tomboy
drwx------  2 carlos carlos   4096 2006-11-26 04:05 .Trash
drwxr-xr-x  2 carlos carlos   4096 2006-11-25 13:46 .update-manager
drwx------  2 carlos carlos   4096 2006-11-25 13:40 .update-notifier
drwxr-xr-x  2 carlos carlos   4096 2006-11-26 10:52 .wapi
-rw-------  1 carlos carlos    117 2006-11-26 10:51 .Xauthority
drwxr-xr-x  2 carlos carlos   4096 2006-11-25 18:59 .xine
-rw-r--r--  1 carlos carlos  15058 2006-11-26 14:46 .xsession-errors


```

---

### Post by solracarevir on 2006-11-26
Irony, I just did what you said, that was the issue, i never thought, beagle would  store data also in root, issue solved, thaks to all of you guys! that's what makes ubuntu different, the comunity, thanks to all of you again:p:KS:KS

---

