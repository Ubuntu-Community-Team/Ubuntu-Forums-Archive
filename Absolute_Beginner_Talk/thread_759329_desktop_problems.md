---
title: "desktop problems"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by SILLAT on 2008-04-19
hey yall  i hav a little problem tht i dont understand .. 
last night i got some updates from ubutu an  as usual i installed them an evry things ok
tonight wen i turn on my pc all of my folders that was in my home folder eg. Music Document, an program files are all spead out over my desktop . . my destop is full of folders like music, gpass,rkhunter and so much more other files that was in my home folder.
when i got to places --> Home folder  i see desktop filesystem music an all them other folder yet still they r on my desk top ...
i didnt copy any of them to my desktop and if i delete any of the folders on my desktop they completely move off the system... why is that so?
anyone kno wat caused this or wat happen can it be fixed

---

### Post by warbread on 2008-04-19
What happens when you make a file on your desktop?  Does it show up in your /home directory?  Also, try creating a file/folder in your /home directory and see if it pops up on your desktop.

---

### Post by SILLAT on 2008-04-19
hey WARBREAD
if i try to create a file in my home directory it goes straight to my desktop ..
you are right about that part... what else shud i do or wat can i do to correct tht

---

### Post by warbread on 2008-04-20
Do an 'ls -al | grep desktop' in your home directory.  Post here what that says.

---

### Post by SILLAT on 2008-04-20
this is wat comes up wen i run the [COLOR="Red"][COLOR="Red"]ls -al[/COLOR][/COLOR] command

$ ls -al
total 4044
drwxr-xr-x 63 tallishumphrey tallishumphrey    4096 2008-04-20 11:16 .
drwxr-xr-x  6 root           root              4096 2008-04-12 22:58 ..
drwx------  4 tallishumphrey tallishumphrey    4096 2008-04-18 20:54 .adobe
drwxrwxrwx  5 tallishumphrey tallishumphrey    4096 2008-02-19 06:34 alarm-clock-0.9.1
drwx------  5 tallishumphrey tallishumphrey    4096 2008-04-18 20:30 .amsn
drwx------  2 tallishumphrey tallishumphrey    4096 2008-04-18 20:30 amsn_received
-rwx------  1 tallishumphrey tallishumphrey  305941 2008-03-14 11:20 ASkin.vlt
-rw-------  1 tallishumphrey tallishumphrey   10696 2008-04-20 11:20 .bash_history
-rw-r--r--  1 tallishumphrey tallishumphrey     220 2008-02-26 15:59 .bash_logout
-rw-r--r--  1 tallishumphrey tallishumphrey    2298 2008-02-26 15:59 .bashrc
drwxr-xr-x  3 tallishumphrey tallishumphrey    4096 2008-02-26 21:13 .cache
drwxr-xr-x  4 tallishumphrey tallishumphrey    4096 2008-04-19 09:44 .clamtk
drwxr-xr-x  8 tallishumphrey tallishumphrey    4096 2008-04-18 22:11 .config
drwx------  2 tallishumphrey tallishumphrey    4096 2008-03-19 23:31 .cups
drwx------  2 tallishumphrey tallishumphrey    4096 2008-03-27 21:05 .dbus-keyrings
-rw-r--r--  1 root           root                 5 2008-04-17 04:57 description-pak
-rw-r--r--  1 tallishumphrey tallishumphrey       0 2008-04-19 08:49 Desktop
-rw-------  1 tallishumphrey tallishumphrey      28 2008-04-20 11:15 .dmrc
drwxrwx---  3 tallishumphrey tallishumphrey    4096 2008-04-19 22:34 Documents
-rw-------  1 tallishumphrey tallishumphrey      16 2008-02-26 21:13 .esd_auth
drwxr-xr-x  4 tallishumphrey tallishumphrey    4096 2008-04-12 21:24 .evolution
drwxr-xr-x  2 tallishumphrey tallishumphrey    4096 2008-04-15 22:36 .fontconfig
drwx------  2 tallishumphrey tallishumphrey    4096 2008-03-30 16:52 .gcjwebplugin
drwx------  4 tallishumphrey tallishumphrey    4096 2008-04-20 11:15 .gconf
drwx------  2 tallishumphrey tallishumphrey    4096 2008-04-20 11:19 .gconfd
drwxr-xr-x  2 tallishumphrey tallishumphrey    4096 2008-04-14 22:23 .gimp-2.4
-rw-r-----  1 tallishumphrey tallishumphrey       0 2008-04-18 21:46 .gksu.lock
drwxr-xr-x  2 tallishumphrey tallishumphrey    4096 2008-04-04 22:37 .gnochm
drwxr-xr-x  3 tallishumphrey tallishumphrey    4096 2008-02-26 21:13 .gnome
drwx------ 14 tallishumphrey tallishumphrey    4096 2008-04-18 23:38 .gnome2
drwx------  2 tallishumphrey tallishumphrey    4096 2008-04-18 20:27 .gnome2_private
drwx------  2 tallishumphrey tallishumphrey    4096 2008-03-21 13:20 .gpass
drwxr-xr-x 13 tallishumphrey tallishumphrey    4096 2008-03-21 13:14 gpass-0.5.1
-rw-r--r--  1 tallishumphrey tallishumphrey       4 2008-03-07 22:52 .gpilotd.pid
drwxr-xr-x  2 tallishumphrey tallishumphrey    4096 2008-02-27 00:30 .gstreamer-0.10
-rw-------  1 tallishumphrey tallishumphrey     233 2008-04-20 11:16 .gtk-bookmarks
-rw-r--r--  1 tallishumphrey tallishumphrey      96 2008-02-26 21:13 .gtkrc-1.2-gnome2
-rwx------  1 tallishumphrey tallishumphrey  198063 2008-03-14 11:20 Heaven.vlt
-rw-r--r--  1 tallishumphrey tallishumphrey    8112 2008-03-12 23:46 HIP-HOP 2008.nlc
-rw-------  1 tallishumphrey tallishumphrey    6852 2008-04-20 11:15 .ICEauthority
drwxr-xr-x  5 tallishumphrey tallishumphrey    4096 2008-03-21 13:35 Ice-Orange
drwxr-xr-x  2 tallishumphrey tallishumphrey    4096 2008-04-18 22:12 .icons
drwxr-xr-x  3 tallishumphrey tallishumphrey    4096 2008-02-26 23:45 .java
drwx------  3 tallishumphrey tallishumphrey    4096 2008-04-14 22:23 .kde
-rw-r--r--  1 tallishumphrey tallishumphrey   85042 2008-04-06 11:31 .libquicktime_codecs
drwxr-xr-x  6 tallishumphrey tallishumphrey    4096 2008-04-19 09:54 .limewire
drwxr-xr-x  5 tallishumphrey tallishumphrey    4096 2008-04-19 09:17 LimeWire
drwxr-xr-x  3 tallishumphrey tallishumphrey    4096 2008-02-26 21:13 .local
drwx------  3 tallishumphrey tallishumphrey    4096 2008-02-26 22:37 .macromedia
drwxr-xr-x  3 tallishumphrey tallishumphrey    4096 2008-02-27 00:32 .mcop
-rw-------  1 tallishumphrey tallishumphrey      31 2008-02-27 00:32 .mcoprc
drwx------  3 tallishumphrey tallishumphrey    4096 2008-02-26 21:13 .metacity
drwx------  3 tallishumphrey tallishumphrey    4096 2008-03-16 14:37 .mozilla
drwx------  3 tallishumphrey tallishumphrey    4096 2008-03-16 14:37 .mozilla-thunderbird
drwxr-xr-x  3 tallishumphrey tallishumphrey    4096 2008-03-13 00:13 Music
drwxr-xr-x  3 tallishumphrey tallishumphrey    4096 2008-04-18 22:09 .nautilus
-rwx------  1 tallishumphrey tallishumphrey  388660 2008-03-14 11:40 neon.vlt
drwx------  2 tallishumphrey tallishumphrey    4096 2008-03-12 23:46 .nero
drwxr-xr-x 15 tallishumphrey tallishumphrey    4096 2008-04-17 04:51 nmap-4.60
drwxr-xr-x  6 tallishumphrey tallishumphrey    4096 2008-03-14 15:59 OOH680_m12_native_packed-1_en-US.9286
-rw-r--r--  1 tallishumphrey tallishumphrey     348 2008-04-06 12:36 .openme.prefs
drwx------  3 tallishumphrey tallishumphrey    4096 2008-04-19 23:27 .openoffice.org2
-rw-r--r--  1 tallishumphrey tallishumphrey     566 2008-02-26 15:59 .profile
drwx------  5 tallishumphrey tallishumphrey    4096 2008-04-19 23:10 .purple
drwxr-xr-x  2 tallishumphrey tallishumphrey    4096 2008-02-27 00:30 .qt
-rw-r--r--  1 tallishumphrey tallishumphrey    8202 2008-03-13 23:15 rap 2008.nlc
-rw-------  1 tallishumphrey tallishumphrey    3829 2008-04-19 22:34 .recently-used
-rw-r--r--  1 tallishumphrey tallishumphrey  150033 2008-04-19 23:20 .recently-used.xbel
drwxr-xr-x  3 tallishumphrey tallishumphrey    4096 2008-02-27 11:10 rkhunter-1.3.2
drwxr-xr-x  2 tallishumphrey tallishumphrey    4096 2008-03-24 11:48 .serpentine
-rw-r--r--  1 tallishumphrey tallishumphrey       0 2008-02-26 21:16 .sudo_as_admin_successful
drwx------  3 tallishumphrey tallishumphrey    4096 2008-03-02 19:33 .supertux2
drwxr-xr-x  2 tallishumphrey tallishumphrey    4096 2008-03-02 19:11 .supertuxkart
drwxr-xr-x  3 tallishumphrey tallishumphrey    4096 2008-03-21 13:37 .themes
drwx------  4 tallishumphrey tallishumphrey    4096 2008-03-01 23:33 .thumbnails
drwx------  6 tallishumphrey tallishumphrey    4096 2008-04-19 08:49 .Trash
drwx------  2 tallishumphrey tallishumphrey    4096 2008-03-10 22:50 .tsclient
-rw-r--r--  1 tallishumphrey tallishumphrey    1456 2008-04-18 23:38 ubuntu-user.php.png
drwxr-xr-x  2 tallishumphrey tallishumphrey    4096 2008-02-26 21:14 .update-manager-core
drwx------  2 tallishumphrey tallishumphrey    4096 2008-04-18 20:27 .update-notifier
drwxr-xr-x  2 tallishumphrey tallishumphrey    4096 2008-04-06 11:32 Video Projects
drwxr-xr-x  2 tallishumphrey tallishumphrey    4096 2008-04-06 15:04 Videos
drwxr-xr-x  4 tallishumphrey tallishumphrey    4096 2008-03-14 22:41 .vlc
drwxr-xr-x 10 tallishumphrey tallishumphrey    4096 2007-09-06 17:00 vmware-server-distrib
drwxr-xr-x  4 tallishumphrey tallishumphrey    4096 2008-04-19 23:20 .wine
drwxr-xr-x  5 tallishumphrey tallishumphrey    4096 2008-04-17 05:43 .wine-doors
-rw-r--r--  1 tallishumphrey tallishumphrey 2592594 2007-07-09 12:30 wine-doors_0.1-1_all.deb
-rw-r--r--  1 tallishumphrey tallishumphrey    5256 2008-04-17 05:26 .wine.stderr.log
-rw-r--r--  1 tallishumphrey tallishumphrey   19311 2008-04-17 05:25 .wine.stdout.log
-rw-------  1 tallishumphrey tallishumphrey     123 2008-04-20 11:15 .Xauthority
drwxr-xr-x  4 tallishumphrey tallishumphrey    4096 2008-04-19 09:45 .xmms
-rw-r--r--  1 tallishumphrey tallishumphrey    1166 2008-04-20 11:16 .xsession-errors
drwxr-xr-x  2 tallishumphrey tallishumphrey    4096 2008-04-17 05:04 .zenmap

---

