---
title: "Kernels"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by sweeper on 2006-06-05
I have an AMD64 (the older type) I am using 32 bit Ubuntu, I don't know what kernel it has or if it is worth changing to K7 if I don't have K7, so..
1 how do I check which kernel?
2 is it worth changing to K7?
3 how do I do it, if it is worth it?

Thanks :)

---

### Post by frodon on 2006-06-05
1- Using the command "uname -a"
2&3- You should use this kernel if you have like me an AMD64 with the 32bit kernel, you may increase your performances. To do it run a :  ```
sudo apt-get install linux-k7
```and reboot.

---

### Post by sweeper on 2006-06-05
[QUOTE=frodon]1- Using the command "uname -a"
2&3- You should use this kernel if you have like me an AMD64 with the 32bit kernel, you may increase your performances. To do it run a :  ```
sudo apt-get install linux-k7
```and reboot.[/QUOTE]

Thank you very much :)
I had the 686 kernel now I have 

*Linux ubuntu 2.6.15-23-k7 #1 SMP PREEMPT Tue May 23 14:20:54 UTC 2006 i686 GNU/Linux*

It mentions 686 but I assume it is the K7 kernel.

---

### Post by frodon on 2006-06-05
Yes, it is the k7 kernel ;)

By the way i forgot to give you the link to a forum guide which could provide you more informations : 
[http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)

---

### Post by sweeper on 2006-06-05
> **frodon]Yes, it is the k7 kernel  said:**
> http://ubuntuforums.org/showthread.php?t=85917[/url]

Thanks Frodon :)

---

