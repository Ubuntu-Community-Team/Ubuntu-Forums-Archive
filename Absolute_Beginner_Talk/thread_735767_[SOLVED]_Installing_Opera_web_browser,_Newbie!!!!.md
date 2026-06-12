---
title: "[SOLVED] Installing Opera web browser, Newbie!!!!"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by adriand2000 on 2008-03-26
I downloaded the newest version of Opera for Linux i386.  When I click on it to download it I get an error: "wrong architecture i386".  I assumed I downloaded the correct Opera since it was the one they suggested when I went to the download page.  I tried using add/remove applications to install it and it says that it can't be installed on my computer type, amd64.  How is my computer type an amd64 when I have an Intel core 2 duo processor?  Am I out of luck installing Opera or is there something I need?  Any help with this would be great!  I just installed Ubuntu yesterday so I'm trying to learn as much as I can.

Thanks,
Adrian D.

---

### Post by Oldsoldier2003 on 2008-03-26
> **adriand2000 said:**
> I downloaded the newest version of Opera for Linux i386.  When I click on it to download it I get an error: "wrong architecture i386".  I assumed I downloaded the correct Opera since it was the one they suggested when I went to the download page.  I tried using add/remove applications to install it and it says that it can't be installed on my computer type, amd64.  How is my computer type an amd64 when I have an Intel core 2 duo processor?  Am I out of luck installing Opera or is there something I need?  Any help with this would be great!  I just installed Ubuntu yesterday so I'm trying to learn as much as I can.

Thanks,
Adrian D.

what is the output of 
```
uname -a
```

---

### Post by adriand2000 on 2008-03-26
Linux A-Desktop 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux

---

### Post by iSplicer on 2008-03-26
It seems that you are using the x64 version of Ubuntu, you should get the x64 version if it is offered. Or, you could simply use FireFox

---

### Post by Khalis7 on 2008-03-26
> **adriand2000 said:**
> Linux A-Desktop 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux

It's clear that your using 64-bit Ubuntu OS. So, try get Opera 64bit from their website if is available.

---

### Post by adriand2000 on 2008-03-26
Thanks for the help!!  I'm just going to download the i386 version and install that one instead.  Seems like more things work with the i386 anyway.

---

### Post by fbg111 on 2008-03-30
Is there a repository for x86-64 Linux Opera?  Even an unstable repo for the 9.5 build?

---

### Post by zvacet on 2008-03-30
You can look [here](ftp://ftp.opera.com/pub/opera/linux/950b/final/en/x86_64/) or [here.](http://snapshot.opera.com/unix/snapshot-1887/x86_64-linux/)

---

