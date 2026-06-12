---
title: "How to apply properties TO ALL THE CONTENT of the folders"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by ChiendeRue on 2006-07-09
After a long, long quest, I have succeeded in accessing my old MP3's
It was a true pain to "mount" the partition (I called it 100GIG).
After lots of help on this forum (Thanks guys!:KS ), I have finally succeeded in seeing the volume, immediately after booting ubuntu 6.06, right there on my desktop (PHEW!).
amaroK finds the files but can't write the tags!

OK, I search & search...
> now I've learned how to log in as root
> I changed permissions and ownership

But more pain came my way....:-({|= 
I can not AUTOMATICALLY change permission for contents and I sure don't want to open thousands of folders.

Structure of these files is:
Volume = 100GIG
                >Folder: Music
                              >Folder: Artist
                                             >Folder: Album

:confused: _**QUESTION**_: How can I apply changes to ALL the files inside a folder? There's no obvious box to click. Is there a way to do this without typing my life story in a terminal?

---

### Post by aysiu on 2006-07-09
We need a little more info here.

What kind of partition is this--NTFS, FAT32, Ext3, Reiserfs, HFS+?

What version of Ubuntu are you using--Ubuntu, Kubuntu, Xubuntu?

---

### Post by ChiendeRue on 2006-07-09
Ubuntu 6.06
I formatted my second physical hard disk (slave) as ext3
It now shows up as hdb1
I mounted that partition after following: [http://psychocats.net/ubuntu/mountlinux.html](http://psychocats.net/ubuntu/mountlinux.html)

I logged in as root because root owned "100GIG"
I changed ownership to chienderue and allowed read/write
I now see a volume called 100GIG on my chienderue desktop (GREAT)

Remaining problem: The CONTENTS of that folder are still owned by root
The MP3's are three levels down into the folders 100GIG/music/artist/album/xxx.MP3

I don't know how to apply the permission changes into the subdirectories. There's no option box to tick (I just switched over from XP and very happily too).

---

### Post by bikeboy on 2006-07-09
I think you're looking for the recursive option, eg. ```
chmod -R 644 ./Music
```
This would apply the change to the selected folder "./Music" and all of its subdirectories. Recursive options can be used on lots of commands, if you're using a different way of changing the permissions try looking at the manpages for it to see if you can do it recursively. To search a manpage type "/" then the search term, and press "n" to loom for it again.

edit: so it's actual ownership you want to change, use the chown command with the -R option. eg ```
sudo chown -R username:groupname ./Music
``` Be careful though, you don't want to use the -R option lightly.

---

### Post by aysiu on 2006-07-09
> **ChiendeRue said:**
> Ubuntu 6.06
I formatted my second physical hard disk (slave) as ext3
It now shows up as hdb1
I mounted that partition after following: [http://psychocats.net/ubuntu/mountlinux.html](http://psychocats.net/ubuntu/mountlinux.html) That's odd. The directions in that link include the **-R** (recursive) option in both the change of ownership and change of permissions commands.

---

### Post by bikeboy on 2006-07-09
> **aysiu said:**
> That's odd. The directions in that link include the **-R** (recursive) option in both the change of ownership and change of permissions commands.Whoops, they sure do. I should have read the link, although I have been there before. Quality site that ;-)

---

### Post by ChiendeRue on 2006-07-09
Thanks guys.

Is it blasphemous to ask for the developers to put a little box there "include all subdirectories" for the next Ubuntu?

By wanting to be different from Windows, Ubuntu looks more like DOS to me. The commands are unintelligible to the unconsecrated, admittedly too lazy or impatient to learn.

Is it just a security thing or is it the desire to keep linux exclusive to the geeks?


From every other perspective I must admit that I find Ubuntu absolutely magnficent.

---

### Post by aysiu on 2006-07-09
Gnome favors simplicity over functionality.

KDE lets you check a box to include all subdirectories.

---

### Post by ChiendeRue on 2006-07-09
Hey hey! :shock: Superb that!

Two weeks ago my buddy installed Ubuntu 6.06 from a live disk for me.
I love the Ubuntu and switched my computer at work too. All is fine there.

I'm getting to know Ubuntu "andante" but I now believe that my home computer should get KDE. Any easy way to switch from here?

---

### Post by aysiu on 2006-07-09
Yes. Follow these instructions:
[http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)

---

