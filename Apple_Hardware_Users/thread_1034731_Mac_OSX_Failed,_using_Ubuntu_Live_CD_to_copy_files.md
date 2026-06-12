---
title: "Mac OSX Failed, using Ubuntu Live CD to copy files"
date: 2009-01-09
forum: Apple Hardware Users
---

### Post by dekz on 2009-01-09
My Mac OSX has a B node error on the HDD and currently won't boot. So I am trying to use Ubuntu 8.10 as a live cd and copy some of the files off to an external HDD. 

I can only access some files and not the OSX created folders of Music, Documents etc.

The userid is 501 i believe. I am trying to change the ubuntu line in /etc/passwd id from 999 to 501, but its now giving me errors and I can't really write back into the file to try and correct it. (permission denied once i wrote change ```
ubuntu:x:999:999 to ubuntu:x:501:501
```).

Can anyone help me with this step and the next few to getting read access to these folders?

and a reboot changes it back to 999

EDIT: I can now access the drives on my Mac HDD but now can't chown -R /media/My\ Passport/ for my external drive.

---

### Post by tiresia on 2009-01-09
1. Open a terminal and run```
gkuso nautilus
```
You will be able to see and copy any file you want, where you want.

2. When you are finished, the files belongs to 'root'. If you can't access them you can change permissions with chown, if you need.

Let us know! :)

---

### Post by cyberdork33 on 2009-01-09
> **dekz said:**
> My Mac OSX has a B node error on the HDD and currently won't boot. So I am trying to use Ubuntu 8.10 as a live cd and copy some of the files off to an external HDD. 

I can only access some files and not the OSX created folders of Music, Documents etc.

The userid is 501 i believe. I am trying to change the ubuntu line in /etc/passwd id from 999 to 501, but its now giving me errors and I can't really write back into the file to try and correct it. (permission denied once i wrote change ```
ubuntu:x:999:999 to ubuntu:x:501:501
```).

Can anyone help me with this step and the next few to getting read access to these folders?

and a reboot changes it back to 999

EDIT: I can now access the drives on my Mac HDD but now can't chown -R /media/My\ Passport/ for my external drive.
the partition is not writable due to the limitations of the HFS+ driver in the Linux kernel and cannot be made writable unless journaling is disabled which can only be done from within OSX.

---

### Post by eddietours on 2009-01-09
maybe you could use applejack am not sure
[http://applejack.sourceforge.net/](http://applejack.sourceforge.net/)

---

