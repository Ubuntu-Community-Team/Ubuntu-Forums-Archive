---
title: "start up scripts"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by ant2ne on 2008-03-04
I'm looking to execute the following lines at start up
```
#!/bin/sh
sudo mount -t smbfs //server/share ~/Desktop/MediaShare -o \ user=me,pass=password,uid=me
``` The code will run when executed manually from the command line.
 
putting it in rc.local don't work
[http://ubuntuforums.org/showthread.php?t=585175](http://ubuntuforums.org/showthread.php?t=585175)

/etc/init.d directory & update-rc.d your_script_name defaults
don't work

My Ubuntu Linux Bible is no help. This shouldn't be this hard.

---

### Post by glennric on 2008-03-04
To mount at boot time you shouldn't add or modify a script.  Instead you should modify the file /etc/fstab.  Edit /etc/fstab and add the line
```
//server/share /home/username/Desktop/MediaShare smbfs user,pass=password,uid=1000 0 0
```
You may need to modify the options.  I changed some of what you had because I don't think what you had was valid.  These still may not be quite right.

---

### Post by lloyd_b on 2008-03-04
> **ant2ne said:**
> I'm looking to execute the following lines at start up
```
#!/bin/sh
sudo mount -t smbfs //server/share ~/Desktop/MediaShare -o \ user=me,pass=password,uid=me
``` The code will run when executed manually from the command line.
 
putting it in rc.local don't work
[http://ubuntuforums.org/showthread.php?t=585175](http://ubuntuforums.org/showthread.php?t=585175)

/etc/init.d directory & update-rc.d your_script_name defaults
don't work

My Ubuntu Linux Bible is no help. This shouldn't be this hard.

A question:  When you tried it in rc.local, did you have the "sudo" in front of the mount command?  If so, try it again without the sudo (since the init scripts are run by root, it's not necessary).

One other note: your mount point is "~/Desktop/MediaShare".  Do you *really* want this thing mounted under "/root/Desktop/MediaShare"? (since init runs as root, the "~" represents root's home directory, which is "/root").  Perhaps that should be "/home/me/Desktop/MediaShare"? (I'm guessing that "me" is your regular username).

Lloyd B.

---

### Post by glennric on 2008-03-04
lloyd_b:  read my post above.  The proper way to mount a filesystem is with fstab.  Not by modifying or adding scripts.  I have also addressed your other statements in my post.

---

### Post by ant2ne on 2008-03-09
> **lloyd_b said:**
> One other note: your mount point is "~/Desktop/MediaShare".  Do you *really* want this thing mounted under "/root/Desktop/MediaShare"? (since init runs as root, the "~" represents root's home directory, which is "/root").  Perhaps that should be "/home/me/Desktop/MediaShare"? (I'm guessing that "me" is your regular username). Yes, I know where I want it mounted.

---

