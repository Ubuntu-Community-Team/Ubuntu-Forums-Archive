---
title: "[SOLVED] kde 4.02"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by skyjacker on 2008-03-23
I had kde4.02 installed (only the core) so that I could choose between 3 an d4 in the startup menu. It was just what I wanted until I was experimenting and chose something called (I think) desktop improvemenyts. It had stuff like tile windows vertically or horizontally,etc. After choosing this ang clicking on "apply" the screen went black and stayed that way. I did an [CODE][sudo aptitude remove clean kde-4 core/CODE], and restarted. Then I did [CODE][/sudo aptitude install kde-4 coreCODE] After choosing kdde4 all I got was another black screen. How can I correct this Thanks in advance!!

---

### Post by skyjacker on 2008-03-23
Bump - Anyone know about this problem???

---

### Post by utUtu on 2008-03-24
> **skyjacker said:**
> Bump - Anyone know about this problem???

On a terminal delete your .kde4/ directory at your home directory

rm -r .kde4

Then restart your computer.

---

### Post by skyjacker on 2008-03-24
> **utUtu said:**
> On a terminal delete your .kde4/ directory at your home directory

rm -r .kde4

Then restart your computer. Worked like a charm.  Thanks:)

---

