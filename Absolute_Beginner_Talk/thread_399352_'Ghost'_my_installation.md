---
title: "'Ghost' my installation?"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by shavenlunatic on 2007-04-02
Hi,

I have finally got Ubuntu working EXACTLY how I want it (well, wine is still sucky for gaming but thats another story).. 

It would be great if I would generate a livecd from my current install so if I need to wipe my PC, i can just boot from my custom livecd and things are back how i want them.

I think I may have read something on this when I first started with ubuntu, but as I was just getting started I thought I'd wait until I could actually get things how I want them before worrying about how to snapshot my system... but following the general theme of my life, now I want this function, I can't find it :rolleyes: 

As its probably painfully aware, I am a bit of a noob when it comes to Linux so the most user-friendly option (if there are options of course) would be prefferable :) 

Thanks in advance

---

### Post by shavenlunatic on 2007-04-02
also:

Someone mentioned making a partition to hold your /home folder.... 

is this along the lines of what i'm looking for?  Is it worth looking into?

---

### Post by gjtoth on 2007-04-02
> **shavenlunatic said:**
> Hi,

I have finally got Ubuntu working EXACTLY how I want it (well, wine is still sucky for gaming but thats another story).. 

It would be great if I would generate a livecd from my current install so if I need to wipe my PC, i can just boot from my custom livecd and things are back how i want them.

I think I may have read something on this when I first started with ubuntu, but as I was just getting started I thought I'd wait until I could actually get things how I want them before worrying about how to snapshot my system... but following the general theme of my life, now I want this function, I can't find it :rolleyes: 

As its probably painfully aware, I am a bit of a noob when it comes to Linux so the most user-friendly option (if there are options of course) would be prefferable :) 

Thanks in advance

I'm sure there are more but, have a look at these:

[http://freshmeat.net/projects/linuxlivescripts/](http://freshmeat.net/projects/linuxlivescripts/)
[http://freshmeat.net/projects/ping_partimage_is_not_ghost/](http://freshmeat.net/projects/ping_partimage_is_not_ghost/)
[http://freshmeat.net/projects/g4l/](http://freshmeat.net/projects/g4l/)

---

### Post by shavenlunatic on 2007-04-02
> **gjtoth said:**
> I'm sure there are more but, have a look at these:

[http://freshmeat.net/projects/linuxlivescripts/](http://freshmeat.net/projects/linuxlivescripts/)
[http://freshmeat.net/projects/ping_partimage_is_not_ghost/](http://freshmeat.net/projects/ping_partimage_is_not_ghost/)
[http://freshmeat.net/projects/g4l/](http://freshmeat.net/projects/g4l/)

thank you..

linuxlive looks complex (at a glance) as its going on about i have to be using certain kernel??? bit scared of this one.. heheh

PING looks like a great idea but you need 2 PC's networked.. i no longer have this.

g4l site is down :(


Looks like I will have to have a play with linuxlive... that looks ideal if i can figure it out... i'll have a hunt for a good looking guide around and post it here if i find one.. for prosperity :)

---

### Post by shavenlunatic on 2007-04-02
> 2)
Build aufs kernel module and squashfs kernel module (optionally patched to support LZMA)
   
The step above is not required if you use precompiled Linux Kernel from this website
   
Install kernel modules to the newly installed distro to /lib/modules/`uname -r`/fs/.
   
Make sure you are running the same kernel you used to compile modules

?

Do i need to do this? i truly have no idea what the hell it's talking about :(

---

### Post by linuxjerk on 2007-04-02
I have been hashing this for many days now. I really haven't found a way to copy the entire hard disk either.
I have tried Gparted, Partimage, read about ghost4 or something. I don't know why you need a FTP???
THis is very frustrating. With win98 I just copy it to another disk with the manufacturers utility.
But of course these don't recognize linux. :confused:

---

### Post by shavenlunatic on 2007-04-02
You would think that in the current climate of people looking for alternative operating systems and chosing linux.. and many people struggling to find their feet, the world would be flooded with "Finally go it working? SNAPSHOT IT!" type software which made sense for new users

I will hopefully get some time tonight to play with linuxlive... but all that jibbering about the kernel stuff just throws me off... I expect there is an easy to read user guide somewhere.. but if you doa search anywhere for "linux live" it returns every page which mentions a linux live cd, so its a tough one to hunt for a guide on :(

I will have a look tonight, but if anyone has any tips/pointers int he meantime they would be GREATLY appreciated!!!!

---

### Post by srt4play on 2007-04-02
My way of doing this is to boot a live cd, install partimage and run it from a terminal.  It asks what to back up and where to back up to, as well as if I want to compress the image or not.

---

### Post by odin1965 on 2007-04-02
Partimage works great for this. You can backup your boot ubuntu partition to a single file which you then burn to a DVD or keep on a separate hard-drive should something bad happen. The only thing you really need that you may not already have is a separate partition from the one being backed up, that you can mount and use to save the image of the partition being backed up. Obviously, you can;t save onto the same partition and back it up at the same time !!!
  I use the system rescue CD, it comes with partimage. Have a look at tyhis thread. Seems complicated, but it's not once you've done it.

[http://ubuntuforums.org/showthread.php?t=287522&highlight=partimage](http://ubuntuforums.org/showthread.php?t=287522&highlight=partimage)

---

### Post by linuxjerk on 2007-04-02
All those still require the disk be unmounted to copy. Try G4U I got it to work on my system.
You can either do floppies or cd.
[http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/)

---

### Post by dannyboy79 on 2007-04-05
sbackup is the best easy fully system backup gui you can find!! I wrote a guide here for checking your sbackup file to make sure your backup is reliable and is correct. i am actaully working right now from my backup system restored. here it is: [http://ubuntuforums.org/showthread.php?t=401425](http://ubuntuforums.org/showthread.php?t=401425)

sbackup is in the repo's but I downloaded and compiled from source as I wanted the latest verison. install instructions will be in either a README or INSTALL file after you extract the source archive. you can get the latest version from sourceforge

---

