---
title: "How do I know if Beagle is working"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by Tzumli_D on 2006-12-31
I'm studying at uni and one of the absolute best things about working with MS XP was that I had Desktop Google installed. I would save all my searches to my hard disc, and then when I needed to pull it all together a search of my PC would bring up lots of relevant information. I've now had Ubuntu for about six months,  and I really miss that facility.
I've been told that Beagle is the thing to use. 
so I did 
:
sudo apt-get install beagle
and it all seemed to work smoothly.

But where is my interface with Beagle? How do I know what it is indexing? I feel :-# :-? :( :confused:  stupid.
It's a small thing, but because I cannot make this happen I still have to rely on my Windows partition, and that is a pain.

---

### Post by tagra123 on 2006-12-31
> **Tzumli_D said:**
> I'm studying at uni and one of the absolute best things about working with MS XP was that I had Desktop Google installed. I would save all my searches to my hard disc, and then when I needed to pull it all together a search of my PC would bring up lots of relevant information. I've now had Ubuntu for about six months,  and I really miss that facility.
I've been told that Beagle is the thing to use. 
so I did 
:
sudo apt-get install beagle
and it all seemed to work smoothly.

But where is my interface with Beagle? How do I know what it is indexing? I feel :-# :-? :( :confused:  stupid.
It's a small thing, but because I cannot make this happen I still have to rely on my Windows partition, and that is a pain.


This link should help

[http://www.wikihow.com/Install-Beagle-on-Ubuntu-Breezy-Badger](http://www.wikihow.com/Install-Beagle-on-Ubuntu-Breezy-Badger)

---

### Post by Tzumli_D on 2007-01-01
I read the article mentioned, but I don't have a file /etc/fstab.
The article is about installing on Breezy Badger, would it still apply?

---

### Post by tagra123 on 2007-01-01
> **Tzumli_D said:**
> I read the article mentioned, but I don't have a file /etc/fstab.
The article is about installing on Breezy Badger, would it still apply?

I have dapper and the how to work great for me.

You better have a file /etc/fstab  (This is the file that mounts the static drives)


try this

From the menu:

Applications - Accessories - Terminal


```
cd /etc
ls -lah fstab

```
you should see something like this

-rw-r--r-- 1 root root 1.6K 2006-12-31 22:29 fstab

next  in the terminal

type

```
sudo gedit /etc/fstab
```

Continue with the how - to

---

### Post by Tzumli_D on 2007-01-03
My fstab does not look anything like the example:
I think I have 4 partitions, as I have a dual boot with MS XP

This is my fstab file:
```
/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=6d6afe6d-c3a9-48ca-9dc2-97323ef317cd /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=07D4-0819  /dell           vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=2E2481B324817E99 /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=36dc5594-5fe0-4383-93c5-e48254d3905d none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```
What should I change?
Anyway how will this tell my system to give me an icon, or interface for when I want to use Beagle?

---

### Post by tagra123 on 2007-01-03
> **Tzumli_D said:**
> My fstab does not look anything like the example:
I think I have 4 partitions, as I have a dual boot with MS XP

This is my fstab file:
```
/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=6d6afe6d-c3a9-48ca-9dc2-97323ef317cd /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=07D4-0819  /dell           vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=2E2481B324817E99 /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=36dc5594-5fe0-4383-93c5-e48254d3905d none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```
What should I change?
Anyway how will this tell my system to give me an icon, or interface for when I want to use Beagle?


edit this line in the /etc/fstab

# /dev/sda4
UUID=6d6afe6d-c3a9-48ca-9dc2-97323ef317cd /               ext3    defaults,errors=remount-ro 0       1


It should look like this when finished
# /dev/sda4
UUID=6d6afe6d-c3a9-48ca-9dc2-97323ef317cd /               ext3    defaults,user_xattr,errors=remount-ro 0       1

save and exit

The above will just help beagle search better. I think what you are doing is asigning it permission.

To use beagle, if you've followed the steps in the how-to.

You should be able to use beagle bye using the menu: Applications > Accessories > Search

Search Is the beagle.

If its not there -- right click on the menu, which will open the menu editor. Place a checkmark next to search and close it.

You can drag item from the menu to the desktop or panel for easier access.

---

### Post by Kabamaru on 2007-02-16
thanks for posting all this information, i really found it helpful.  i installed beagle fine on my computer, but ran into problems with my roommate's computer.  part of the initial problem was that i wasn't sure where to put "user_xattr", as like Tzumli_D the fstab did not look like the initial one shown.  i played around with it, and eventually got it to work--sort of.

for some reason, when i searched using beagle it would only show me files in my mail client and in the "home" folder (but none of the subfolders).  

i ran "beagle-info --status" in the terminal, and it gave me a list that basically consisted of the following:

Maintenance 0 (2/15/2007 11:46:24 PM)
Optimize ThunderbirdIndex
Hold until 2/15/2007 11:56:25 PM)

I kept restarting, trying to put  the ":user_xattr" command in other spots.  i finally left it in the "/" line, as opposed to "/home".  i noticed that every time i restarted, the times changed.  so i thought--why the hell not, i'll wait until after the "hold" time.

and it's working.  i'm going to see what happens when i restart, but i think it'll be okay (i hope).  

does anyone have any idea why there should be a hold time???

---

### Post by Kabamaru on 2007-02-16
i did run into problems when i restarted my computer.  here is a more detailed version of what i think the problem is:

[I]Status: Waiting for next task.

Pending Tasks:
1 Delayed 0 (2/16/2007 12:32:27 AM)
Crawling /home/[specific folder]

2 Delayed 0 (2/16/2007 12:32:28 AM)
Tree Crawler
Pending directories: 74
[/I]

help?  i'm going to try manually removing that folder from the list of places beagle should look.

---

### Post by orionsbelt on 2007-02-16
*(note:  i accidentally posted the two previous posts under my friend's - kabamaru - account.)*

well, i seem to have resolved the issue using a different method.  i went to Applications-->Add/Remove and removed "kerry beagle" and "search" from there.  then i reinstalled them, from the same place.

i don't know what is up with the other method mentioned above, since it worked on the other computer.  however, i am having no trouble with speed and did not have to edit /etc/fstab.

good luck to anyone else having issues, and long live ubuntu.

---

