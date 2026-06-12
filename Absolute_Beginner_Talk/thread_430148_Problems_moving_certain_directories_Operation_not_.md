---
title: "Problems moving certain directories: Operation not allowed?"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by Lucifiel on 2007-05-01
Yeah, I've been moving various directories across from 1 partition to another. From media/sda5/hdc2 to /media/hdc2 , that is. 

Most of these directories were transferred properly while so far, 2 directories had problems(I deleted one of them, though as I didn't need it). For that one remaining directory, I basically got an error message: Error "Operation not permitted" while moving "/media/sda2...codings.dir".

So, what I tried to do was run "sudo chmod -Rvf 755 /media/sda5/hdc2" and "sudo chown -Rvf Hidan /media/sda5/hdc2" on the entire directory which contained all my sub-directories since I thought it might be a permission error.  

Then, I tried to move the directories again, in Nautilus. However, that failed and so I tried using the "mv" as well as "mv -f" commands in Terminal. As expected, I got plenty of error messages like the ones below:

1) "mv: cannot create symbolic link `/media/hdc2/home backup/Lucifiel 26th April 2007/Desktop/gimp-2.2.14/modules/.libs/libcdisplay_gamma.la': Operation not permitted

2) mv: inter-device move failed: `/media/sda2/hdc2/home backup/Lucifiel 26th April 2007/desktop' to `/media/hdc2/home backup/Lucifiel 26th April 2007/desktop'; unable to remove target: Is a directory

3) mv: setting permissions for `/media/hdc2/home backup/.azureus/torrents/here1(Complete)/here1.mkv': Operation not permitted

and many other error messages about time, inter-device move  and other stuff, Errr... so, am I not allowed to move my home directories or something? Man, I feel guilty for posting 2 threads within 48 hours.

---

### Post by Lucifiel on 2007-05-02
Hmmm, this problem seems to occur with other folders used by Ubuntu programs like Ktorrent, etc. Now, I'm getting errors like "cannot create symbolic link". But, isn't a symbolic link = a shortcut that points towards a file or folder? 

If I'm trying to move a folder over, why do I need symbolic links then?

---

### Post by nanotube on 2007-05-02
what is the filesystem type on both the source and destination dir? if there is a fat32 involved in there, it may have trouble dealing with permissions and links and stuff.

also, for the error files (e.g. /media/hdc2/home backup/.azureus/torrents/here1(Complete)/here1.mkv), try an "ls -ald" for all parts of the hierarchy, just to see if there's anything weird with permissions at any point in there. 

also, if move fails, try a "cp" first, and if that's successful, then just delete the source after the cp is done.

well, there're some ideas for you. :)

---

### Post by kvonb on 2007-05-02
.....or

use an su nautilus.  Press <alt><f2> and type "gksu nautilus" in the box, that's what I usually do :)

---

### Post by Lucifiel on 2007-05-02
> **nanotube said:**
> what is the filesystem type on both the source and destination dir? if there is a fat32 involved in there, it may have trouble dealing with permissions and links and stuff.

also, for the error files (e.g. /media/hdc2/home backup/.azureus/torrents/here1(Complete)/here1.mkv), try an "ls -ald" for all parts of the hierarchy, just to see if there's anything weird with permissions at any point in there. 

also, if move fails, try a "cp" first, and if that's successful, then just delete the source after the cp is done.

well, there're some ideas for you. :)

Well, the volume being copied to is fat32. The source folder is: ntfs, i believe.

Copying doesn't work at all. I get a lot of error messages as well. 

Oh my dear gods, what a mess. Linux can't create ntfs volumes while Windows can only read certain types of volumes, right?  T___T;; 

In "home\ backup", "ls -ald" gives "drwxrwxrwx 1 root root 0 2007-04-29 05:19 .".

In ".azereus", "ls-ald" gives "drwxrwxrwx 1 root root 0 2007-04-21 03:01 ." 

Errr so what am I supposed to look for?

---

### Post by Lucifiel on 2007-05-02
> **kvonb said:**
> .....or

use an su nautilus.  Press <alt><f2> and type "gksu nautilus" in the box, that's what I usually do :)

Ahhh, I tried gksudo nautilus but gksu is not gksudo , right?

Edit: Oh wait, using gksu nautilus also gave me the same problems. @_@ Goodness, why is it that I keep needing help? How I wished Ubuntu didn't give me so many issues. And a temp solution is to eat tons of chocolate while reading some manga. :P

---

### Post by nanotube on 2007-05-02
> **Lucifiel said:**
> Well, the volume being copied to is fat32. The source folder is: ntfs, i believe.

Copying doesn't work at all. I get a lot of error messages as well. 

Oh my dear gods, what a mess. Linux can't create ntfs volumes while Windows can only read certain types of volumes, right?  T___T;; 

In "home\ backup", "ls -ald" gives "drwxrwxrwx 1 root root 0 2007-04-29 05:19 .".

In ".azereus", "ls-ald" gives "drwxrwxrwx 1 root root 0 2007-04-21 03:01 ." 

Errr so what am I supposed to look for?

heh well, you found it - the stuff's owned by root, not by your user. the fat32 filesystem does not support any kind of permissions, or symlinks, so that's what basically is screwing you up.

windows can read ext3 filesystems, with an add-on extension (google it). so i would recommend that you convert your target fat32 drive to ext3, and then you should not have any problems moving this stuff over. 

or you could try "gksudo nautilus" (this is the "standard way" of getting a root filebrowser. not 'gksu' (not sure from what you wrote whether you have tried it already).

edit: chocolate and manga: good combo :)

---

### Post by Lucifiel on 2007-05-02
> **nanotube said:**
> heh well, you found it - the stuff's owned by root, not by your user. the fat32 filesystem does not support any kind of permissions, or symlinks, so that's what basically is screwing you up.

windows can read ext3 filesystems, with an add-on extension (google it). so i would recommend that you convert your target fat32 drive to ext3, and then you should not have any problems moving this stuff over. 

or you could try "gksudo nautilus" (this is the "standard way" of getting a root filebrowser. not 'gksu' (not sure from what you wrote whether you have tried it already).

edit: chocolate and manga: good combo :)

LOL... okay, that's good. :)  'Cos I got a little afraid that ubuntu was screwing up. :p

Well, gksudo nautilus didn't work. Think that option's out for now and no way am I gonna spend some more time trying to combat a raging bull. :p

Chocolate and manga? Hell yeah!!!! Gokusen rocks! :D 

Oh thank you everyone for your gracious support. :)

---

