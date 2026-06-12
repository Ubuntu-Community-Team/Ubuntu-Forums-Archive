---
title: "About to attempt dual-boot"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by Wake Rider on 2007-04-28
I'm about to attempt a dual-boot. I have an 80GB hard drive with Feisty installed on a single partition. How do I repartition the hard drive 50-50 (About 40gigs each). I would also like to keep Feisty intact if that is possible. I have never done a dual boot before.:confused:  HELP!!

---

### Post by Happy_Man on 2007-04-28
All right, man, here's the deal: You go ahead and click the install icon. Go ahead, it won't bite. Answer all the questions, and then stop when you get to the part about how you want to partition. Take a deep breath, and then move the slider to choose how much space you want to allocate. Then click next. Keep going with clicking next until it starts installing. Problem solved! Don't you love Ubuntu? :D

---

### Post by Wake Rider on 2007-04-28
> **Happy_Man said:**
> All right, man, here's the deal: You go ahead and click the install icon. Go ahead, it won't bite. Answer all the questions, and then stop when you get to the part about how you want to partition. Take a deep breath, and then move the slider to choose how much space you want to allocate. Then click next. Keep going with clicking next until it starts installing. Problem solved! Don't you love Ubuntu? :D

Thanks for your advice. When you mentioned installing, were you talking about Windows or Ubuntu? Ubuntu is already on my system and I would like to install windows next to it.

---

### Post by Wake Rider on 2007-04-28
The reason I am going to a dual boot system is not because I don't love Ubuntu, it is because Ubuntu won't run any games. I have already attempted Wine but the games I was trying just wouldn't work. I am going to use Windows for the games and Ubuntu for everything else.

---

### Post by apunc1 on 2007-04-28
i think you have to install windows first because windows overwrites grub.then once you have windows you can install feisty. someone correct me if i'm wrong...

---

### Post by apunc1 on 2007-04-28
> **Wake Rider said:**
> The reason I am going to a dual boot system is not because I don't love Ubuntu, it is because Ubuntu won't run any games. I have already attempted Wine but the games I was trying just wouldn't work. I am going to use Windows for the games and Ubuntu for everything else.

have you tried codega? it's not free but i think it's more compatible

---

### Post by Wake Rider on 2007-04-28
> **apunc1 said:**
> have you tried codega? it's not free but i think it's more compatible

I know, but I'd rather not sign up to a subscription and be paying US$5 a month just to run my games. If there is anything like Cedega that is for free or a one-off payment then I'd get it.

---

### Post by Happy_Man on 2007-04-28
Oh darn. That makes things less happy. You see, Windows has a big ego (like Microsoft) and won't install itself correctly if it thinks that it isn't the only OS on the hard drive. The only thing that can be done for that is to install Windows over Ubuntu (sorry), and then reinstall Ubuntu. Then my previous set of directions will apply.

---

### Post by Wake Rider on 2007-04-28
I had to delete my Ubuntu partition, so I'll have to reset that. As soon as Windows finishes installing, what do I do when repartitioning the drive for Ubuntu, so that I don't destroy the Windows that I have just installed? I haven't done this before so I need some detailed step by step instructions please!!

---

### Post by Happy_Man on 2007-04-28
As I said: see my first set of directions...

---

### Post by Wake Rider on 2007-04-28
I have installed Windows on one large partition and I am hoping that it will not cause problems when Feisty tries to repartition it. Should I have created the partitions before I put Windows in? It is a bit late now though!

---

### Post by Happy_Man on 2007-04-28
No, you're ok. Just go ahead and repartition; it'll be fine. ;)

---

### Post by apunc1 on 2007-04-28
> **Wake Rider said:**
> I had to delete my Ubuntu partition, so I'll have to reset that. As soon as Windows finishes installing, what do I do when repartitioning the drive for Ubuntu, so that I don't destroy the Windows that I have just installed? I haven't done this before so I need some detailed step by step instructions please!!

during the install you can choose the default partition scenario and the windows partition will be resized and Ubuntu will be installed on a separate partition, plus a swap partition. or you can partition manually to allow for a /home or /documents partition, or however you want to do it. here is a tutorial [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Wake Rider on 2007-04-29
Both Ubuntu and Windows are now up and running. Thank you for your guidance everyone!!:)

---

### Post by rickggreen on 2007-04-29
There is another gret site with more in depth explanations about dual booting, grub, super gub etc  check out [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

