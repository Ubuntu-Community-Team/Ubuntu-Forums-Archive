---
title: "I need help with Ubuntu and Ktorrent.. or do I?"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by StarscreamD on 2007-02-19
I am using Edgy. Ktorrent is the best linux torrent program out there(correct me if I'm wrong); it is far better than the bundled Freeloader because it is more configurable and you can resume downloads.

My question is this: after it runs for awhile, Ktorrent seems to grind to a halt, and I have to restart the program to check on the status of the downloads. Is everyone having this problem? Is it fixable? What's goin ON here? Any help would be greatly appreciated.

---

### Post by Bachstelze on 2007-02-19
I personnaly have no problems with KTorrent. What exactly does it do ?

And yeah, it is the best torrent client indeed ;)

---

### Post by StarscreamD on 2007-02-19
OKay this is what happens. You know how every half second or so how the program refreshes your dl and ul speed and just displays the overall staus of the download? Well that will function normally for about 20 seconds, then, it will freeze for about 20 seconds. I can minimze the window, but if I restore it, when it comes back I cannot see the information normally in the window, It is just a blueish gray window. After the 20 seconds transpires, the program functions as normal for another 20 seconds and it just keeps doing that. I can't tell if it is functioning normally while the screen is frozen or not.

*pant*

---

### Post by Bachstelze on 2007-02-19
Wile it's "frozen", does it's memory and/or CPU usage increase ? You can use the *top* command to watch this.

---

### Post by StarscreamD on 2007-02-19
Ahh.. I have a NTFS disk mounted that Ktorrent is saving to? When it is frozen, that partition is taking 95% of the processing power.. :(

---

### Post by StarscreamD on 2007-02-19
Also at the time that the ntfs partition takes over my processor I cannot see Ktorrent on the TOP menu.

---

### Post by Bachstelze on 2007-02-19
Use a decent filesystem instead, then ;)

---

### Post by StarscreamD on 2007-02-19
Forgive me, I'm a new linux user, this is my third day.

What do you recommend I do?

---

### Post by Maestro23 on 2007-02-19
> **StarscreamD said:**
> Forgive me, I'm a new linux user, this is my third day.

What do you recommend I do?

Doh...lol  Trying to put a square peg in the round hole.:lolflag: 

Easiest thing would be to have Ktorrent save them to your /home partition. How big is your /home partition? Can also have it save them to a FAT32 partition which both Linux and Windows can read/write to.

---

### Post by StarscreamD on 2007-02-19
I am running a Dual boot Win XP Pro 32 SP2 and Ubuntu Edgy. There are two HD's on my system, one is 20GB which contains both the Win XP system partition and the Ubuntu system partition. It is full. :)

The other drive is a 60 GB. It is pretty much empty. I wouldn't mind reformatting it, probably to the FAT 32 format you described. Is there a way to do that inside linux?

---

### Post by Maestro23 on 2007-02-19
> **StarscreamD said:**
> I am running a Dual boot Win XP Pro 32 SP2 and Ubuntu Edgy. There are two HD's on my system, one is 20GB which contains both the Win XP system partition and the Ubuntu system partition. It is full. :)

The other drive is a 60 GB. It is pretty much empty. I wouldn't mind reformatting it, probably to the FAT 32 format you described. Is there a way to do that inside linux?

You can use gparted.  Can get it from the repositories.

> sudo aptitude update

sudo aptitude install gparted

Can run from terminal:

gparted

Or, I believe you can use the Live CD.

*See this thread also: [http://www.ubuntuforums.org/showthread.php?t=365229](http://www.ubuntuforums.org/showthread.php?t=365229)

---

### Post by StarscreamD on 2007-02-19
Ktorrent is now running smoothly thanks to your advice. Thank you!

---

