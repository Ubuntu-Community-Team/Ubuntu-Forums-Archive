---
title: "New to linux"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by Topaz on 2006-03-28
Over 70 in age, very slow, can't seem to find answers to questions using search.
Wanted to update to 5.10 from my 5.04 on machine. Also why does all my icons
on desktop have locks over them?

---

### Post by taurus on 2006-03-28
If you want to upgrade from 5.04 to 5.10, you need to edit your /etc/apt/sources.list.  Open a terminal and at the prompt, type
```

sudo gedit /etc/apt/sources.list

```
Then, replace all the lines that contain hoary with the word breezy.  Save it and from the prompt again, type
```

sudo apt-get update
sudo apt-get dist-upgrade

```

p.s.  When it asks you for a password, use the same one that you log in with...

---

### Post by RedKnight on 2006-03-28
Locks on files usually mean you have created the files as "root" you can check this by going to the properties of the files and checking the file owner under the premission's tab.

Stuart

---

### Post by Topaz on 2006-03-29
I uninstalled 5.04 and reinstalled, then did upate to Breezy. There was some failed
items but it was going so fast and not knowing what they were, did nothing. Breezy
seems to be running alright. I believe the reason the icons on the desktop were locked was because I slid them from places/computer to desk top. As long as they
remain in places/computer they are not locked. I wish there was a book or how to
that would explain how to do things. I feel like I'm in a total darkness room gropping
around. I sure would like to know what programs I have on my hard drive and how
much room I have left?

---

### Post by NeghVar on 2006-03-29
one easy way to see all your discs and available space is to go

System>Administration>Disks Type in login password, then click on the disk in question and hit over to partitions.

Another way is to just go

Places>Computer>File System then look at the bottom of that window it will tell you how much free space.

---

