---
title: "Access Denied"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by cytutchi on 2006-10-01
Hi there people!
I run Kubuntu to be honest but i supose that is the same!
Well anyway since a beginner as well here i have a question to ask...in my laptop i have three main partitions...1 for windows, 1 for linux and 1 lets say for common use (+swap...etc)!
Anyway my access to the "common room" was ok, and still is in the sense i can use the files mp3 or either view staff so this means that this device is mounted, i can access it!
,But now for example i cannot paste stuff on that space, it says that my access is denied,!
What can i do about that? - How?
Thenx a lot for your understanding!

---

### Post by Tominator on 2006-10-01
I can't answer your question but there are 3 desktops, Kubuntu,Xubuntu, and Gnome, they are different. Good luck, Tom.

---

### Post by Fass on 2006-10-01
How are you mounting the partition? What filesystem is it?

---

### Post by bulldog on 2006-10-01
> **Tominator said:**
> I can't answer your question but there are 3 desktops, Kubuntu,Xubuntu, and Gnome, they are different. Good luck, Tom.
 

Well this is very helpfull,thank you so much.

Type in your terminal```
kdesu nautilus
``` and right click the mounted disk and alter the rights so you can read and write again.

Or is it Konquerer?? 
Use gnome and think everyone is.......:D

---

### Post by cytutchi on 2006-10-02
Firstly guys thenx for your replies but nothing worked out of this!
i typed kdesu nautilus but the command nautilus was not found...i also tried to type kdesu konqueror but still the command konqueror was not found.
The partition i did it at the begining when i was instalng KUBUNTU and it is fat32.
if you have any more sugestions...i would appretiatie it..
thenx

---

### Post by cytutchi on 2006-10-02
i forgot to say that that parition is /root/media/data
the data is what i cant copy on
this is where it is shared!
how i mount it was manually with the command:
sudo kate /etc/fstab
then i added in the last row the following and i can see and play with it

/dev/hda6	/media/data	vfat	defaults,user	0	0

---

### Post by hyper_ch on 2006-10-02
I use this for mounting fat32:

```

/dev/hda6 /media/fat32 vfat umask=000 0 0

```

That works on my ubuntu 6.06

---

### Post by cytutchi on 2006-10-02
YYEEEAAAA!!!!!!!!!!
:)))
THENX A LOT MATE
it works fine now...i mounted it diferently with the unmask and it works now just fine
but i'd like for somebody to explain it to me why this happes..so no just to make it work but also to understand it!
before it was defalt,user and it was not working but now with unmask=000 it does...what did actually happend?
THENX a lot guys...Kubuntu and this Forum Rules! ;)

---

### Post by hyper_ch on 2006-10-02
actually I have no clue what it exactely does. All I know is I found that code somewhere on the web, added it to my fstab and it works... :)

---

