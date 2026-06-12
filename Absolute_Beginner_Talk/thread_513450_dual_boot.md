---
title: "dual boot"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by llzero1337 on 2007-07-30
hi i was wondering if someone can help me dual boot i have Ubuntu on a 120gb Maxtor ide hdd and windows xp on a 200gn maxtor ide thanks for help!

---

### Post by llzero1337 on 2007-07-30
ubuntu is on master and windows on slave btw

---

### Post by oilchangeguy on 2007-07-30
read this:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by llzero1337 on 2007-07-30
hmm i've already got both OS'es installed on both HDD's

---

### Post by ron999 on 2007-07-30
I asked a very similar question to this last week.
I have Ubuntu on my master drive and Windows 2000 on the slave.
I had to edit the grub menu.
There is a file named menu.lst
Look in boot folder then in grub folder.
I had to add these extra lines and re-save it.

title           Windows
root            (hd1,0)
makeactive
chainloader     +1
map (hd0) (hd1)
map (hd1) (hd0)

---

### Post by llzero1337 on 2007-07-30
it doesnt let me save it 



can someone please help me dual boot without formatting anyyhing

---

### Post by atomkarinca on 2007-07-30
did you try to open it using sudo?

---

### Post by ron999 on 2007-07-30
> **llzero1337 said:**
> it doesnt let me save it 





You need to type into the monitor
[B]sudo nautilus
[/B]
Then search for the file.
Then open  it.
Then copy and paste  my extra lines.
Then save it and reboot.

---

### Post by llzero1337 on 2007-08-02
woah ron thanks alot i never knew it was so easy to dual boot i thought that it would of taken 30- 1 hour to set up but it actuall only took 2 mins thanks again!

---

