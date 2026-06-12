---
title: "Store my games..."
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by Lindworm on 2007-05-14
Hey my old hard drive broke so I don't have much space (40gb) also considering my windows partitions takes up 25 gb I have little space for /home. Don't tell me to either go completely Linux, (not my choice), or to use windows. I'm trying to get as good at Linux so it's an experiment. I have about 1 gig for /home so I don't have much. Is there anywhere else to put it like in /. I tried this but it says I don't have permissions also I tried logging on as root but it wont let me.

Thanks,
Ben

---

### Post by oilchangeguy on 2007-05-14
i'm guessing you've got an ide hard drive. since they're being replaced by sata drives, they've become fairly cheap. i'd suggest buying a new one before they get even harder to find.

---

### Post by Lindworm on 2007-05-14
I'm 14 so I am not exactly in a position to buy one. Also whats wrong with IDE hard drives?

---

### Post by oilchangeguy on 2007-05-14
> **Lindworm said:**
> I'm 14 so I am not exactly in a position to buy one. Also whats wrong with IDE hard drives?

nothings wrong with them. newer computers have switched to sata drives, which are supposedly better. (all of my computers run ide drives)
as far as being 14. i'm a bit older than you. but when i was 14 i made money. mowing yards, delivering newspapers, etc. don't use your age as an excuse not to make money. it can be done.

---

### Post by Lindworm on 2007-05-14
:D
I'm not trusted with the lawn mower hehe.

Anyway do you know of any way for me to store my games in the / directory thing as I have about 500mb left in the /home. Or do I just have to use gparted and shrink / down and make /home bigger.

---

### Post by oilchangeguy on 2007-05-14
approx. how much space do your games need?

---

### Post by aidanr on 2007-05-14
of course there's no reason you can't put it in / (if there's enough space)
sudo mkdir /games
sudo chown username /games

---

### Post by Lindworm on 2007-05-14
500 which would mean I have around 150 left, but I want some space spare aswell. Maybe I shouldn't have put so much in /. I have around 10 gig in all.

---

### Post by Lindworm on 2007-05-14
Ah thanks aiden. BTW what does Sudo mean I come across it alot.

---

### Post by aidanr on 2007-05-14
superuser do, it runs the command following it as root

---

