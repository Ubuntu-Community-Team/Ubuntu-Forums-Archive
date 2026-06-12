---
title: "how to keep vista? partitioning. ubuntustudio"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by giorgiomartini on 2007-05-19
hi , i finally could boot the ubuntustudio.

now , i need to know how to partition my hard disk.

i think its posible to do it in the instalation process of ububtustudio , when it comes the partitioning part you can choose :

guided : use entire disk
guided: use entire disk and set up lvm
manual

witch one should i choose to keep vista? i have 120g   i will leave 60 for vista and 60 for ubuntustudio, and i think i need to do one for  '' swap'' right?

so can someone please explain me. what do i have to choose to keep vista and install ubuntustudio?

---

### Post by bobplano on 2007-05-19
use vista's partiton manager to resize your windows partition. then it is recommended (for maintsream ubuntu at least) to have:
10gigs or more /(root)
1-2gig, or double ram of swap
and a /home as big as you want

---

### Post by maniacmusician on 2007-05-19
> **bobplano said:**
> use vista's partiton manager to resize your windows partition. then it is recommended (for maintsream ubuntu at least) to have:
10gigs or more /(root)
1-2gig, or double ram of swap
and a /home as big as you want
nah, most installs will never exceed 5GB for /. You'd only need 10 if you were installing everything (Gnome + KDE + XFCE + window managers, etc).

---

### Post by giorgiomartini on 2007-05-19
[COLOR="DarkOrange"]use vista's partiton manager to resize your windows partition[/COLOR]

ok , so from vista i resize my windows partition.

what is that?

so i supose should resize my windows disk space to 60g , so then i wpuld have 60g free for ubuntu right?

do you know any tutorial on resizing?

thanx

---

### Post by confused57 on 2007-05-19
Maybe this will help:
[http://www.pro-networks.org/forum/viewstory.php?t=78111](http://www.pro-networks.org/forum/viewstory.php?t=78111)

---

