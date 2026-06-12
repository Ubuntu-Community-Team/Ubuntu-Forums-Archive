---
title: "Multiple questions (GRUB, device mounting...)"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by hito1 on 2006-04-25
Ok, I just installed the Dapper beta through the espresso install, and have a few (MANY) problems and doubts:

1. My previous WindowsXP instalation doesn't appear on GRUB menu, I searched the forum and discovered I can manually add it, but the code used differs from post to post, so I'd like to know if there is a more correct one:

```
title Microsoft Windows XP Home Edition
root (hdx,y) 
savedefault 
chainloader +1
```
or
```
title        Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1
```
or even another?

My winxp is in hda1 (fat32), my Ubuntu is in hdc1 (ext3).


2. My second disk - hdc - is formated (used gparted) like this: 
hdc1 (ext3) 
hdc2 (swap) 
hdc3 (fat32)

Ubuntu automatically mounts hdc3, but the name given is very strange (made screenshot, I don't know how to write that :) ): 
[IMG]http://i67.photobucket.com/albums/h284/hitoregistro/Captura_da_tela-1.png[/IMG]

[edit: screenshot seems to be tiny, the name is: ___>____ ]

is that a problem?


3. My /etc/fstab says hda1 and hdc3 are mounted with the umask=007, will I have problems with that? should I change to umask=000 as stated at the ubuntuguide.org?


4. I can't find gparted since I installed Ubuntu, a bug in my instalation??


5. Automatix or easyUbuntu work under Dapper beta? If so, can we select the desired changes in Automatix?


That's it for now :). Thanks in advance! BTW, I liked it!

---

### Post by enopepsoo on 2006-04-25
[QUOTE=hito1]
4. I can't find gparted since I installed Ubuntu, a bug in my instalation??


5. Automatix or easyUbuntu work under Dapper beta? If so, can we select the desired changes in Automatix?
[/QUOTE]

4. just use synaptic or sudo apt-get install gparted

5. they should work fine.

---

### Post by Sutekh on 2006-04-26
[QUOTE=hito1]Ok, I just installed the Dapper beta through the espresso install, and have a few (MANY) problems and doubts:

1. My previous WindowsXP instalation doesn't appear on GRUB menu, I searched the forum and discovered I can manually add it, but the code used differs from post to post, so I'd like to know if there is a more correct one:

...

My winxp is in hda1 (fat32), my Ubuntu is in hdc1 (ext3).
[/quote]
 - The first one should be fine.  GRUB has a different numbering system,  instead of /dev/hda, /dev/hdc2, for example, that contain letters, GRUB uses a numbering system, (hd0,0), (hd2,1).

 - The numbering starts at 0, so /dev/hda1 should be (hd0,0).  You can double-check, by listing the contents of the device.map.
```
cat /boot/grub/device.map
```
 - If you see a line like
```
(hd0) /dev/hda
``` - Then you are good to use (hd0,0) in the Windows entry.

[QUOTE=hito1]
2. My second disk - hdc - is formated (used gparted) like this: 
hdc1 (ext3) 
hdc2 (swap) 
hdc3 (fat32)

[edit: screenshot seems to be tiny, the name is: ___>____ ]

is that a problem?
[/quote]
 - No its not a problem.  I would say that is a character encoding issue.  Since the partition is FAT, I would suggest you check your /etc/fstab entry to see if it includes the option in bold
```
/dev/hdc3   /media/somefiles   vfat   **iocharset=utf8**,umask=007   0   0
```
 - If you make any changes use
```
sudo umount /dev/hdc3
sudo mount -a
```to affect the changes
[QUOTE=hito1]
3. My /etc/fstab says hda1 and hdc3 are mounted with the umask=007, will I have problems with that? should I change to umask=000 as stated at the ubuntuguide.org?
[/quote]
 - The way the **umask** option works, is to set the permission bits by removing them from full access.  

 - The first number corresponds to the mode of access granted to the owner of the mount point.  

 - The second number corresponds to the mode of access granted to the group owner of the mount point.  

 - The third number corresponds to the level of access granted to everyone else.

 - Each umask bit is made up of a value corresponding to read access, write   access and execute access.  Read is worth 4, write 2 and execute 1.

 - Thus a umask bit equal to 7 (4+2+1) means that all permissions are *removed*.   A umask bit equal to 2, for example, means that write permissions (write=2) are removed.  A umask bit equal to 0 means that no permissions are removed.

Hope that's clear. :D
[QUOTE=hito1]
4. I can't find gparted since I installed Ubuntu, a bug in my instalation??
[/quote]
 - GParted isn't installed by default.  **enopepsoo's** post will get that installed for you.
[QUOTE=hito1]
5. Automatix or easyUbuntu work under Dapper beta? If so, can we select the desired changes in Automatix?[/quote]
 - No Automatix for Dapper yet, I think that it is planned.

 - Easy Ubuntu has a [Dapper version](http://easyubuntu.freecontrib.org/get.html), but I think it is like a beta version, for testing only.

 - In the meantime, if you can't get what you need from the [Ubuntu Wiki - Restricted Formats](wiki.ubuntu.com/RestrictedFormats) page, then try this multimedia script for Dapper.

[Ubuntu Forums -  A little multimedia script for y'all!](http://ubuntuforums.org/showthread.php?t=138889)
[QUOTE=hito1]
That's it for now :). Thanks in advance! BTW, I liked it![/QUOTE]
Glad to hear it!

I think Dapper is rocking at this current point, and will only get better as we head towards the final release.

---

### Post by hito1 on 2006-04-26
First, thanks! :)

[QUOTE=Sutekh]- The first one should be fine.[/quote]
So, I shouldn't include the 'makeactive' line?

[QUOTE=Sutekh] - No its not a problem.  I would say that is a character encoding issue.  Since the partition is FAT, I would suggest you check your /etc/fstab entry to see if it includes the option in bold
```
/dev/hdc3   /media/somefiles   vfat   **iocharset=utf8**,umask=007   0   0
```[/quote]
there is 'utf8', should it be 'iocharset=utf8'?

[QUOTE=Sutekh]Hope that's clear. :D[/quote]
Yep! Thanks!

[QUOTE=Sutekh]
 - GParted isn't installed by default.  **enopepsoo's** post will get that installed for you.

 - No Automatix for Dapper yet, I think that it is planned.

 - Easy Ubuntu has a [Dapper version](http://easyubuntu.freecontrib.org/get.html), but I think it is like a beta version, for testing only.

 - In the meantime, if you can't get what you need from the [Ubuntu Wiki - Restricted Formats](wiki.ubuntu.com/RestrictedFormats) page, then try this multimedia script for Dapper.

[Ubuntu Forums -  A little multimedia script for y'all!](http://ubuntuforums.org/showthread.php?t=138889)[/quote]
Thanks again!

---

### Post by uzi09 on 2006-04-26
[QUOTE=Sutekh] - The way the **umask** option works, is to set the permission bits by removing them from full access.  

 - The first number corresponds to the mode of access granted to the owner of the mount point.  

 - The second number corresponds to the mode of access granted to the group owner of the mount point.  

 - The third number corresponds to the level of access granted to everyone else.

 - Each umask bit is made up of a value corresponding to read access, write   access and execute access.  Read is worth 4, write 2 and execute 1.

 - Thus a umask bit equal to 7 (4+2+1) means that all permissions are *removed*.   A umask bit equal to 2, for example, means that write permissions (write=2) are removed.  A umask bit equal to 0 means that no permissions are removed.

Hope that's clear. :D
[/QUOTE]

Oh hey, that's awsome. I knew how to set file permissions using numbers, and I had also copy/pasted peoples commands they provided to mount hard drives using umask, but I didn't understand how it worked.

It's as clear as day now! Thanks so much!

uzi

---

### Post by Sutekh on 2006-04-26
[QUOTE=hito1]
So, I shouldn't include the 'makeactive' line?
[/quote]I don't think its necessary, so no.

[QUOTE=hito1]
there is 'utf8', should it be 'iocharset=utf8'?
[/quote]
I'm not sure there is any difference.  Give it a try and see what happens, it won't hurt the partition.

What do you think it should say?  Does it require any special characters that you are aware of? 

If it still doesn't work then maybe there you need to install a font package to recognise them.  I'm really not sure though.



[QUOTE=uzi09]Oh hey, that's awsome. I knew how to set file permissions using numbers, and I had also copy/pasted peoples commands they provided to mount hard drives using umask, but I didn't understand how it worked.

It's as clear as day now! Thanks so much!

uzi[/QUOTE]
No problem!  Better to understand what you are doing than just copying and pasting.

---

### Post by hito1 on 2006-04-27
Thanks!

[QUOTE=Sutekh]
What do you think it should say?  Does it require any special characters that you are aware of? 
[/QUOTE]

Gparted made that partition out of 0, when I was using the liveCD.

---

### Post by Sef on 2006-04-27
> - No Automatix for Dapper yet, I think that it is planned.

Yes, it is planned. It is scheduled to be released when Dapper goes gold (1 June.)

---

