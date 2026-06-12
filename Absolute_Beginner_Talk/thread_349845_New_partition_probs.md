---
title: "New partition probs"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by V-600 on 2007-01-30
I have successfully repartitioned my hard disk following instructions from 

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

to create a new partition for my home directory.  Now i have hda1 (25gig) with everything except /home and hda3 (50gig) with /home

However as far as i can make out all my programs are looking for their settings in my folder now on the new partition. Is there anyway i can tell them "en masse" to replace hda1 with hda3 for their settings. Or have i got it all wrong in my head. Still trying to understand filesystem as it is different from windows.

---

### Post by rocknrolf77 on 2007-01-30
The settings is in the /home folder as hidden folders. Like this :  ".gnome2"   etc. Files or folders with a "." in front of them are hidden and can be shown by pressing CTRL-H in nautilus.

The files and folders beneath /home are system files and you need super user priveligies too access them. (This is one of the things that makes linux safer)

/media is mounted disks  Just to name a couple of things.

/etc are more important setting files that you should know how to tweak. Like the xorg.conf and stuff

---

### Post by mangoti on 2007-01-30
Are you having any issue at all? If yes, please describe. How did you make the new partition your home directory? You shouldnt have problems if your new partition is mounted at the right place (/home)and the content of your old home is properly transfered to it.

---

### Post by V-600 on 2007-01-31
Basically  i would like to know how to get all my old emails back into evolution.

When i start it now i got the wizard that appears when you start it for the first time. From what people have said i guess it would be something to do with /home/.evolution folder but i have no idea what it would be.

Many thanks for any advise

---

### Post by mangoti on 2007-01-31
you simply need to have the .evolution folder moved to your new home. If you followed the instructions from the howto, you should have everything set. apparently, there is something wrong.

please post the output of these commands:
```
ls -al ~
less /etc/fstab
```

---

### Post by V-600 on 2007-01-31
nathan@nathan-desktop:~$ ls -al ~
total 380
drwxr-xr-x 52 nathan nathan  4096 2007-01-31 11:16 .
drwxr-xr-x  4 root   root    4096 2007-01-30 23:26 ..
drwx------  2 nathan nathan  4096 2007-01-30 23:37 .AbiSuite
-rw-r--r--  1 nathan nathan    43 2007-01-30 23:37 .aspell.en.prepl
-rw-r--r--  1 nathan nathan    22 2007-01-30 23:37 .aspell.en.pws
drwxr-xr-x  2 nathan root    4096 2007-01-30 23:26 .automatix
drwxr-xr-x  9 nathan nathan  4096 2007-01-30 23:33 .azureus
-rw-------  1 nathan nathan  3615 2007-01-31 01:03 .bash_history
-rw-r--r--  1 nathan nathan   220 2007-01-30 23:26 .bash_logout
-rw-r--r--  1 nathan nathan   414 2007-01-30 23:26 .bash_profile
-rw-r--r--  1 nathan nathan  2227 2007-01-30 23:26 .bashrc
-rw-------  1 nathan nathan     0 2007-01-30 23:33 .civserver_history
drwxr-xr-x  5 nathan nathan  4096 2007-01-30 23:26 .config
drwxr-xr-x  2 nathan nathan  4096 2007-01-30 23:26 CV stuff
drwxr-xr-x  3 nathan nathan  4096 2007-01-31 11:15 Desktop
-rw-------  1 nathan nathan    24 2007-01-30 23:26 .dmrc
drwxr-xr-x  4 nathan nathan  4096 2007-01-30 23:37 .dvdcss
-rw-------  1 nathan nathan    16 2007-01-30 23:26 .esd_auth
drwxr-xr-x  8 nathan nathan  4096 2007-01-31 01:14 .evolution
lrwxrwxrwx  1 nathan nathan    26 2007-01-30 23:26 Examples -> /usr/share/example-content
drwxr-xr-x  2 nathan nathan  4096 2007-01-30 23:37 .fonts
-rw-r--r--  1 nathan nathan  1301 2007-01-31 11:16 .fonts.cache-1
-rw-r--r--  1 nathan nathan   516 2007-01-30 23:37 .fonts.conf
drwxr-xr-x  2 nathan nathan  4096 2007-01-30 23:33 .freeciv
drwxr-xr-x  6 nathan nathan  4096 2007-01-30 23:37 freeloader
drwx------  4 nathan nathan  4096 2007-01-31 11:17 .gaim
drwx------  4 nathan nathan  4096 2007-01-31 10:41 .gconf
drwx------  2 nathan nathan  4096 2007-01-31 11:17 .gconfd
drwxr-xr-x 21 nathan nathan  4096 2007-01-30 23:33 .gimp-2.2
-rw-r-----  1 nathan nathan     0 2007-01-31 00:39 .gksu.lock
drwxr-xr-x  3 nathan nathan  4096 2007-01-30 23:26 .gnome
drwx------  9 nathan nathan  4096 2007-01-31 11:15 .gnome2
drwx------  2 nathan nathan  4096 2007-01-30 23:26 .gnome2_private
drwx------  2 nathan nathan  4096 2007-01-30 23:26 .gnupg
drwxr-xr-x  2 nathan nathan  4096 2007-01-30 23:26 .gpilotd
-rw-r--r--  1 nathan nathan     4 2007-01-30 23:26 .gpilotd.pid
drwxr-xr-x  2 nathan nathan  4096 2007-01-30 23:26 .gstreamer-0.10
-rw-r--r--  1 nathan nathan    88 2007-01-30 23:26 .gtkrc-1.2-gnome2
drwxr-xr-x  3 nathan nathan  4096 2007-01-30 23:37 GTTR stuff
-rw-r--r--  1 nathan nathan    32 2007-01-30 23:37 .hwdb
-rw-------  1 nathan nathan  5270 2007-01-31 10:41 .ICEauthority
drwxr-xr-x  2 nathan nathan  4096 2007-01-30 23:26 .icons
drwxr-xr-x  3 nathan nathan  4096 2007-01-30 23:33 .java
drwx------  2 nathan nathan  4096 2007-01-30 23:26 .kde
-rw-------  1 nathan nathan   160 2007-01-30 23:37 .kderc
-rw-r--r--  1 nathan nathan  1730 2007-01-30 23:33 .key.gpg.asc
-rw-------  1 nathan nathan    35 2007-01-30 23:37 .lesshst
drwxr-xr-x  3 nathan nathan  4096 2007-01-30 23:26 .local
drwxr-xr-x 18 nathan nathan  4096 2007-01-30 23:33 .lyrics
drwx------  3 nathan nathan  4096 2007-01-31 00:12 .macromedia
drwxr-xr-x  3 nathan nathan  4096 2007-01-30 23:33 .mcop
-rw-------  1 nathan nathan    31 2007-01-30 23:33 .mcoprc
drwx------  3 nathan nathan  4096 2007-01-30 23:55 .metacity
drwx------  3 nathan nathan  4096 2007-01-30 23:56 .mozilla
drwxr-xr-x 38 nathan nathan  4096 2007-01-30 23:33 Music
drwxr-xr-x  3 nathan nathan  4096 2007-01-31 01:14 .nautilus
-rw-r--r--  1 nathan nathan   937 2007-01-30 23:26 .nvidia-settings-rc
drwx------  2 nathan nathan  4096 2007-01-30 23:33 .openoffice.org2
drwxr-xr-x  3 nathan nathan  4096 2007-01-30 23:33 .parallelrealities
drwxr-xr-x  5 nathan nathan  4096 2007-01-30 23:26 Photos
drwxr-xr-x  4 nathan nathan  4096 2007-01-30 23:26 pics
drwxr-xr-x  2 nathan nathan  4096 2007-01-30 23:33 .qt
-rw-------  1 nathan nathan 34643 2007-01-30 23:33 .realplayerrc
-rw-------  1 nathan nathan 24639 2007-01-31 01:08 .recently-used
-rw-r--r--  1 nathan nathan  6579 2007-01-31 11:14 .recently-used.xbel
-rw-r--r--  1 nathan nathan   237 2007-01-31 01:11 .registry
-rw-r--r--  1 nathan nathan   360 2007-01-30 23:33 .slune
-rw-r--r--  1 nathan nathan     0 2007-01-30 23:26 .sudo_as_admin_successful
drwxr-xr-x  2 nathan nathan  4096 2007-01-30 23:37 .supertuxkart
drwxr-xr-x  2 nathan nathan  4096 2007-01-30 23:26 .themes
drwx------  4 nathan nathan  4096 2007-01-31 00:02 .thumbnails
drwx------  2 nathan nathan  4096 2007-01-31 11:15 .Trash
drwxr-xr-x  2 nathan nathan  4096 2007-01-30 23:26 .update-manager
drwx------  2 nathan nathan  4096 2007-01-30 23:26 .update-notifier
drwxr-xr-x  3 nathan nathan  4096 2007-01-30 23:37 .vlc
drwxr-xr-x  2 nathan nathan  4096 2007-01-30 23:26 .wapi
drwxr-x---  2 nathan nathan  4096 2007-01-30 23:33 .wormux
drwxr-x---  2 nathan nathan  4096 2007-01-30 23:33 .xarchive
-rw-------  1 nathan nathan   125 2007-01-31 10:41 .Xauthority
drwx------  2 nathan nathan  4096 2007-01-30 23:33 .xchat2
-rw-------  1 nathan nathan   192 2007-01-30 23:37 .xcompmgrrc
drwxr-xr-x  2 nathan nathan  4096 2007-01-30 23:33 .xine
-rw-r--r--  1 nathan nathan  2496 2007-01-31 11:16 .xsession-errors

and

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=af5bcf45-8547-4545-affb-b4bb22b8f046 /               ext3    defaults,errors=
remount-ro 0       1
# /dev/hda5
UUID=8c907ff6-8be3-4e85-ac00-4988eadeeb9a none            swap    sw              
0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda3 /home ext3 nodev,nosuid 0 2

---

### Post by V-600 on 2007-01-31
I don't know if this helps anyone but playing Gnometris i found that my settings had reverted to default...but it had kept my high scores. I would have assumed they were stored in the same place so why one remained and the other didn't is beyond me.

---

