---
title: "New Linux User : Advice On Nvidia Drivers Please."
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by AdyE on 2007-01-19
Hi, I have been using Ubuntu for about a day and was wondering about drivers for an Nvidia Geforce 7600 GT graphics card.
Do I have to install specific Linux drivers for it to work properly and if so which one do I need for Ubuntu?
There is 1)Linux IA32, 2)Linux AMD64/EM64T, Solaris x64/x86 and 4)FreeBSD to choose from.Any help would be appreciated.
Thanks,
Ady.

I have an ASUS A8N SLI Mobo, Nvidia Geforce 7600 GT, AMD Athlon64 3800+, 250GB Sata2 HD and 1 GB of Ram.

---

### Post by %hMa@?b&lt;C on 2007-01-19
> **AdyE said:**
> Hi, I have been using Ubuntu for about a day and was wondering about drivers for an Nvidia Geforce 7600 GT graphics card.
Do I have to install specific Linux drivers for it to work properly and if so which one do I need for Ubuntu?
There is 1)Linux IA32, 2)Linux AMD64/EM64T, Solaris x64/x86 and 4)FreeBSD to choose from.Any help would be appreciated.
Thanks,
Ady.

I have an ASUS A8N SLI Mobo, Nvidia Geforce 7600 GT, AMD Athlon64 3800+, 250GB Sata2 HD and 1 GB of Ram.
it all depends upon which linux you are running. If you are running 64 bit then you want AMD64 if you are running 32 bit then you want LinuxIA32. either way, you could just use automatix though.
if you dont want to use automatix, at least give me the output of 
"uname -a"

---

### Post by AdyE on 2007-01-19
> **jeffc313 said:**
> it all depends upon which linux you are running. If you are running 64 bit then you want AMD64 if you are running 32 bit then you want LinuxIA32. either way, you could just use automatix though.
if you dont want to use automatix, at least give me the output of 
"uname -a"

I am running Ubuntu 32 bit.
I am afraid I dont know what automatix or "uname -a" means. Sorry. Am a total noob.

---

### Post by taurus on 2007-01-19
[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by %hMa@?b&lt;C on 2007-01-19
> **AdyE said:**
> I am running Ubuntu 32 bit.
I am afraid I dont know what automatix or "uname -a" means. Sorry. Am a total noob.
"uname -a" is a command from the terminal that shows info about your kernel, so i could direct you to the proper driver
automatix is a program to download abdinstall things easily for you
[www.getautomatix.com](www.getautomatix.com)
if you at all feel that you might screw up installing the drivers, I would use automatix!

---

### Post by BillGod on 2007-01-19
I would use automatix to install it.  Much easier.

[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

just install the .deb file and run it from applications\systemtools. It will install it and configure it for you.

---

### Post by AdyE on 2007-01-19
@ everyone ... Thank you very much. I will try automatix :-)

Linux  2.6.15-27-386 #1 PREEMPT Fri Dec 8 17:51:56 UTC 2006 i686 GNU/Linux

---

### Post by enopepsoo on 2007-01-19
envy is better than automatix, it is a bit more advanced though.  I would suggest using the Alberto Milone link above. :guitar:

---

### Post by %hMa@?b&lt;C on 2007-01-19
> **enopepsoo said:**
> envy is better than automatix, it is a bit more advanced though.  I would suggest using the Alberto Milone link above. :guitar:
what is envy. would you please provide me with a link?

---

### Post by taurus on 2007-01-19
Look at Post #4.

---

### Post by %hMa@?b&lt;C on 2007-01-19
> **taurus said:**
> Look at Post #4.
sorry, i should read before i post:lolflag:

---

### Post by bodhi.zazen on 2007-01-19
I run the same card and the beta driver (from envy) is the way to go :p

---

### Post by deanjm1963 on 2007-01-19
Envy is definately the way to go, very easy to install and use, it does all the hard work for you.

---

