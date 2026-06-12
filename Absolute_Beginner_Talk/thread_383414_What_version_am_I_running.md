---
title: "What version am I running?"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by RandyOldgeek on 2007-03-13
I installed Ubuntu a few weeks ago and then added Kubuntu because a software package I wanted to run only worked on Kubuntu.  It was supposed to run on Ubuntu 6.10 but only the version that runs on 6.06 would run......so:

I am trying to figure out what the heck version of Ubuntu is on this machine.  Is there someplace I can look to see?  And in that same vain....if it is 6.06 how can I upgrade to 6.10??

Thanks for any help on this. 

Randy

---

### Post by AndyCooll on 2007-03-13
In a terminal type:
```
uname -r
```

:cool:

---

### Post by Kateikyoushi on 2007-03-13
Copy this to terminal and you will know which version are you running.
```
cat /etc/lsb-release
```

To upgrade read this page. [LINK]("https://help.ubuntu.com/community/EdgyUpgrades")

---

### Post by RandyOldgeek on 2007-03-13
Thanks.....those both worked!!! \\:D/

---

### Post by ardchoille42 on 2007-03-13
```

lsb_release -a

```

---

### Post by theophiles on 2008-02-22
how fascinating. So many different ways to do the same thing!

---

### Post by SOULRiDER on 2008-02-22
> **theophiles said:**
> how fascinating. So many different ways to do the same thing!

Indeed!
Actually, uname -r will show the kernel version while the other will show the release name.

---

### Post by frankos44 on 2008-04-08
Be nice to know from via ssh if it told you if you are running 64bit or 32bit? Sometimes when visiting a server you worked on ages ago you just dont remember. Ive been using phpinfo() to discover but there dont like sending detailed info over web using browser.

---

### Post by stchman on 2008-04-08
> **RandyOldgeek said:**
> I installed Ubuntu a few weeks ago and then added Kubuntu because a software package I wanted to run only worked on Kubuntu.  It was supposed to run on Ubuntu 6.10 but only the version that runs on 6.06 would run......so:

I am trying to figure out what the heck version of Ubuntu is on this machine.  Is there someplace I can look to see?  And in that same vain....if it is 6.06 how can I upgrade to 6.10??

Thanks for any help on this. 

Randy

KDE packages run very well on Gnome.  What package was it that said you needed Kubuntu?  I run many KDE apps on Gnome.

---

