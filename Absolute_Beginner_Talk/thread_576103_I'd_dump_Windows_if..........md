---
title: "I'd dump Windows if........."
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2007-10-14
I could get a proper disk image program that wasn't a pain, I have stuggled with partimage
for half the day, and when trying to do it, got a "Disk Full" error, any new ideas on that ?
:confused:

---

### Post by MatthewPlanchard on 2007-10-14
Are you trying to burn image files to CD's or create image files from CD's? Or something else entirely?

---

### Post by aktiwers on 2007-10-14
[http://www.psychocats.net/ubuntu/iso#burning](http://www.psychocats.net/ubuntu/iso#burning)

---

### Post by Pumalite on 2007-10-14
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by Drakkor on 2007-10-14
Uuh, no to both, what I am trying to do is make an image of my disk #2 which has Ubuntu/Gutsy on it. , ........   I can use Acronis True Image in XP to accomplish that task, but
from what I've seen in Linux, is very disappointing. :(

---

### Post by troy1of2 on 2007-10-14
...I had it to dump.

---

### Post by Pumalite on 2007-10-14
[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)

---

### Post by aktiwers on 2007-10-14
Uh sorry..  I misunderstood your post completely..
DId you try this guide?
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

And are you sure you have enough disc space to create the backup?

---

### Post by Drakkor on 2007-10-14
Yeah,tried the psychocats deal and [http://ubuntuforums.org/showthread.php?t=80790](http://ubuntuforums.org/showthread.php?t=80790)
is way too much trouble for me. so I'll eiher keep XP or live life dangerously and if I 
mess up totally re-install Gutsy,lol :)

---

### Post by asmoore82 on 2007-10-14
> **Drakkor said:**
> Uuh, no to both, what I am trying to do is make an image of my disk #2 which has Ubuntu/Gutsy on it. , ........   I can use Acronis True Image in XP to accomplish that task, but
from what I've seen in Linux, is very disappointing. :(

[http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/)

---

### Post by wolfen69 on 2007-10-14
i use acronis "demo" version. works perfect everytime. i use hirens boot cd just for evalutation purposes only. :-)

---

### Post by Drakkor on 2007-10-14
Wow,Clonezilla, I like the name already,lol :)

---

### Post by HermanAB on 2007-10-14
Copying disks is an ancient problem going back to some time before the dinosaurs.  Just use dd and gzip over nc.

On the server:
nc -l -p 5000 | gunzip | dd bs=100k of=file.img

On the workstation:
dd if=/dev/sda bs=100k | gzip --fast | nc server 5000

Then go and get some coffee and complain to everybody about how hard you are working.

Writing the image back to another disk is just the reverse process.

Cheers,

Herman

---

### Post by AMDBuntu on 2007-10-14
Perhaps I'm misunderstanding? If your looking for a good recording program to write the Ubuntu to a CD try Infrarecorder. It's free, works great and is straight forward.

---

### Post by Drakkor on 2007-10-14
Yep, you are misunderstanding me,lol :)
Edit: Herman.........swhooosh.........way over my head,lol

---

### Post by bodhi.zazen on 2007-10-14
Partimage is nice, but i see you haev had problems.

You can look at ghost for Linux : [http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/)

---

### Post by HermanAB on 2007-10-14
nc = netcat, a very simple and fast way to shovel data over a network
gzip, gunzip = obvious
dd = ancient sector by sector disk copy utility

Pipe those three together and you can move mountains of data:
[http://www.aeronetworks.ca/netcat-howto.html](http://www.aeronetworks.ca/netcat-howto.html)

Cheers,

H.

---

### Post by hyper_ch on 2007-10-15
Are you sure you want to make disk images? They use up a lot of space. I rather do on a regular base (like every 6h) a complete file backup using rsync and hardlinks dating back 90 days.

---

