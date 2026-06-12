---
title: "How secure is a newly installed Ubuntu?"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by MatsB on 2006-02-17
Basic question for you gurus


How secure is a newly installed Ubuntu? I need some advice on what I should do to increase the security. I&#8217;m not asking for totally secure system but maybe some hints on basic things I should consider. Keep in mind I'm a newbe in the Linux world.

As an example when I port scan my Ubuntu PC I see that NetBIOS ports are open (I guess Samba is running by default). How do shutdown Samba? /etc/init.d/samba stop desn't work.

Thx

---

### Post by frodon on 2006-02-17
Ubuntu is secure enough, but if you're really scared you can install a firewall (firestarter is a really good one), it will close all your ports.
You could also go in System>Administration>services and disable the services that you don't need, for exemple i don't use mail servers on my computer so i disabled postfix.

Don't worry ;)

---

### Post by Clark Nova on 2006-02-17
I was wondering this myself, I'm not too wooried about viruses in Linux but I guess a firewall would just be common sense. I'll have a look at Firestarter this evening then:)

---

### Post by MatsB on 2006-02-17
Can't seem to find Samba in System>Administration>services? Is there another way I can shutdown Samba?

running ps -ef really doesn't show that Samba is running but I still see the open NetBIOS ports???

---

### Post by daacosta on 2006-02-17
[QUOTE=MatsB]Basic question for you gurus


How secure is a newly installed Ubuntu? I need some advice on what I should do to increase the security. I’m not asking for totally secure system but maybe some hints on basic things I should consider. Keep in mind I'm a newbe in the Linux world.

As an example when I port scan my Ubuntu PC I see that NetBIOS ports are open (I guess Samba is running by default). How do shutdown Samba? /etc/init.d/samba stop desn't work.

Thx[/QUOTE]

I am not a guru but I wholeheartedly recommend you to read Ubuntu's impartial review at [www.distrowatch.com](www.distrowatch.com) where the firewall installatin is discussed as well as the management of groups and users (The author advices you to create an account with little priviledges...)

---

