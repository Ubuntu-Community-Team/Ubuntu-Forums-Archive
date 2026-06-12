---
title: "Tried many things for Fat32 access..."
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by Shaddarr on 2007-02-08
First Post! :) 

Tried Linux about 5 years ago and waited a bit until things got a 'little more user friendly (gui) and an LOVING Ubuntu so far (as the Novice that I am)

I have installed and liked what I saw, but recently spent _hours_ trying all of the helpful suggestions from all you great contributors out there concerning accessing a FAT32 partition on the system..

fstab editing: I have tried (not all at once, over time, as per suggestions):
vfat user users umask=000 umask=077 gid  uid  1000 myname rw auto ... 
in so many combinations, but just can't seem to get access to the other FAT32 partition :confused: 

Running Ubuntu 5.10 (2612) until my Edgy downloads!

Thanks for any other ideas I could try from any of you wonderful experts 
Happy to come aboard

:popcorn: 

~Shad

---

### Post by taurus on 2007-02-08
What partition is your fat32 on?  You want to write to it, right?

---

### Post by meng on 2007-02-08
Maybe you'll have better luck with Edgy.

---

### Post by rocknrolf77 on 2007-02-08
Have a look at [www.ubuntuguide.org](www.ubuntuguide.org) :)

---

### Post by Shaddarr on 2007-02-08
> **taurus said:**
> What partition is your fat32 on?  You want to write to it, right?

hda1, yes I'd like rw access if possible

Responses already! Thanks guys...

Edit: 
There is one drive, partitioned in half
hda1 is fat32
there is a swap and ext3 for ubuntu as well

---

### Post by Shaddarr on 2007-02-08
> **rocknrolf77 said:**
> Have a look at [www.ubuntuguide.org](www.ubuntuguide.org) :)

THanks, that is a GREAT resource (bookmarked!) but their exact commands didn't get it going either.. :-k 

I notice there is a hda1 mount higher up in the fstab (vfat  defaults) that I didn't put in, could they be conflicting? 
The one I am adding to the bottom mounts it as a folder, however, in an attempt to access it

---

### Post by taurus on 2007-02-08
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/hda1   /media/hda1   vfat   iocharset=utf8,umask=000   0   0
```
Save it.  Now, create a new mount point and mount it.

```
sudo mkdir /media/hda1
sudo umount /dev/hda1
sudo mount -a
df -h
```

p.s.  Remove any previous entry for /dev/hda1 in /etc/fstab.

---

### Post by Omnios on 2007-02-08
Hi I have a vfat document drive and have been using this fstab entry for over a year.

```

/dev/hda2       /media/documents     vfat   rw,users,gid=users,umask=000,       0       0

``` /dev/hda2 is the partition /media/documents is the directory you make to mount the partion to in /media. The last part sets up permitions etc that I found to work really well. Also you can use any name for /documents and it will show up in your file systems.

[[COLOR=#D40000]**taurus**[/COLOR]]("http://ubuntuforums.org/member.php?u=43398")  beat me to it lol

 ALso there is a good fstab link in my signature that really helped me out when I just started Linux.

---

### Post by Shaddarr on 2007-02-08
After over 4 hours of trying different combinations, I did it step-by-step from Taurus' instructions and BOOM, I can 'Create Folder'!

I don't know whether it was the 'hda1' (I was using /windows as I thought it didn't matter what it was called, just wanting 'folder' access)
or the previous entry of hda1 (which was put in there auto.) that I removed but... 
Thank You  :grin: 

I may have more questions, but as I learn more (from 'what's hda' to this thread in a matter of hours!) I hope to someday return the help..

Thanks to all who helped, it is all very much appreciated - keep it up!

=D>

---

