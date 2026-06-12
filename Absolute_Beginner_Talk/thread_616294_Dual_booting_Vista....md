---
title: "Dual booting Vista..."
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by RobotoWorks on 2007-11-18
I have Ubuntu Gutsy and I want to dual boot Windows Vista Ultimate, right now I have 500mb of RAM but I am going to upgrade it to 1.5gigs, is this enough RAM or do I need more?

---

### Post by Skefflock on 2007-11-18
What's your question? If you want to know whether 1,5gigs of RAM is enough for Vista than yes, it is. If you're not going to load it with heavy applications.

---

### Post by RobotoWorks on 2007-11-18
What do you mean by "Heavy applications"?

---

### Post by Skefflock on 2007-11-18
Games, graphic, video editing, I mean everything that needs RAM. I'm not telling that Vista is wasting RAM, but there's lots of people I know complaining about 1gig and even 1,5 onboard with Vista isn't enough for a game which system requirements is 1gig minimum for example. It's just heavy OS by itself. And I've even seen that funny marks on games boxes like 1,5gigs of RAM, but if you're Vista user - go ahead and add 1gig more:)

---

### Post by RobotoWorks on 2007-11-18
Hehe, Im going to dual boot with a .ISO Torrent file, would 2.5 gigs be referabley better?

---

### Post by Skefflock on 2007-11-18
Think so, but again it just depends on what you're going to do with it. If just look around and play with interface and so on, than 1,5 and even 1gig of RAM will be complitely enough for Vista, but if you're hard gamer than yes, 2 or 2,5 will be much better.

---

### Post by RobotoWorks on 2007-11-18
I have Ubuntu Gutsy installed and a want to dual boot Vista Ultimate through live CD, what is a good program to use to dual boot Vista on Ubuntu?

---

### Post by Pumalite on 2007-11-18
Have to install Vista first in the whole drive, then allocate space for Ubuntu with Vista partitioner. Then install Ubuntu.

---

### Post by overdrank on 2007-11-18
> **RobotoWorks said:**
> I have Ubuntu Gutsy installed and a want to dual boot Vista Ultimate through live CD, what is a good program to use to dual boot Vista on Ubuntu?

Are you talking virtual machine again? :confused:

---

### Post by RobotoWorks on 2007-11-18
Well then how do I do that. I installed Ubuntu just a few weeks ago and I have really customized it too my liking.I have Vista Ultimate on Live CD, but I dont want to have to delete Ubuntu in order to use Vitsta, plase is there any solution?

---

### Post by RobotoWorks on 2007-11-18
Not Virtual Box, I actually want to dual boot Vista with my Ubuntu.

---

### Post by Rippie on 2007-11-18
> **RobotoWorks said:**
> Well then how do I do that. I installed Ubuntu just a few weeks ago and I have really customized it too my liking.I have Vista Ultimate on Live CD, but I dont want to have to delete Ubuntu in order to use Vitsta, plase is there any solution?

You cant multi boot with Vista when you have Ubuntu installed first, you will have to do as you got told in the first post to this thread.. :)

Im sorry mate ....

// Rippie

---

### Post by RobotoWorks on 2007-11-18
*Sob* Is there any way to do a data back-up of my Ubuntu files? *Sob*

---

### Post by Pumalite on 2007-11-18
[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
[http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html](http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html)

---

### Post by RobotoWorks on 2007-11-18
Thanx,,,,,link master....

---

### Post by RobotoWorks on 2007-11-18
So are you sure theres no way to dual boot Vista on Ubuntu?

---

### Post by kiepmad on 2007-11-18
It is possible . 
However, you need to install Windows Vista FIRST, and reinstall Ubuntu afterwards.

Otherwise, it's a very tedious process...

First, create a new parition for Windows, then backup ubuntu.
Then install Windows Vista on the new partition.
Boot from ubuntu live cd and install grub.
Configure grub.
Boot into your old ubuntu. You might need to change some values in fstab.

That's roughly what needs to be done, but note, that's not as easy as it sound and note, I am not a expert and have only done this with Windows XP, not with Vista. 

Furthermore, it's advised to have a second PC with internet connection to be able to search for help in case something goes wrong.

Good luck

---

### Post by RobotoWorks on 2007-11-18
Well, thanx for the help:) Finally, I understand that the process wont exactly be a piece of cake, but I have people that can help me.

P.S. I've been to Luxemburg before, and all I have to say is, what a beutiful country!

---

### Post by Duck2006 on 2007-11-18
This mite be what your looking for.

[http://www.eloff.se/tutorials.php?ubuntu_vista_dualboot](http://www.eloff.se/tutorials.php?ubuntu_vista_dualboot)

---

### Post by RobotoWorks on 2007-11-18
> **Duck2006 said:**
> This mite be what your looking for.

[http://www.eloff.se/tutorials.php?ubuntu_vista_dualboot](http://www.eloff.se/tutorials.php?ubuntu_vista_dualboot)

Wow, even better thanx my friend:)

---

### Post by infogorf on 2007-11-18
You could also buy a new harddisk, install Vista on it and F8.

---

### Post by RobotoWorks on 2007-11-18
Moneys tight, I cant afford that

---

### Post by infogorf on 2007-11-18
If you got all your files on a shared NTFS partition, you could buy an old 40 GB (or less). Should be affordable to anyone. Personally I like this solution cause it is flexible.

---

### Post by RobotoWorks on 2007-11-18
Well I wiped my laptop's hardrive and I have about 64 gigs of free space, so I think Ill be find

---

### Post by Rippie on 2007-11-18
100% you need to install Vista first. and then install ubuntu

OBS !! make some diskspace for ubuntu when you installed Vista :)

---

### Post by RobotoWorks on 2007-11-18
If you are so sure you need Vista first, check this out:
[http://www.eloff.se/tutorials.php?ubuntu_vista_dualboot](http://www.eloff.se/tutorials.php?ubuntu_vista_dualboot)

---

### Post by monte48lowes on 2007-11-18
I just want to add... make a seperate partition for /home. You can completely reinstall ubuntu on your / partition and not lose any of your files or configurations. You might lose some of the programs you installed, but those are simple to replace. I also recommend backing up your /home partition to some other form of media, or at least a seperate hard drive.

Mike

---

### Post by techmunkey on 2007-11-18
I dual Boot Ubuntu 7.10 and Vista. I use a virtual disk on my Vista partition and it works like a champ!

WUBI 7.10 installer you run within Vista to start. [http://wubi-installer.org/devel/minefield/]("http://wubi-installer.org/devel/minefield/")

[http://wubi-installer.org/]("http://wubi-installer.org/")

If you have any questions let me know.

---

