---
title: "I don't know why I am getting this message."
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by ICUR2Ys on 2007-06-15
Immediately after logging in I get this message:

"User's $Home/.dmrc file is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  User's $Home directory must be owned by user and not writable by other users."

I know about /home I don't know about $Home.  I did an ls -la, the results follow:

dace@dace-desktop:~$ ls -la
total 1747412
drwxrwxrwx 40 dace dace       4096 2007-06-15 10:16 .
drwxr-xr-x  4 root root       4096 2007-06-07 08:02 ..
-rwxrwxrwx  1 root root          0 2007-06-07 10:03 1
drwxrwxrwx  2 dace dace       4096 2007-06-12 11:29 .abook
drwxrwxrwx 24 dace dace       4096 2007-06-12 19:21 .amaya
drwxrwxrwx  2 dace root       4096 2007-06-13 07:25 .automatix
-rwxrwxrwx  1 dace dace     255544 2007-06-07 09:50 automatix2_1.1-4.5-7.04feisty_i386.deb
-rwxrwxrwx  1 root root 1785144650 2007-06-10 11:06 backup.tgz.old
-rwxrwxrwx  1 dace dace       8120 2007-06-12 11:32 Barb.odt
-rwxrwxrwx  1 dace dace       5008 2007-06-15 08:34 .bash_history
-rwxrwxrwx  1 dace dace        220 2007-06-07 08:02 .bash_logout
-rwxrwxrwx  1 dace dace       2298 2007-06-07 08:02 .bashrc
drwxrwxrwx  3 dace dace       4096 2007-06-07 14:36 .config
-rwxrwxrwx  1 dace dace         61 2007-06-13 06:35 .DCOPserver_dace-desktop__0
lrwxrwxrwx  1 dace dace         38 2007-06-13 06:35 .DCOPserver_dace-desktop_:0 -> /home/dace/.DCOPserver_dace-desktop__0
drwxrwxrwx  2 dace dace       4096 2007-06-13 05:55 Desktop
-rw-r--r--  1 dace dace         26 2007-06-07 08:08 .dmrc           <this is the file of interest
drwxrwxrwx  3 dace dace       4096 2007-06-13 10:41 Documents
-rwxrwxrwx  1 dace dace     410860 2007-06-12 14:24 envy_0.9.5-0ubuntu1_all.deb
-rwxrwxrwx  1 dace dace         16 2007-06-07 08:08 .esd_auth
drwxr-xr-x  8 dace dace       4096 2007-06-15 08:35 .evolution
lrwxrwxrwx  1 dace dace         26 2007-06-07 08:02 Examples -> /usr/share/example-content
drwxrwxrwx  2 dace dace       4096 2007-06-07 08:08 .fontconfig
drwxrwxrwx  2 dace dace       4096 2007-06-12 21:45 .gaim
drwxrwxrwx  4 dace dace       4096 2007-06-15 10:20 .gconf
drwxrwxrwx  2 dace dace       4096 2007-06-15 10:27 .gconfd
drwxrwxrwx  8 dace dace       4096 2007-06-11 13:45 .gdesklets
-rwxrwxrwx  1 dace dace          0 2007-06-15 10:17 .gksu.lock
drwxrwxrwx  3 dace dace       4096 2007-06-07 08:08 .gnome
drwxrwxrwx 10 dace dace       4096 2007-06-15 08:35 .gnome2
drwx------  2 dace dace       4096 2007-06-07 08:08 .gnome2_private
drwxrwxrwx  2 dace dace       4096 2007-06-13 07:30 .gstreamer-0.10
-rwxrwxrwx  1 dace dace         86 2007-06-07 08:08 .gtkrc-1.2-gnome2
-rw-------  1 dace dace       1351 2007-06-15 10:16 .ICEauthority
drwxrwxrwx  3 dace dace       4096 2007-06-07 16:35 .kde
drwxrwxrwx  2 dace dace       4096 2007-06-13 20:49 Linuxstuff
drwxrwxrwx  3 dace dace       4096 2007-06-12 20:53 .macromedia
drwxrwxrwx  3 dace dace       4096 2007-06-07 21:29 .mcop
-rwxrwxrwx  1 dace dace         31 2007-06-13 07:26 .mcoprc
drwxrwxrwx  3 dace dace       4096 2007-06-07 08:08 .metacity
drwxrwxrwx  4 dace dace       4096 2007-06-12 20:53 .mozilla
drwxr-xr-x  2 dace dace       4096 2007-06-13 08:39 Music
drwxrwxrwx  3 dace dace       4096 2007-06-15 10:16 .nautilus
drwxrwxrwx  3 dace dace       4096 2007-06-12 11:32 .openoffice.org2
drwxrwxrwx  9 dace dace       4096 2007-06-12 20:31 .opera
-rwxrwxrwx  1 dace dace        566 2007-06-07 08:02 .profile
drwxrwxrwx  2 dace dace       4096 2007-06-07 16:35 .qt
-rwxrwxrwx  1 dace dace        872 2007-06-12 11:32 .recently-used
-rw-r--r--  1 dace dace      12704 2007-06-14 09:29 .recently-used.xbel
-rwxrwxrwx  1 root root          2 2007-06-11 07:13 resolv.conf
drwxrwxrwx  3 dace dace       4096 2007-06-07 18:40 .sane
drwxrwxrwx  2 dace dace       4096 2007-06-07 09:58 .serpentine
-rwxrwxrwx  1 dace dace    1503232 2007-06-12 16:23 SteamInstall_ATI.msi
drwxrwxrwx  2 dace dace       4096 2007-06-09 22:26 .stellarium
-rwxrwxrwx  1 dace dace          0 2007-06-07 08:11 .sudo_as_admin_successful
-rwxrwxrwx  1 dace dace         16 2007-06-11 07:38 test
-rwxrwxrwx  1 dace dace          9 2007-06-11 07:36 test~
drwxrwxrwx  4 dace dace       4096 2007-06-07 15:58 .thumbnails
drwxrwxrwx  3 dace dace       4096 2007-06-07 20:27 .tomboy
-rwxrwxrwx  1 dace dace       1887 2007-06-07 20:27 .tomboy.log
drwxrwxrwx  3 dace dace       4096 2007-06-13 06:44 .Trash
drwxrwxrwx  2 dace dace       4096 2007-06-07 08:08 .update-manager-core
drwxrwxrwx  2 dace dace       4096 2007-06-07 08:08 .update-notifier
drwxrwxrwx  2 dace dace       4096 2007-06-07 22:43 .wapi
drwxrwxrwx  4 dace dace       4096 2007-06-13 20:44 .wine
-rwxrwxrwx  1 dace dace        123 2007-06-13 05:51 .Xauthority
drwxrwxrwx  3 dace dace       4096 2007-06-13 07:35 .xine
-rw-r--r--  1 dace dace       4906 2007-06-15 10:20 .xsession-errors
dace@dace-desktop:~$ 

I think I own it and that the permissions are correct.  What am I misunderstanding?

---

### Post by newlinux on 2007-06-15
maybe this will help.
[http://ubuntuforums.org/showthread.php?t=371052](http://ubuntuforums.org/showthread.php?t=371052)

I had this problem way back... But I don't remember exactly what I did. i think changing permissions on that file and on my homedir did it.

---

### Post by ICUR2Ys on 2007-06-15
Thanks I will read up on it didn't think about permissions on my home directory.  Thanks I appreciate your help

---

### Post by dreadlord_chris on 2007-06-15
You permission aren't correct for your home folder (btw $HOME is the environment variable that = your home folder, ie /home/dace). According to your ls output:
**drwxrwxrwx 40 dace dace 4096 2007-06-15 10:16 .** show your $HOME is writable by *everyone* - this is not good.
```

chmod -hR o-w ~

```
This will turn off the write perms for *others* for your home folder & all its contents.

---

### Post by ICUR2Ys on 2007-06-15
Thanks for the info I hadn't thought about permissions for /home I was just looking at the file.

It is all squared away now.  My thanks to all that have helped me.  I appreciate your guidance.

---

