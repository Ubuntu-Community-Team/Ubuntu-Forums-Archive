---
title: "sudo this and sudo that."
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by ProjectGod on 2006-05-10
Hi gang,

this has probably been answered a many times already... or perhaps no one has asked yet. don't know looking through the documentation and wikis i failed to locate the answer...

at the console. the command **sudo** is it part of the linux kerneL? meaning can it be used in other distributions or is it only part of the ubuntu distro? is it part of BASH? like other commands?

appreciate it if you could point out url or resource that explains this. 

cheers.

---

### Post by n3tfury on 2006-05-10
[http://en.wikipedia.org/wiki/Sudo](http://en.wikipedia.org/wiki/Sudo)

---

### Post by Borniet on 2006-05-10
You'll find this in just about every Unix implementation.

---

### Post by Kvark on 2006-05-10
Some distros use sudo to do admin stuff from your normal account but most distros don't use sudo. On those distros you have to actually log in as root to do admin stuff.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by ProjectGod on 2006-05-10
great. 

thanks for the feedback. :)

---

### Post by Borniet on 2006-05-10
[QUOTE=Kvark]Some distros use sudo to do admin stuff from your normal account but most distros don't use sudo. On those distros you have to actually log in as root to do admin stuff.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)[/QUOTE]
I think it is a bit different from what you say here (I might be wrong though): Sudo exists on (almost) all Unices. Almost all linux versions let you log in as root to do admin work, as well as use sudo. Not so for (?)Ubuntu, it will not let you log in as root, but only lets you sudo to do your everyday household-admin. This is to prevent idiots like me to log in as root and use that account all the time. And if an idiot like an old friend of mine walks in to an idiot like me, and he believes me when I say: "Read your mail? Use rm -rf! It stands for ReadMail -Read Fast!". He was an idiot like me, but now he isn't anymore, he never again logged in as root...

---

### Post by Omnios on 2006-05-10
sudo is very clean 
compare
```
sudo whatever-you-need
password
```

compared to
```
su root 
password
su your-username to get back to your username
```

 Noticed there is a -? that lets you stay in root but forget what it is

---

### Post by richbarna on 2006-05-10
> Not so for (?)Ubuntu, it will not let you log in as root,

You CAN log in as root, it's just not recommended ;)

---

### Post by gibson on 2006-05-10
I was a debian user before coming ubuntu, and use "su" for everything and was i bit dishartened when i didnt have a root account in ubuntu. Now i use sudo all the time as i prefer it -- it grows on you!

---

### Post by CybaCowboy on 2006-05-10
[QUOTE=n3tfury][http://en.wikipedia.org/wiki/Sudo](http://en.wikipedia.org/wiki/Sudo)[/QUOTE]

Oh, interesting!

I was wondering why there was no need to login to the admin account when installing software (my admin & user accounts use the same password)...

---

