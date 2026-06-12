---
title: "What version of Ubuntu do i have"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by lilyoshi13 on 2007-05-14
How do i figure out witch ubuntu i have

---

### Post by nphx on 2007-05-14
In terminal type in:

```
cat /etc/issue
```

---

### Post by cliv on 2007-05-14
try clicking the main menu -> System -> about ubuntu

---

### Post by DaveyG on 2007-05-14
> **lilyoshi13 said:**
> How do i figure out witch ubuntu i have

try System then about ubuntu

---

### Post by lilyoshi13 on 2007-05-14
is

Ubuntu 5.10 "Breezy Badger" \n \l

The newest version of ubuntu

p.s. srry if this is really noobie

---

### Post by Skrynesaver on 2007-05-14
In a terminal
```

cat /etc/issue

```
Or indeed just switch to one of the text consoles [CTRL][ALT][F3], [CTRL][ALT][F7] switches back to the graphical console

---

### Post by lilyoshi13 on 2007-05-14
If not how do i upgrade

---

### Post by DaveyG on 2007-05-14
> **lilyoshi13 said:**
> is

Ubuntu 5.10 "Breezy Badger" \n \l

The newest version of ubuntu

p.s. srry if this is really noobie

No, 7.04 Feisty Fawn is the latest release :D


Edit: i dont know about updating....

---

### Post by lilyoshi13 on 2007-05-14
now how do i upgrade

---

### Post by taurus on 2007-05-14
You need to upgrade to 6.06 -> 6.10 -> 7.04.  You cannot go from 5.10 to 7.04 because it will break.  

Therefore, the best way is to install 7.04 fresh.

---

### Post by lilyoshi13 on 2007-05-14
is there a way to do that without a cd

---

### Post by L Campbell on 2007-05-14
> **lilyoshi13 said:**
> How do i figure out witch ubuntu i have

When you open your Firefox web browser it announces it to you.

I don't mean verbally but it is written there.

---

### Post by icechen1 on 2007-05-14
> **lilyoshi13 said:**
> is there a way to do that without a cd

use auto update to 6.04 then update to 6.10 then 7.04 but that will take a lot of time and a risk of breaking your system!
You can do this on the update manager.

---

### Post by lilyoshi13 on 2007-05-14
If i were to upgrade one by one how would i do that.  

I have had way to much trouble with making cds

---

### Post by icechen1 on 2007-05-14
> **lilyoshi13 said:**
> 
I have had way to much trouble with making cds

Request free Cds with Shipit([https://shipit.ubuntu.com/](https://shipit.ubuntu.com/))

---

### Post by lilyoshi13 on 2007-05-14
When i was making the cd i had no trouble downloading it but i had no idea how to get it into a bootable iso image.  Is there something i'm missing

---

### Post by pikul on 2007-05-14
The file you download is an .iso file? if thats the case all you need to do is open the software you use to burn files and look for an option that says something about burning iso image or file, its not that hard, what program do you use to burn files?

---

### Post by Happy_Man on 2007-05-14
If you are using nautilus, the best way to burn an .iso is to drop a blank CD into the drive, and then go to your .iso file (wherever it's stored) and right-click and choose Burn Disc. It will autoburn as a disk image.

---

### Post by lilyoshi13 on 2007-05-14
> **pikul said:**
> The file you download is an .iso file? if thats the case all you need to do is open the software you use to burn files and look for an option that says something about burning iso image or file, its not that hard, what program do you use to burn files?

I use nero on my windows XP computer

---

### Post by Sef on 2007-05-14
[How to burn an iso on Nero]("http://www.petri.co.il/how_to_write_iso_files_to_cd.htm").  Just scroll down a bit, and the directions are there.   Do not burn faster than 4x as it may corrupt the burn.

---

### Post by lilyoshi13 on 2007-05-14
ok i upgraded to to 6.06 but now 6.10 dose not appear in the update manager so how do i upgrade

---

### Post by Happy_Man on 2007-05-15
Go into /etc/apt/sources.list and change every instance of "dapper" to "edgy" and restart the update manager.

---

### Post by zvacet on 2007-05-15
Your Dapper must be up-to-date if you want to upgrade to Edgy.
```
sudo aptitude update
```

and after that

```
gksu "update-manager -c"
```

---

### Post by lilyoshi13 on 2007-05-15
thx zvacet it worked

---

### Post by NevadaSam on 2007-11-24
I found some replies in this thread to be very useful. The main thing I believe I need to do is upgrade.

---

