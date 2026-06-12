---
title: "help with post install"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by Moonah on 2008-01-16
hi guys
i'm still new to using linux.
but i've installed ubuntu studio (64 bit).
now my problem is after i go through the install process and it boots back up i select ubuntu as the os to boot up in. but then it comes up with this screen that looks like dos (but obviously isn't), i enter in my username and password and then it says a little speel saying that ubuntu has no warranty. 

now i was wondering is there a command i need to type in to get it to come up to the normal ubuntu desktop, or is there something i should be typing in here?

if you guys could help it would be greatly appreciated.

---

### Post by wolfen69 on 2008-01-16
```
startx
```

---

### Post by SOULRiDER on 2008-01-16
> **wolfen69 said:**
> ```
startx
```

That will most likely spit an error, post it here please.

---

### Post by Moonah on 2008-01-16
thanks guys

it came up that it wasn't installed 

so i did the whole sudo apt thing

but then once it installed i ran that command

and it says

X: cannot stat /etc/X11/X (No such file or directory), aborting.
giving up.
xinit: Connection refused (errno 111): unable to connect to X server
xinit: No such process (errno 3): server error.

---

### Post by Moonah on 2008-01-16
how do i fix this guys?

---

### Post by nikoPSK on 2008-01-16
maybe reconfigure x?
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

nikoPSK

---

### Post by Moonah on 2008-01-16
i did what you said 
and it came up with 

Package 'xserver-xorg' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (=dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-xorg is not installed

like i said i'm new to ubuntu and have only had a quick demo from a few people and was very impressed. if i could get this sussed that would be great.

---

### Post by nikoPSK on 2008-01-16
> **Moonah said:**
> i did what you said 
and it came up with 

Package 'xserver-xorg' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (=dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-xorg is not installed

like i said i'm new to ubuntu and have only had a quick demo from a few people and was very impressed. if i could get this sussed that would be great.

0.o.... maybe x is not installed... :confused: oddness....

---

### Post by PurposeOfReason on 2008-01-16
Did you do a minimal install? Try:

sudo apt-get install xorg

---

### Post by Moonah on 2008-01-16
when i installed this i just followed the prompts that were given on the CD.

i've installed the x like you said

and i configured it 

now when i try to startx it comes up saying this 

Fatal server error:
no screens found
X10:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
        after 0 requests (0 known processed) with 0 events remaining.

---

### Post by Moonah on 2008-01-17
](*,)

---

### Post by nikoPSK on 2008-01-17
> **Moonah said:**
> ](*,)

it's fine, try not to bump your thread too much. It's best if you wait a day. :)

nikoPSK

---

