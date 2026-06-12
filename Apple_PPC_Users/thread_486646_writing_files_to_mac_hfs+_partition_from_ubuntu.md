---
title: "writing files to mac hfs+ partition from ubuntu"
date: 2007-06-28
forum: Apple PPC Users
---

### Post by jaskah on 2007-06-28
hello

all my data files are on another partition than the one os x is on (this is a hfs+ format partition, with journaling off).

when in ubuntu, i would like to be able to read **and** wreite to this this partition. right now, i can only read.
when i try to write to any of my hfs+ partitions (all with journaling off) i get the following message:
¨You do not have permissions to write to this folder.¨

when in os x i can, using ext2fsx, read and write to any of my ubuntu partitions. i don´t know, however, if the user id´s are correct.

in ubuntu i´ve already installed hfsplus and hfsutils, but don´t know how to use these.

i´ve tried following the instructions at this link:
[http://ubuntuforums.org/showthread.php?p=1922676#post1922676](http://ubuntuforums.org/showthread.php?p=1922676#post1922676)

the following command line seems to work:
sudo usermod -u osx-uid ubuntu-username # change Ubuntu UID to 501

but the next does not:
sudo find / -uid old-ubuntu-uid -print0 | xargs -0 chown osx-uid # change file permissions

i get the following in terminal:
find: /proc/7159/task/7159/fd/4: No such file or directory
find: /proc/7159/fd/4: No such file or directory
chown: changing ownership of `/var/cache/restricted-manager/2.6.20-16-powerpc.restricted': Operation not permitted
chown: changing ownership of `/var/crash/_usr_bin_alacarte.1000.crash': Operation not permitted
chown: changing ownership of `/var/crash/_usr_bin_gnome-sound-properties.1000.crash': Operation not permitted
chown: changing ownership of `/usr/share/applications/nvu.desktop': Operation not permitted

many thanks for any help!

jason

---

### Post by jaskah on 2007-07-01
can someone please give me some help on this?!
thanks
jason

---

### Post by Auria on 2007-07-01
This is what i did (maybe not optimal but worked here)

i just opened the files in OS X, selected them, did ,get info', changed permissions so everyone could read them, clicked 'apply to all' and voila all my files had no permission on them.

but i was using an external HD and not a partition so i have no idea if it can behave diffrently

---

### Post by jaskah on 2007-07-01
hi
thanks for your reply.
could you please be more specific as to "changed permissions so everyone could read them"
what does this mean exactly? can you tell me exactly what you changed the positions to for:
--owner
--group
--others
jason

---

### Post by Auria on 2007-07-01
> **jaskah said:**
> hi
thanks for your reply.
could you please be more specific as to "changed permissions so everyone could read them"
what does this mean exactly? can you tell me exactly what you changed the positions to for:
--owner
--group
--others
jason

read and write everywhere... after all that's what you want, to be able to read and write ;) if there are multiple users on your computer this also means however your files are now public

---

### Post by jaskah on 2007-07-01
yes, read and write everywhere...i understand this part. but who has permissions for "owner" (i.e., your user id, administrator, etc) and for "group?"
thanks!

---

### Post by Auria on 2007-07-01
> **jaskah said:**
> yes, read and write everywhere...i understand this part. but who has permissions for "owner" (i.e., your user id, administrator, etc) and for "group?"
thanks!

leave the default it will be okay, because no matter what is there , the field "others" will have read/write access so anyway everyone will be able to write to it.

if you can't change one, switch owner to your user (unlock the little lock if necessary)

---

### Post by jaskah on 2007-07-01
thanks...but i tried all this and it didn't work...
will keep looking for another solution.

---

