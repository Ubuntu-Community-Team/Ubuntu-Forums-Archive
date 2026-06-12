---
title: "[SOLVED] What file permissions should I establish in the File Browser?"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by hul on 2007-06-29
I went into the File Browser, and foolishly messed with the file permissions in my home directory by right-clicking on the "/home/hul" folder, going to Properties, and messing with the Permissions tab.  Now I get angry messages at start-up saying the /home/dmrc file or something is being ignored, and I need 644 permissions set . . . So, um, how should I set the permissions to make Ubuntu not angry at me?

Currently the permissions are as such:
```
Owner: hul
Folder Access: Create and access files
File Access: --

Group: hul
Folder Access: Access files
File Access: --

Others
Folder Access: List files only
File Access: --

Execute: Allow executing files as a program (CHECKED)

SELinux context: Unknown
Last changed: Unknown 
```

Furthermore, if I try to change any of these the File Browser freezes up.  What did I mess up?  Thank you!

---

### Post by bikeboy on 2007-06-29
The usual permissions for folders in /home/user are:
Create and delete
Access
Access

Which is equivalent to 755. My suggestion (since you mention a freeze) is to do this through the terminal. Applications > Accessories > Terminal

Firstly, show us what your current exact permissions are in the terminal, just copy and paste this in there.
```
ls -la
```

Once we see that (just to make sure) one simple command should fix things for you.

---

### Post by hul on 2007-06-29
Here's the code:

```
total 31852
drwxr-xr--  33 hul hul     4096 2007-06-29 05:05 .
drwxr-xr-x   3 root  root      4096 2007-06-25 09:13 ..
-rw-r--r--   1 hul hul     1926 2007-06-29 00:36 Atlas Shrugged
-rw-rw----   1 hul hul      856 2007-06-29 02:07 .bash_history
-rw-rw-r--   1 hul hul      220 2007-06-25 09:13 .bash_logout
-rw-rw-r--   1 hul hul     2298 2007-06-25 09:13 .bashrc
drwxr-xr--   7 hul hul     4096 2006-03-05 21:19 comical-0.8
-rw-r--r--   1 hul hul   480270 2007-06-27 19:51 comical-0.8.tar.gz
drwxr-xr--   4 hul hul     4096 2007-06-29 00:46 .comix
drwxr-xr--   4 hul hul     4096 2007-06-27 21:56 .config
-rw-------   1 hul hul       72 2007-06-27 18:42 .cvspass
drwxr-xr--   5 hul hul     4096 2007-06-29 02:07 .dc++
drwxr-xr--   2 hul hul     4096 2007-06-29 05:05 Desktop
-rw-rw----   1 hul hul       26 2007-06-25 13:17 .dmrc
-rw-rw----   1 hul hul       16 2007-06-25 13:17 .esd_auth
lrwxrwxrwx   1 hul hul       26 2007-06-25 09:13 Examples -> /usr/share/example-content
-rw-rw-r--   1 hul hul 28346542 2007-06-26 20:06 family_jewels_full.pdf
drwxr-xr--   2 hul hul     4096 2007-06-26 08:24 .fontconfig
drwxr-xr--   4 hul hul     4096 2007-06-29 05:05 .gconf
drwxr-xr--   2 hul hul     4096 2007-06-29 05:06 .gconfd
-rw-rw----   1 hul hul        0 2007-06-29 05:06 .gksu.lock
drwxr-xr--   3 hul hul     4096 2007-06-25 13:17 .gnome
drwxr-xr--  10 hul hul     4096 2007-06-29 04:10 .gnome2
drwx------   2 hul hul     4096 2007-06-25 13:17 .gnome2_private
drwxr-xr--   3 hul hul     4096 2007-06-26 23:48 .gourmet
drwxr-xr--   2 hul hul     4096 2007-06-26 12:35 .gstreamer-0.10
-rw-------   1 hul hul        0 2007-06-29 01:48 .gtk-bookmarks
-rw-rw-r--   1 hul hul       87 2007-06-25 13:17 .gtkrc-1.2-gnome2
-rw-------   1 hul hul      724 2007-06-29 05:05 .ICEauthority
-rw-r--r--   1 hul hul    17677 2007-06-29 04:09 John's Budget.ods
drwxr-xr--   3 hul hul     4096 2007-06-25 20:55 .kde
drwxr-xr--   8 hul hul     4096 2007-06-27 22:20 linuxdcpp
drwxr-xr--   3 hul hul     4096 2007-06-27 21:56 .local
drwxr-xr--   3 hul hul     4096 2007-06-25 17:06 .macromedia
drwxr-xr--   4 hul hul     4096 2007-06-25 00:13 Manga & Comics
drwxr-xr--   3 hul hul     4096 2007-06-25 20:57 .mcop
-rw-rw----   1 hul hul       31 2007-06-27 19:35 .mcoprc
drwxr-xr--   3 hul hul     4096 2007-06-25 13:17 .metacity
-rw-------   1 hul hul  1416275 2007-06-28 16:04 mikael_computer.pdf
drwxr-xr--   4 hul hul     4096 2007-06-25 17:06 .mozilla
drwxr-xr-- 264 hul hul   114688 2007-03-04 00:28 Music
drwxr-xr--   3 hul hul     4096 2007-06-29 04:10 .nautilus
-rw-rw-r--   1 hul hul  1945600 2007-06-29 04:39 nautilus-debug-log.txt
drwxr-xr--   3 hul hul     4096 2007-06-29 04:09 .openoffice.org2
-rwx------   1 hul hul    22568 2007-06-21 18:47 Passwords.psafe3
-rw-rw-r--   1 hul hul      566 2007-06-25 09:13 .profile
drwxr-xr--   2 hul hul     4096 2007-06-28 07:28 .qt
-rw-------   1 hul hul     4612 2007-06-29 04:09 .recently-used
-rw-r--r--   1 hul hul    13346 2007-06-29 04:58 .recently-used.xbel
-rw-------   1 hul hul     1024 2007-06-27 22:37 .rnd
drwxr-xr--   3 hul hul     4096 2007-06-25 18:58 .scim
-rw-rw-r--   1 hul hul        0 2007-06-25 13:20 .sudo_as_admin_successful
drwxr-xr--   5 hul hul     4096 2007-06-26 20:56 .thumbnails
drwxr-xr--   2 hul hul     4096 2007-06-29 05:05 .Trash
drwxr-xr--   2 hul hul     4096 2007-06-25 13:19 .update-manager-core
drwxr-xr--   2 hul hul     4096 2007-06-25 13:17 .update-notifier
-rw-rw----   1 hul hul      124 2007-06-27 07:44 .Xauthority
drwxr-xr--   2 hul hul     4096 2007-06-25 20:56 .xine
-rw-r--r--   1 hul hul     1095 2007-06-29 05:06 .xsession-errors
```

---

### Post by bikeboy on 2007-06-29
Hmm, I must say that's barely different to what I have, and it should be working. The only difference is that in yours, users who aren't the owner or in the owner's group can't access your folders. Since you're the owner, everything should be fine.

Unless I missed something obvious in there, a different issue could be causing your problem. Would you mind posting the output of 'whoami'?

---

### Post by hul on 2007-06-29
The output of "whoami" is just "hul".

---

### Post by hul on 2007-06-29
OK, for the interested, this is the exact error message I get at start up after typing in my password:

> Users $Home/.dmrc file is being ignored.  this prevents the default session and languages from being saved.  Files should be owned by user and have 644 permissions.  Users $Home directory must be owned by user and not writable by other users.

---

### Post by hul on 2007-06-29
After searching the error message (stupid me for not doing this sooner), I found this:

[http://ubuntuforums.org/showpost.php?p=2340094&postcount=8](http://ubuntuforums.org/showpost.php?p=2340094&postcount=8)

Which solved the problem nicely.

---

### Post by bikeboy on 2007-06-29
Ah, so it's .dmrc in particular. To make the file have the permissions the error asks for, do ```
chmod 644 .dmrc
```

edit: glad you got it fixed, I was away having dinner. It could be a good idea to learn a bit about file ownership/permissions and changing them, a good read is the [Ubuntu wiki on file permissions](https://help.ubuntu.com/community/FilePermissions)

---

