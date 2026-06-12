---
title: "Denied access to my own HDD - ouch!"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by u.b.u.n.t.u on 2006-06-02
Using the "Disks Manager" I want to browse my 2nd HDD but I am told it doesn't belong to me. Ubuntu says that I do not have permission to view the contents. It is my XP NTFS data HDD.

How can I access my HDD?

Thanks.

---

### Post by Jagot on 2006-06-02
Read this:

[http://help.ubuntu.com/starterguide/C/ch05.html](http://help.ubuntu.com/starterguide/C/ch05.html)

---

### Post by u.b.u.n.t.u on 2006-06-02
The HDD is mounted. 

"according to mtab, /dev/hdb1 is mounted on /tmp/disks-conf-hdb1"

That confirms it. I need read/write/execute permissions.

Thanks.

---

### Post by mcduck on 2006-06-02
[QUOTE=u.b.u.n.t.u]The HDD is mounted. 

"according to mtab, /dev/hdb1 is mounted on /tmp/disks-conf-hdb1"

That confirms it. I need read/write/execute permissions.

Thanks.[/QUOTE]
It's mounted, but it's not mounted with correct permissions.. The link in second post tells you how to do that ;)

edit: sure you know that writing to NTFS is not actually suported in Linux? It's possible, with some experimental apps, but if data on that partition has any value I wouldn't risk it..

---

### Post by u.b.u.n.t.u on 2006-06-02
Hi,

I did this:

"sudo mkdir /media/windows 
sudo mount /dev/hda1 /media/windows/ -t ntfs -o umask=0222"

I don't know what else to do. I have only used Ubuntu for about a week.

I don't want to write data on my NTFS HDD. I want to move all the data files over to my ubuntu HDD. Then format the NTFS to Reiser or ext3 and then  move the data back again. Data - my documents, music etc.

Thanks.

---

### Post by u.b.u.n.t.u on 2006-06-02
I typed "mount" in ther terminal.

"/dev/hdb1 on /tmp/disks-conf-hdb1 type ntfs (rw)"

Does that state that I should be able to read and write to it?

---

### Post by CompShrink on 2006-06-02
try:

sudo mount /dev/hda1 /media/windows/ -t ntfs -o umask=0222 uid=USERNAME

replace USERNAME with your username (what you log in as). I don't have any problems with reading NTFS myself. You could try this:

sudo gedit /etc/fstab

and then make sure the line for your NTFS partition looks like this:

/dev/hdb1       /media/windows  ntfs    defaults        0       0

I don't have any problems personally with the defaults. After doing this, make sure /media/windows exists, type:

sudo umount /dev/hdb1
sudo mount -a 

the -a mounts everything as it is written in your fstab.
if you still have problems, try:

gksudo nautilus

and then see if you can read it that way. Not a perminate solution, but it would tell us why you can't read it.

---

### Post by Ben Sprinkle on 2006-06-02
LMAO i had this same problem wit me usb hard drive anyway to write to it you have to have the ext3 or reiserfs extension insted of ntfs because ntfs is **read-only** this is your problem just edit ur partitions and make ext3 or resierfs one 8)

---

### Post by Jagot on 2006-06-02
[QUOTE=Goat Spirit]LMAO i had this same problem wit me usb hard drive anyway to write to it you have to have the ext3 or reiserfs extension insted of ntfs because ntfs is **read-only** this is your problem just edit ur partitions and make ext3 or resierfs one 8)[/QUOTE]

It's his Windows XP partition from which he needs to retrieve data.  If he were to convert the partition to ext3 or reiserfs then he would lose the data he wants to get from it.

---

### Post by u.b.u.n.t.u on 2006-06-02
Thankyou CompShrink and Jagot.

:rolleyes: @ Goat Spirit re reforming my HDD with my valuable data on it. (Thanks away lol).

I made a work around solution - moved the HDD onto an XP box and networked it from ubuntu. After I finish transfering everything over I will put it back and format it as either ext3 or resier4 (the latest and the best?).

Not ideal I know but I needed my computer working. I was going to move across later but now my main box is ubuntu. It is a nice feeling. I had 3 boxes with XP, then it was 2, and now just one left. 

Ubuntu is really fine eye candy and you can tell it has a lot of quality. Made from love and not love of money. I am amazed that 6.10 will be released in October. Talk about being spoilt.

The learning curve is steep but I have notes which means I only need to learn something once. I will need to do something with XP later for games but that will be dedicated as a games operating system and nothing else. An XP-Box instead of an X-Box :-D

---

### Post by Ben Sprinkle on 2006-06-02
ye what i meant in my message was u use like acronis disk director or summit and resize ur windows partitioon, then make a reiserfs or ext3 partition while still having xp partition, then log on ubuntu and copy ur files ur need from xp partition to ext3 or reiserfs partition then delete/whatever to ur xp drive

its simple as that :mrgreen:

---

### Post by CompShrink on 2006-06-02
[QUOTE=Goat Spirit]ye what i meant in my message was u use like acronis disk director or summit and resize ur windows partitioon, then make a reiserfs or ext3 partition while still having xp partition, then log on ubuntu and copy ur files ur need from xp partition to ext3 or reiserfs partition then delete/whatever to ur xp drive

its simple as that :mrgreen:[/QUOTE]
He mentioned that he **can't even read** the NTFS hard drive. Helping out people is useful, but try to read carefully.

Glad you got it working, yeah having multiple computers makes it a lot easier.

---

