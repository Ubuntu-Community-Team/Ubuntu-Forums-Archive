---
title: "Various issues"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by Kharun on 2007-03-09
Hello all!

Prepare for a loooooong read....

For a long time I've wanted to install a Linux Distro, and after fiddling around for a couple months, I decided to order an Ubuntu 6.06 LTS disk. I finally got it and decided last night around midnight that I was going to install it. The installation went pretty well, popped in the live disk and installed no problem. But when I rebooted, it would hang at unpacking Linux, and would say something about IRQ #169, and that "nobody cared" :( . It said something about booting with irqpoll, so I rebooted, and edited the boot file, and added that to it. It booted no problem. After fiddling around, I wanted to reboot for some reason. I thought it wouldn't be a problem, but that "nobody cared" thing came up again. So here's my first question:

How can I get the irqpoll to stay in the kernel loading thing so I don't have to put it in every time I boot?

Onto the second story/question:

Ok, so I went to do as I always do with a new installation, install drivers. I already went and got a driver for my graphics card, and have a general idea on how to install that. My big issue with driver installation is for my NETGEAR WG311T. I went to the networking place, went to the ath0 (wireless connection) and went to the properties. I found my wireless connection in the list of available connections, and put in the WEP key that I use. And for the address, I selected DHCP, which is also what I'm using. But I can't connect to my router.

Do I need to search for a Linux version of the WG311T driver, or am I going to have to run some cable through the floor and go wired?

Thanks ahead of time for the help,

BRT

---

### Post by lamalex on 2007-03-09
This isn't really a 'fix', but worth a try. download 6.10 edgy and give that a go. I've had MUCH better luck with edgy than dapper, others will tell you the opposite but in my experiance edgy has worked a lot better. Your best bet is to back up stuff you need then do a clean install, dapper to edgy upgrades can get a little bit messy. Not always, but i've seen quite a few ugly ones.

---

### Post by Kharun on 2007-03-09
No backing up needed, nothing is installed...

I might give it a try later on, I'm gonna fiddle with it a little more

---

