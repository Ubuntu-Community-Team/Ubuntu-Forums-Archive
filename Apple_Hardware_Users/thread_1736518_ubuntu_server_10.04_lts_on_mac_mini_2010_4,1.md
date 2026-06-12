---
title: "ubuntu server 10.04 lts on mac mini 2010 4,1"
date: 2011-04-22
forum: Apple Hardware Users
---

### Post by acroix on 2011-04-22
greetings,

i like to run my mac mini 2010 edition with ubuntu server 10.04 lts. i did this successful with 10.10 server which recognized the new motherboard. 10.04.2 lts unfortunately does not boot the mac mini.

is there a documented way to create a boot cd that uses the 10.04 lts base system with the newer 10.10 kernel?

thank you,

a.

---

### Post by acroix on 2011-04-24
BUMP.

Is there really no on one who can give me a hint? Thank you.

---

### Post by mondo2k on 2011-04-24
Could you try downloading and using the daily build of 11.04 Natty?

[http://cdimage.ubuntu.com/ubuntu-server/daily/current/](http://cdimage.ubuntu.com/ubuntu-server/daily/current/)

---

### Post by acroix on 2011-04-24
mondo2k: Thank you for your response.

Yes, I could but I like to take advantage of a LTS release as I intend to use the mac mini in a small office environment and stability is key.

a.

---

### Post by mondo2k on 2011-04-24
I don't believe the October release (10.10) is LTS. When I recently did a Terminal dist-upgrade from Ubuntu server 8.04.1 PPC, it only upgraded me to 10.4 (kernel 2.6.32-31), the last LTS I know of. 

However, doing a search for ubuntu-10.10-server-powerpc.iso, I found a copy on a (Thailand?) mirror. [http://mirror1.ku.ac.th/ubuntu-maverick/]("http://mirror1.ku.ac.th/ubuntu-maverick/")

---

### Post by acroix on 2011-04-25
!?

---

### Post by mondo2k on 2011-04-25
I feel the same way, but the software's there if you want it. I just don't think it, or any 10.10 version, is LTS. Ubuntu gurus please correct me if I'm wrong.

---

### Post by Lars Noodén on 2011-04-26
You might leave a small OS X partition and make it dual boot.  Then use [rEFIt](http://refit.sourceforge.net/) to set it to boot from [Ubuntu LTS](http://refit.sourceforge.net/) by default.  That's how I have set up various Mac Minis.

---

### Post by acroix on 2011-04-26
I might have expressed myself poorly, so I give it another try.

I have the newest mac mini model called 4,1 or mid 2010 which is an intel mac.

This mac mini has a new motherboard that was not supported by Ubuntu 10.04 LTS. I got it to work with Ubuntu Server 10.10 though, which is -not- a LTS release.

My question was and still is: is there a documented way to modify 10.04 LTS with the kernel found in 10.10 so I can use the Long TIme Support version with my mac mini.

Basically, 10.10 kernel + 10.04 base system onto 1 boot cd = me a happy camper.

Thank you for reading my post.

a.

---

### Post by pauljwells on 2011-04-26
Mixing kernels and base systems won't give you an LTS, so why bother?
10.10 will be supported until long after the next LTS is released and it is already stable enough. Don't make life harder than it need be!

---

### Post by Lars Noodén on 2011-04-27
> **acroix said:**
> 
My question was and still is: is there a documented way to modify 10.04 LTS with the kernel found in 10.10 so I can use the Long TIme Support version with my mac mini.


You could try [apt-pinning](http://www.howtoforge.com/a-short-introduction-to-apt-pinning), there are a lot of [apt-pinning](http://jaqque.sbih.org/kplug/apt-pinning.html) tutorials.  It won't give you LTS, if you run a different kernel, though.

---

### Post by acroix on 2011-04-27
Thanks Lars, that is what I was looking for! I do understand that this will not give me an official LTS but it would be as close as it gets with only the kernel being different.

Thanks again,

a.

---

### Post by cottfcfan on 2011-04-27
Don't know if this is what you need, but if you enable the backports on 10.04 lts, the 2.6.35 kernel is in the repos, which is the one that 10.10 uses.
That may help.

---

### Post by acroix on 2011-04-27
Thank you, cottcfan, I'll give that a try too. a.

---

