---
title: "Using same installation of Dapper Drake on two PCs"
date: 2006-08-31
forum: Apple PPC Users
---

### Post by pkiddie on 2006-08-31
Hi all,

I've just recently put the Dapper Drake installation on an external USB drive holding an old 2.5" laptop HD I had lying around, with the intention of being able to use this in two PC's, one at home and one in work. 

Has anyone had any experience with this, or encountered any problems - I forsee one being that I installed Ubuntu onto sdd: on my home PC reflecting its configuration, but the drive numbering will probably change in my work pc... (possibly sda: or sdb:) will this affect Grub booting up Linux? How about cycling the redetection of hardware between my work/home PC, is Ubuntu robust to this?

Any comments would be really appeciated!
Paul :)

---

### Post by Ocxic on 2006-08-31
moving the drive from computer to computer, shouldn't affect your current computers configuration, the drive would most likly br appended to the current drive list. (hda,hdb,hdc are in use 6you new external drive would become hdd etc...)

just be sute to mount and unmount properly, it is very easy to hose a file system but accdentaly/(or in a rush) unplugging it without unmounting, speacially if it's in use at the time.

---

### Post by 3rdalbum on 2006-09-01
You might encounter problems with the drive numbering between PCs, but the showstopper is likely to be the Xorg configuration. Unless the two PCs have the same graphics card, it's probably wisest to set Ubuntu to use the generic "vesa" driver. If you look in the file "/etc/X11/xorg.conf", under the Section Driver part, it will say which driver you are currently using. Change this to "vesa" and hopefully you shouldn't have any problems.

---

