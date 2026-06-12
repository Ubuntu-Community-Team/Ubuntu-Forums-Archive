---
title: "Great"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by WoodyMahan on 2006-03-24
For all those frustrated newbies.  It will get better.  I was lost for a few days but I have found that this forum does have the answers.  
I got a new system and decided that I wanted to try Linux on it.  I found out about Ubuntu and was informed that you can install it and nearly everything works out of the box.  So I added another hard drive to my new system and loaded up the OS.  It found everything on the computer and had drivers for it all.  NIC, monitor, floppy, CD....It all worked.  I had to figure out how to load codecs for video files, (Automatix handled this) and I had to figure out how to load my storage drive (80 GB Fat32 Spare hard drive).  This was the most difficult thing to figure out, but after a day or 2 I understood how mounting drives and editing the fstab worked, so that was fixed.  

My Laptop got hosed by a virus 3 days ago so I decided to setup a dual boot on it.  Keeping Windows for my job and for my wife, but installing Ubuntu for myself.  Again, everything worked out of the box.  I did something wrong so my Storage partition on this machine isn't as big as I wanted (I'll post a new thread to figure that out) but I had video, sound, NIC, right out of the box.  This time I mounted my extra drive (Fat32 partition) in less than 3 minutes.  Now my challenge was wireless.  I spent about 2 hours searching the wiki and the forum for instructions but just couldn't figure it out.  So I posted a thread stating the system and wireless card that I use.  This morning when I got up, I had a reply with 4 simple commands in it.  Copy, Paste, Voila.  I have a working wireless connection.  The person answering had the same wireless card so they had already figured it out.

Maybe this has been a little too easy, but reinstalling Windows, finding the drivers, getting all my software back on took 6 or 7 hours.  Installing Ubuntu and figuring out how to get my wireless card working took about 4.

I feel like I have stepped into a different world.  Ubuntu is working great for a little tool hick in Georgia.

Stick with guys and girls, it gets easier as you go along.

Wood

---

### Post by gnu2tux on 2006-03-24
I'm really glad to hear that Ubuntu is working out so well for you!

With regards to the gparted tool problem - have you tried qtparted, I find that the gnome equivalent (gparted) is a it flaky, oh and make sure that you are running the tool as the super user rather than the normal user (gksu gparted)

Regards,

Al

---

### Post by WoodyMahan on 2006-03-24
What repository is qtparted in?  I'll try it.  Super user didn't fix the issue.  Thanks for the reply.

---

### Post by gnu2tux on 2006-03-24
It's in kubuntu, so I'd imagine it's in the main or universe repository and should be installable without any more efforts (as long as you have universe/multiverse enabled -- give me a shout if you don't know how to enable these, hint: /etc/apt/source.list).

Regards,

Ali.

---

### Post by plors on 2006-03-25
[QUOTE=gnu2tux]
With regards to the gparted tool problem - have you tried qtparted, I find that the gnome equivalent (gparted) is a it flaky... <snip>

Regards,

Al[/QUOTE]

sorry, /me running to the defense again ;) 
I guess this is because the default ubuntu gparted is quite old, you should get the latest gparted indeed. I strongly advice to use the [gparted livecd]("http://gparted.sourceforge.net/livecd.php").

have fun :)

---

### Post by WoodyMahan on 2006-03-25
FYI:  The Live CD did the trick.  Thanks All.

---

### Post by nalmeth on 2006-03-25
Excellent!
Great to hear more success stories.
Very satisfying when you're able to get over those humps, and when you are able to find such great help.

Happy Ubuntuing!

---

### Post by WoodyMahan on 2006-03-25
Absolutely.  You can always find great help here.

---

### Post by bionnaki on 2006-03-25
[QUOTE=WoodyMahan]

I did something wrong so my Storage partition on this machine isn't as big as I wanted [/QUOTE]

I think ext3 filesystem takes up alot of space. try reiserfs instead - uses less space.

---

