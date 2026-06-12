---
title: "2 problems  please help ASAP"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by piratedninja06 on 2006-08-24
im using ubuntu 5.04

1st problem is i cant get my RTL8185 driver to work  i downloaded it from the realtek website but im stuck at the first step  (its saying the file doesnt exist)   
its one of those compusa pcmcia cards (im using a laptop)
device manager sees the card   and the card works perfectly in windows xp

2nd problem   how do i setup ubuntu to where it can read from the ntfs partition?



im a complete noob with linux (especially ubuntu) in general so please try to break it down for me as much as possible

---

### Post by nalmeth on 2006-08-24
1st question...
Is it possible to download the newest version of Ubuntu?
Dapper Drake 6.06.1 is the newest, 5.04 is two versions back.

2nd question...
What method are you using for your driver? Must be ndiswrapper right? Do you have the ndisgtk app which will make this much easier for you?

Honestly, you card may be supported out of the box with Dapper. If you can you should get that instead.

Post back with answers

---

### Post by Jagot on 2006-08-24
Is there any reason you're not using Dapper?

Not sure about the wireless, but read this re the Windows partition:

[https://help.ubuntu.com/5.10/ubuntu/faq/C/fg-windows-partitions.html](https://help.ubuntu.com/5.10/ubuntu/faq/C/fg-windows-partitions.html)

Either way, upgrading to Dapper wouldn't hurt.

---

### Post by professor_chaos on 2006-08-24
I assume that you downloaded the driver rtl8180-0.21.tar.gz and did the following.
Open up the terminal and change directory to the directory you download the tar archive. 

example
```
cd /home/yourusername/
```

following the install instructions in the tar you need to do this.

```
tar xzf rtl8180-0.9.1.tar.gz
cd rtl8180-0.9.1
make
```

Do you get this far?


As for ntfs filesystems, do a search in this forum for the keywork NTFS and you will find your answer. Let us know if you still have problems getting it to work.

---

### Post by piratedninja06 on 2006-08-24
wow  thanks for the quick replys
i'll download dapper rite now

professor_chaos   i didnt get that far   i opened the readme file and tried to run the makedrv file in terminal as well as some other files  but none of them worked   i'll have to try what u posted above in a few minutes    i'll post back tomorrow as im going to start downloading dapper right now and go to bed

---

### Post by piratedninja06 on 2006-08-24
i downloaded dapper but once i go to install it it freezes at a blank screen

the specs of the laptop are   p3@850mhz, 20gb 5400rpm hdd, and 128mb ram  is that enough for dapper?


o and can someone post some stepbystep instructions (broken down as much as possible) on what to do after i download the linux RTL8185 driver ?

---

### Post by piratedninja06 on 2006-08-26
can anyone please help me?

---

