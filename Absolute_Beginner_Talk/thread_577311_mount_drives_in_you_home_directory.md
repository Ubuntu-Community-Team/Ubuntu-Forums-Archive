---
title: "mount drives in you home directory"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by lordViN on 2007-10-16
greetings 

I have a 120GB HDD (hda) and a second 250GB HDD (hdb), 

In the (hda) I have 3 partitions one as (/)  and the others as /home and the last one as swap.
and I want to use the 250GB HD for media purposes.

my question is if I can mount the second drive (250GB HDD) in the /home directory? for example as /home/user/videos or  /home/user/downloads?


I'm asking all this because I want to use SAMBA for sharing the 250GB and part of the 120GB hdd in my LAN, but for what I know SAMBA only works along with the users in the /home directory.

thanks beforehand

---

### Post by skymera on 2007-10-16
create that dir.

mkdir /home/USER/videos

sudo mount /dev/sda* /home/USER/videos

etc

---

### Post by lordViN on 2007-10-16
so it is possible then.

but it's recommended ? 
what happens If I format the /home directory, it will format the hdb directories as well?

---

### Post by skymera on 2007-10-16
no, its only mounted there.

if you want you can just unmount it :wink:

---

### Post by lordViN on 2007-10-16
I understand now, 

Last question, if I want to mount the partition for the next Ubuntu start in the /home/user/videos, I need to modify the /etc/fstab right, or is done with other method?

---

