---
title: "usd drive copy/paste"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by snake1mi on 2007-04-23
I tried to copy some files and documents from my computer to the external drive, a message came up saying that I couldn't do that, because I don't have the permission or "copyrights" to do so.

Can someone tell me how I can move/copy files from my ubuntu laptop to the usb hd?

---

### Post by dfreer on 2007-04-23
quickest way (may not work): open up the terminal. Type ```
sudo nautilus
```
Find the files you want to copy and paste them in using that window.

If that doesn't work, post what file system you are using on the external HD and post /etc/fstab and /etc/mtab files.

---

### Post by snake1mi on 2007-04-23
Post where?
The external drive format is ntfs. When i used the sudo nautilus command, this came up in the terminal:


(nautilus:570): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.
/home/nova/.gtkrc-2.0:18: error: invalid string constant "my_color", expected valid string constant

And the root folder came up in a new window.

Isn't there any other way?

---

### Post by snake1mi on 2007-04-23
Help?

---

### Post by dfreer on 2007-04-23
post *here*. 
That error message you see in the terminal. you do not need to worry about it.

in terminal, type
```
sudo gedit /etc/fstab
```
Copy everything in that file and paste it into a post on this page.

Do the same thing with /etc/mtab

[EDIT]: You have NTFS? linux can read ntfs, but not write to it unless you install a driver. So the root window will not help, although knowing your /etc/fstab and /etc/mtab files will help us give you the exact commands to install the driver. These links will help (remember, search this thread and google, because more likely than not someone has already had the same problem and solved it):

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)
*make sure to read these steps carefully!*

[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)
*this should help you if you are running feisty, although the above method should work as well*

---

