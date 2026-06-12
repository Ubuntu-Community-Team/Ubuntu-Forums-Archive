---
title: "[SOLVED] Home network. Want to connect my laptop to my desktop through router and cop"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by daimaru on 2008-02-25
i need help with networking. i want to connect my laptop to my desktop through a fritzbox router/dslmodem (wirelessly) . both laptop and desktop can ping router @192.168.178.1
funny thing is that my desktop computer can ping my laptop @ 192.168.178.30 and i can ssh into the laptop. but my laptop cannot ping or ssh the desktop @ 192.168.178.29
EDIT: ok well uhm i did not have openssh-server installed on desktop, so i guess that solves the not being able to ssh in to desktop thing, but still i cant even ping the desktop from laptop so i probably won't be able to ssh into it even with ssh-server installed (but since i don't really want to ssh and scp anyways i guess that does not matter).


all i want is to share files between the laptop and the desktop (both running ubuntu gutsy - so no windows sharing). Hope there is a graphical way cause i don't want to use scp everytime. would be nice to have my laptop and vice versa the desktop show up under network (under places). 

i turned off firestarter on both machines to see if that was interfering, but to no avail. 

need some step by step advice here :) 
if somebody could please give me some pointers on howto do, thx.

---

### Post by finer recliner on 2008-02-25
samba


EDIT:
linky: [https://help.ubuntu.com/community/ComprehensiveSambaGuide?highlight=(samba](https://help.ubuntu.com/community/ComprehensiveSambaGuide?highlight=(samba))
the guide is for connecting windows with linux, however it is easy to set it up for linux<=>linux

---

### Post by movieman on 2008-02-25
I'm not sure why you'd use samba for linux->linux mounting. Surely NFS will be easier?

---

### Post by Sproid on 2008-02-26
How so? I use samba to share with my desktop = laptop, WinXp = Ubuntu and Ubuntu = Ubuntu. Because I never understood how to use NFS for Ubuntu = Ubuntu.
I'll apreciated if someone tell me how to use NFS

---

### Post by backflip on 2008-02-26
You can't go wrong if you follow this post, before finding it I was tearing my hair out in clumps.
[http://ubuntuforums.org/showthread.php?t=574171&highlight=install+nfs&page=2](http://ubuntuforums.org/showthread.php?t=574171&highlight=install+nfs&page=2)

---

### Post by stchman on 2008-02-26
> **daimaru said:**
> i need help with networking. i want to connect my laptop to my desktop through a fritzbox router/dslmodem (wirelessly) . both laptop and desktop can ping router @192.168.178.1
funny thing is that my desktop computer can ping my laptop @ 192.168.178.30 and i can ssh into the laptop. but my laptop cannot ping or ssh the desktop @ 192.168.178.29
EDIT: ok well uhm i did not have openssh-server installed on desktop, so i guess that solves the not being able to ssh in to desktop thing, but still i cant even ping the desktop from laptop so i probably won't be able to ssh into it even with ssh-server installed (but since i don't really want to ssh and scp anyways i guess that does not matter).


all i want is to share files between the laptop and the desktop (both running ubuntu gutsy - so no windows sharing). Hope there is a graphical way cause i don't want to use scp everytime. would be nice to have my laptop and vice versa the desktop show up under network (under places). 

i turned off firestarter on both machines to see if that was interfering, but to no avail. 

need some step by step advice here :) 
if somebody could please give me some pointers on howto do, thx.

I have had much luck with Ubuntu to Ubuntu sharing using pyNeighboorhood.

[http://www.stchman.com/share.html](http://www.stchman.com/share.html)

---

### Post by stchman on 2008-02-26
I was browsing the web and this guy has a tutorial.

[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

Very nicely done.

---

### Post by daimaru on 2008-02-29
thanks everyone for the replies, I'll go with samba then.

---

