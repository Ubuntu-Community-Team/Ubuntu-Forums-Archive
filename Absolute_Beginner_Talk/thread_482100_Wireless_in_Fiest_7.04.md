---
title: "Wireless in Fiest 7.04"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by theproject on 2007-06-23
I've used (afraid to say this) Wubi to install linux inside Windows vista, when i boot up it acts like a duel boot. I didn't understand LiveCD's at all, apparently they didnt work. When i pop them in and reboot it comes up with the ubuntu screen, with al the options, i pick "start/instal Ubuntu" and then it says loading in the top left corner, and stays like that. I left it for about 2hrs, with no change. The CD just kept going around and around. I would realy like to get a secure duel boot enviroment, if any1 has EASY steps for that. I've read alot but nothing is working...Anyways with my wubi Ubuntu it has everything a normal Ubuntu has but im starting to suspect issues with wireless, or drivers that come with official ubuntu dont come with wubi ubuntu?? I have a Belkin router, with comcast service, i use my computer in the basement, router is on the second floor, it works perfectly on Windows Vista, no issues at all. But when im on Linux, it doesnt even have any wireless showing, when around my house on vista theres over ten with strong signals. I have WEP Hex Pairs generated security, i typed all that in DHCP works with vista, so i choose that as well, i click connect and nothing happens. Im very confused, i hear its a driver thing and what not. I need simple steps if thats possible, im very new to Ubuntu/Linux in general. I just installed it yesturday, but to get any further in my Linux experiance i need the internet...
Thank you for any future help.

---

### Post by gn2 on 2007-06-23
Have you read this: [https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#wireless](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#wireless) ?
.
Particularly the bit about Unsupported Wireless Cards.

---

### Post by theproject on 2007-06-23
Yea...Im must be missing something, a lot of websites say install the nswrapper or w/e, but how can you download and install if you cant connect to the iternet??? I dont get it

---

### Post by gn2 on 2007-06-23
> **theproject said:**
>  how can you download and install if you cant connect to the iternet???
.
Perhaps try downloading while booted into Windows, and save to flash drive?
.
Or connect to wired ethernet to get the wireless sorted then switch to wireless?

---

### Post by theproject on 2007-06-23
Yea that worked, but since it was wubi, i let my power drain, and everything shut down....*hit myself on the head*....Anyways i'd realy like to learn how to use a Live CD and make it work. Either Fedora7 or Ubuntu Feisty

---

### Post by gn2 on 2007-06-24
Sometimes Live CD's just don't get on with the hardware, which is where the additional boot parameters available through pressing F6 at boot time help. e.g. noapic nolapic. etc.
.

---

