---
title: "How to tell which Ubuntu version is running"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by ealdaz on 2006-12-13
Dear All
I've installed Ubuntu some time ago in an older computer, I later changed it to Kubuntu and i have enjoyed using it a lot. 

However there is two things that i stumble accross everytime, these are:

1.- I have no idea how to find out what version of ubuntu/kubuntu i've actually got. That is I have no idea if it's Breezy, Hoary, etc and I can't find the version number either. 

2.- Even if i knew, i wouldn't know how to relate name to version number, is there a page in ubuntu land somewhere that relates them?

In a newer release (6.06) of ubuntu that i've installed i can find i in the documentation available in the help, but in this older ubuntu there's no ubuntu specific information in the help.

Any tips?
Thanks

---

### Post by _simon_ on 2006-12-13
If you go to System -> About Ubuntu 

It **should** tell you.

e.g. Mine says "Thank you for your interest in Ubuntu 6.10 - the Edgy Eft - released in October 2006."

If that's what you meant by "help" then sorry I don't know where else it would tell you.

There is probably a terminal command for it but if so I don't know it.

---

### Post by xyz on 2006-12-13
Also, in a terminal, I type:
```
cat /etc/issue
```
Ubuntu 6.06.1 LTS \n \l

---

### Post by ealdaz on 2006-12-13
I don't have a system -> About Ubuntu entry, 
It could be because it's kubuntu. 

In any case cat /etc/issue does work, Thank you very much !

However since i'm not sure i'll remember next time, i was wondering if anyone running a kubuntu know of a easier to remember approach?

---

### Post by xyz on 2006-12-13
How about that one! Might be Kubuntu compatible??
```
th@luser:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06.1 LTS"

```

---

### Post by civic_si on 2006-12-13
cat /etc/*release

works on almost all releases and some Unix flavors as well

---

### Post by Iowan on 2006-12-13
I'm not near my machine (which is Gnome-based) - does CTRL-ALT-F1 spill any information? (Remember CTRL-ALT-F7 to get back).

---

### Post by MountainX on 2008-02-16
How can you find out if the Ubuntu installation on a computer is the 32 bit or 64 bit version?

---

### Post by MountainX on 2008-02-16
> **MountainX said:**
> How can you find out if the Ubuntu installation on a computer is the 32 bit or 64 bit version?

found it here:
[http://ubuntuforums.org/showpost.php?p=3761242&postcount=2](http://ubuntuforums.org/showpost.php?p=3761242&postcount=2)

Check the output of:

```
uname -m
```

On 32bit you'll see i686, on 64bit you'll see x86_64.

---

