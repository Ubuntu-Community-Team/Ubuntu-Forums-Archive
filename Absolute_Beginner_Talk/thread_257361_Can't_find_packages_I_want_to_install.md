---
title: "Can't find packages I want to install"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by uselessnobody on 2006-09-14
Hi all!  First post so please bare with me...

I just finished installing ubuntu dapper drake as a dual boot on my dell inspiron 6000 laptop, and am trying to configure the intel wireless card (2195 abg) to work with my d-link wpa-psk/tkip wireless router.

I tried following the guide to install network manager as a package posted on [this other thread]("http://www.ubuntuforums.org/showthread.php?t=125150"), but I can't find network manager in synaptic and when I try to use apt-get I get an error that says something like:

E: Couldn't find package.

even with the ubuntu cd in my drive.  Could someone lend me a hand as to what I might be doing wrong?  Is it looking at the wrong path?  And why wouldn't it be listed in synaptic?

Thanks in advance!

---

### Post by oedipuss on 2006-09-14
Synaptic gets its package lists from online repositories. By default only the officially supported are used, 'main' and 'restricted'. 
However there are two more which hold a great amount of unsupported but stable enough software, 'universe' and 'multiverse' . The package you're looking for could be in the universe repository.

Check out [this page]("https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html#id2542172") for instructions on how to use the extra repositories.

---

### Post by Najand on 2006-09-14
Click:
System -> Administration -> Software Properties and check all unchecked repositories. Then run:
```

sudo apt-get update &&  sudo apt-get upgrade

```

---

