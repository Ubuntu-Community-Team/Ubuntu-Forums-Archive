---
title: "Slow DNS lookup with Gutsy"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by john262 on 2007-10-25
When I open Firefox and browse to a website, it usually sits there for a while saying "looking up Google.com" or whatever the website is. I have a dual boot system and when I boot into Windows XP that doesn't happen. The DNS lookup is fast. But with Ubuntu it's slow. And it doesn't seem to remember DNS settings either. If I close the domain the I browsed to, then reopen it a minute later it usually takes a long time again to look it up.

Does anyone know what's gouing on here?

Thanks,

John

---

### Post by john262 on 2007-10-26
OK, I searched the forum (which I should have done in the first place) and found that I had to disable IPV6. Now it's OK.

---

### Post by salvador24 on 2007-11-06
I also had this problem and attempted to fix it by disabling IPv6, but that didn't work for me, and neither did changing DNS servers to OpenDNS.  However, in my searching of the internets I did find this bug:

[https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/156720]("https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/156720")

Seemed to explain my problems, so I enabled the -proposed repository and downloaded only the libc updates from it.  Enabled my ISP's DNS servers, and... problem solved!  Now internets are just as fast as they were in Feisty.  Hope this works for you.

---

### Post by moe_syzlak on 2007-11-29
this prolem has been solved here ---> [http://ubuntuforums.org/showthread.php?t=616744](http://ubuntuforums.org/showthread.php?t=616744)

please search the forums for a solution BEFORE asking for help. many problems advanced and some of the noob problems (such as "how do i get root on my computer," or "how to install xxxxx package" that is in the repository) have been fixed. and you can get the answers to your problem by searching

---

