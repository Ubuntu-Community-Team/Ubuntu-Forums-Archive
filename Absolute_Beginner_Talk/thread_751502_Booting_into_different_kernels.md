---
title: "Booting into different kernels"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by howiehowie93 on 2008-04-10
Greetings,
I've been using ubuntu for about a year and doing good TY.

I installed Gutsy on a frined 'pooter a month back an run into a strange problem yesterday after an update. 
after the update it refuses to boot past the first ubuntu splash  screen with the orange progress bar. it halts with just a hint of orange showing.

i was able to edit grub and found several  entries:

kernel 2.6.22-14-generic
kernel 2.6.20-16-generic

2.6.22-14 is the halting default and if i change it to kernel 2.6.20-16-generic it will boot up as normal.

I'm not too bothered about the why now I've the machine running - she just uses it for e-mail & surfing. but worried about not being able to use the latest kernel and what ever benefits that includes.

Do I need to be enabling it to boot into the latest Kernel and if so what should I do about it?


thanks very much in advance

Howie

---

### Post by stim on 2008-04-10
Howie, 
   I had the exact same problem with my XPS 410: 2.24 Generic would hang and 2.20 would work just fine.     This only happened after I let the autoupdater do its thing :lolflag:  

  I found that there is no real difference in performance or otherwise between the kernels, sure there may be some security updates, but if you cant load the OS it doesn't really matter.  

  In my case, I had commented everything out of my menu.lst file except for 2.24 Generic, so it was kind of a hassle to get it working again.... :mad:  learned my lesson on that one.

  If it works, let it alone.  This is not the first time that updates to the kernel have broke or seriously buggered parts of my system. Moral of my story: dont update the kernel\headers.   
 
Hope this helps.

---

### Post by howiehowie93 on 2008-04-10
Stim,
an awesomley quick reply thanks.

regards
Howie

---

