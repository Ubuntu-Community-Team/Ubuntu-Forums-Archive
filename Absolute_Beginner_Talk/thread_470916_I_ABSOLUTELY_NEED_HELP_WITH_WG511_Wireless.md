---
title: "I ABSOLUTELY NEED HELP WITH WG511 Wireless"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by atupeck on 2007-06-11
I am VERY new to Ubuntu or even Linux itself. I have a netgear wireless card, WG511 v2. I am at a loss on how to install ndiswrapper. I found a website or a program called active matix (or i believe that is the name) and it installed ndiswrapper for me... But i tried the website i believed i went to, to get it working; it wasn't there. But anyway, is there someone that can help me install ndiswrapper step by step? Please, I need help!

Ubuntu 6.06LTS is the Ubuntu Version. 

As for the wireless card, I have the correct .inf driver files for windows XP and I have the .sys files as well. Help please!

Thank you in advanced,

atupeck

---

### Post by drs305 on 2007-06-11
Quick and dirty solution:

Try running this from terminal and see if it starts working. I have a WG511T and have it working in Feisty but I think I had it running in Edgy as well.

```

sudo aptitude install linux-restricted-modules-$(uname -r)

```

---

### Post by jcronkhite on 2007-06-11
You may want to install Ubuntu 7.04.  Wireless connectivity was a major focus of this release.  I've been thoroughly impressed with the ease of use when connecting to wireless networks.  Go to [http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download") and download the latest version for your platform if you'd like. :p

---

### Post by adampyre on 2007-06-11
Hey, this will tell you how to get your wireless going. You need to make sure build-essential is installed in order to compile ndiswrapper and get it going. I wrote up a how to on this, it will tell you step by step exactly how to do it from start to finish. Follow all the steps and your wireless should be working Let me know if this helps!:

Note, it starts out telling you how to partition the hd and install Ubuntu, skip to the part that starts with installing BUILD-ESSENTIAL
[http://ubuntuforums.org/showthread.php?t=458415](http://ubuntuforums.org/showthread.php?t=458415)

- Adam

---

### Post by atupeck on 2007-06-11
Thank you all for your help, i'm gonna take the advice on to update to ubuntu 7, fiesty. Then I will follow the directions posted to get the wireless working...hopefully i have success, I have seen WAY too many people not able to get this card to work... But...heres to hoping! Thank you all!

---

### Post by atupeck on 2007-06-11
I also have another question... Have any of you heard of using a program called activematix? It was kinda like the "add/remove" program buttons under the main applications menu... Im searching for this piece of software again. I'm not sure if im spelling it right though, so if anyone has heard of it, post please!

---

### Post by jcronkhite on 2007-06-11
I think you mean Automatix.  Go to [http://www.getautomatix.com/]("http://www.getautomatix.com/") to get it.

---

