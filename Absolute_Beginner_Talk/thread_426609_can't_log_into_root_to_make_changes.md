---
title: "can't log into root to make changes"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by firedancer on 2007-04-28
:confused:  i can't seem to log into root , isn't it similar with the name i installed the system with

cause when i log in with my first account (name) and try to run something in sudo it says : not superuser, i'm kind of lost here , just ubuntu few days ago for:guitar: music rec 
please, some help!

---

### Post by taurus on 2007-04-28
What's the output of this command from a terminal?

```
id
```
You should see both adm & admin (and other groups) on that list.  If you don't, then sudo won't work.

---

### Post by Bachstelze on 2007-04-28
To run command-line stuff with root privileges :

```
sudo command
```


To run GUI stuff with root privileges :


In Gnome or XFCE :

```
gksudo command
```

In KDE :

```
kdesu command
```


[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Tomosaur on 2007-04-28
You log in as your ordinary account. When you want to perform an administrative action using sudo or gksudo, the password you input is the same as your normal password.

Ubuntu has the root account (where you actually log in with user name 'root') disabled for security reasons - you should just use sudo whenever you need to do something requiring root permissions.

If that doesn't answer your question, could you be a little clearer? It sounds like you're trying to log in as root, sorry if I'm mistaken.

---

### Post by firedancer on 2007-04-28
id 
uid=1001(firedancer) gid=117(admin) groups=4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),29(audio),30(dip),46(plugdev),104(scanner),117(admin),119(fuse)

---

### Post by taurus on 2007-04-28
What's the output of this command from a terminal?

```
sudo aptitude update
```

---

### Post by firedancer on 2007-04-28
gksudo worked !:) 


i am trying to unswap a partition on my second hdd , because i made it totally swap

i have a dual boot sys xp and ubuntu 2 hdd split them in two (well almost)  and then the above occured

sorry that i'm changing the topic now thnx

i'll be back :popcorn:

---

### Post by firedancer on 2007-04-28
should i start new thread for my other Quesetions):P

---

### Post by Tomosaur on 2007-04-28
Not necessarily, unless you think they'd help other people who did a search for them. If they've been asked before, you may aswell just ask them here.

---

### Post by firedancer on 2007-04-28
so first i did gksudo swapoff /dev/hdb2

then fdisk  /dev/hdb

but to make partitions ?:-\"

one partition for filing

and another for swap

---

