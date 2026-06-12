---
title: "new k52f headphones jack not working right 10.04"
date: 2011-08-02
forum: Asus Ubuntu Support (CLOSED)
---

### Post by match417 on 2011-08-02
So I bought this laptop about a month ago when my other laptop died. The first thing I did was wipe the drive and install ubuntu 10.04 with win7 in virtualbox. The problem I noticed immediately was when I plug in a headphone plug it does not make the laptop speakers silent, instead I have sound coming out of both the laptop speakers and the headphones. It gets annoying having to turn my laptop speakers down almost all the way and then run the headphones through some kind of speaker system that can amplify the headphones just so I can listen to the headphones with the laptop sound nearly off. Anyone else have this problem? Do I need a different driver?

---

### Post by LoganDimond on 2011-08-17
same problem with a k52f and 11.04. I'll let you now if i find something that works for me.

[http://ubuntuforums.org/showthread.php?t=1460790](http://ubuntuforums.org/showthread.php?t=1460790) this is the closest thing I could find, but it didn't work for the sound for me (I have kernel 2.6.39).

---

### Post by match417 on 2011-08-17
> **LoganDimond said:**
> same problem with a k52f and 11.04. I'll let you now if i find something that works for me.

[http://ubuntuforums.org/showthread.php?t=1460790](http://ubuntuforums.org/showthread.php?t=1460790) this is the closest thing I could find, but it didn't work for the sound for me (I have kernel 2.6.39).

actually mine started working when I installed ubuntu 11.04. My kernel is 2.6.38-10

---

### Post by firefox_user2 on 2011-08-24
Here is a solution that worked for me at the following link for a similar problem, it might help.
[http://ubuntuforums.org/showthread.php?t=1685073](http://ubuntuforums.org/showthread.php?t=1685073)

---

### Post by fieloryb on 2012-08-17
My Asus K52F after instruction:
```

~$ lspci|grep Audio

```
gives:
```

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)

```

I found answer [[COLOR="Red"]here[/COLOR]]("http://www.physicsforums.com/blog.php?b=2580").

Solution is simply adding:
```

options snd-hda-intel model=z71v position_fix=1

```
to the end of file:
```

/etc/modprobe.d/alsa-base.conf

```
Restart the computer.

It really works for me :).

---

