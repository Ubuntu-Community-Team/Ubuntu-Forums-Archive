---
title: "Trouble with permission to access stuff"
date: 2005-11-29
forum: Absolute Beginner Talk
---

### Post by buspital on 2005-11-29
I have just installed for the first time and I'm curious as to why i am unable to access certain things, for example when i double click on hda1 on the desktop i get an error message saying i don't have permission to access it. Is this normal?
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=3967&stc=1&d=1133268409[/IMG]
Sorry if I'm being incredibly stupid here, but i don't know where to start working these things out.

---

### Post by frodon on 2005-11-29
Could you post your fstab file here, I would like to check if it's not the problem. To open it use this command in a terminal : ```
sudo gedit /etc/fstab
```

---

### Post by buspital on 2005-11-29
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

```

this what you mean?

---

### Post by frodon on 2005-11-29
ok, i suggest to modify the file like that : ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
**/dev/hda1 /media/hda1 ntfs nls=utf8,user,auto,umask=0222 0 0**
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
```Then do a "sudo mount -a" or reboot if this command don't change anything.

PS : With NTFS file system you will get only read access with linux because there isn't any good NTFS write support for the moment.

---

### Post by buspital on 2005-11-29
That's got it. Not sure why i wanted to access it now, but thanks very much

---

### Post by HarryMangurian on 2005-11-29
do you mean "mount -a"

I could find no mout.


(I don't even qualify as a newbie yet)

---

### Post by frodon on 2005-11-30
Of course, i will correct the error

thanks ;)

---

### Post by HarryMangurian on 2005-11-30
by the way, your suggested changes to fstab worked great for me.
(after a reboot).

How do folks learn these "inner secrets" for Linux?

Can you recommend a book or two ?
(or even better, on-line resources)

many thanks,

---

### Post by Robgould on 2005-11-30
The best way I have found are the forums.  If you google you will find there are a LOT of linux forums beyond the distribution specific ones.  These forums and the serach function contain more knowledge than I will ever need.

---

### Post by Robgould on 2005-11-30
Another thing to look at are the man pages.
 
try doing
 
man ?
 
or substitue the command you are trying to use in place of the question mark.

---

### Post by frodon on 2005-11-30
Here are some details about fstab options : [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

Do you need more informations ?

---

