---
title: "What is the perpose of sudo?"
date: 2005-06-03
forum: Absolute Beginner Talk
---

### Post by allforcarrie on 2005-06-03
I changed my root password, I dont like the whole sudo thing...

---

### Post by karthik085 on 2005-06-03
root access

---

### Post by GrumpySimon on 2005-06-03
Sudo (Super-user do) provides an easy way of temporarily getting super user (ie: root) access. 

So... why has the root account been disabled in Ubuntu?

It's long been considered a bad thing to use a root account for most things, basically because the risk of screwing things up by mistake is very high. It's been stressed for a long time that you should use sudo to temporarily get superuser status. 

The other reasons the [Wiki page](http://www.ubuntulinux.org/wiki/RootSudo) mentions, are that no root account makes brute force attacks harder, most new users don't know what a 'root' account is (or when to use one), and allows the super user account to be easily transferred.

It is very easy to get yourself a root terminal:
```

sudo su

(or)

sudo bash

```


and it's also very easy to re-enable it:
```

sudo passwd root

```

--Simon

---

### Post by YopY on 2005-06-03
Sudo is basically to do something as root without logging in as root. Simple as that, its main purpose is to secure your system and prevent users from being logged in as root all the time, a common problem in Linux-based operating systems.

See, when you're root,you can do anything - usually screw up your computer. 

With the use of sudo, you don't need the Root account anymore, or at least you don't need to log out and in again or start up a virtual thingy in order to do something.

---

### Post by XDevHald on 2005-06-03
>  With the use of sudo, you don't need the Root account anymore.

With that being said, how would you sudo if root is sudo with backend access? I don't think saying that line is a promise for the user due to them probably deleting the root account, but I do see what you meant by that ;)

With sudo being a fun topic to enjoy, it's not recommended but useful hence not safe as well. Now **su **on the other hand is a more complete run around of being root instead of free falling with no password and pretty much anything goes if you're not ready for out of the unordinary tricks to happen to you without knowing.

If you're needing a file that is not letting you have access, then feel free to sudo gedit /directory to file, but please don't make this a habit, it can lead to more things if you're not careful.

---

### Post by odin on 2005-06-06
If using sudo you can do all the root "tasks" then you can also screw yhe system up anyway,dont you(I)?It is like that or are there any restrinctions using it?

---

### Post by Alexander Kirillov on 2005-06-06
[QUOTE=odin]If using sudo you can do all the root "tasks" then you can also screw yhe system up anyway,dont you(I)?It is like that or are there any restrinctions using it?[/QUOTE]
 Yes, you can.  
But sudo forces you to type "sudo" and enter your passwors whenever you are trying to do something that requires root privileges - so if you see this prompt, you know that you are messing  system configuratin. Makes accidental mistakes  less likely.

---

### Post by Sionide on 2005-06-06
I must admit that I sometimes forget to put 'sudo' in front of the command I'm trying to do but I guess I'll get used to it. It's just a different way of doing it, there's nothing especially wrong with it unless you're used to having root all the time.

---

