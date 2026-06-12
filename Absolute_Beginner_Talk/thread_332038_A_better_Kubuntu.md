---
title: "A better Kubuntu?"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by gigaferz on 2007-01-05
Hello everybody!!!

I tried simply mepis and I liked it, but I was even more excited when I found that is also debian and ubuntu dapper based!!!

anyway..I was wondering if all the repositories of ubuntu  and if some of the instructions to fix problems would work on simplymepis?

P3 800mhz
320 ram

---

### Post by mahy on 2007-01-05
the answer is a firm NO! ;)

---

### Post by gigaferz on 2007-01-05
Opps!!

Well I forgot to mention that i  got that from a website , where they try several kde distros on an IBM T20.
And simply mepis won on the score..followed by kubuntu.. :P

anyway, as Im posting this im downloading the kde on my ubuntu, hopefully in the next hour or so ill find out.

---

### Post by louieb on 2007-01-05
> **gigaferz said:**
> Hello everybody!!!
anyway..I was wondering if all the repositories of ubuntu  and if some of the instructions to fix problems would work on simplymepis?

Most probably will. Its all Linux. I have gotten a few packages from Debian like Glipper and not had a problem yet. But there is no warranty. There is some difference in where some things are found that varies by distribution.

---

### Post by gigaferz on 2007-01-06
Ive been trying for so long to make any x,k,(flx),ubuntu on my poor old ibm t20.

Ubuntu,fluxbuntu and xubuntu froze during the livecd.
However the Kubuntu I burned this morning made it!!!!

But when it comes to wireless.. it;s enabled and everything, but it tells me there is a manual radio button  outside the computer..well bottom line it didnt work!

I tried kubuntu on a newer machine, but its a broadcom modem..and when i try to enable it it goes back to disabled...

In this newer computer Simplymepis failed too...

But in the t20 the wireless is runnig out of the box!!!

I feel so much better now, theres more life to this old computer now.

Bytheway where do i find..something like .."the ultimate wireless troubleshooting guide for ubuntu,(or at least for linux)?

---

### Post by aysiu on 2007-01-07
The major difference in terms of instructions to fix problems--Ubuntu uses *sudo*. Mepis uses root.

So when instructions here say something like ```
sudo apt-get update
sudo apt-get install *packagename*
``` you would do this in Mepis instead: ```
su
apt-get update
apt-get install *packagename*
exit
```

---

### Post by gigaferz on 2007-01-08
ok..that explains a lot....

anyway.. it was not my intension to say mepis is better. 

its missing some applications in the gui, i cant find where to configure the network devices,or a wlan assistant.

however kubuntu is more complete but didnt detect my "unknown wireless card".

And so far i have not found a way to make work this broadcom integrated card  802.11g wireless network adapter.

Any links for something like this?

ive ben searching a lot , but nothing yet.

thank you !

---

### Post by aysiu on 2007-01-08
Well, since Mepis is now using Ubuntu repositories, you could probably install any one of [these *wlan* assistants](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=wlan&searchon=name&subword=1&version=all&release=all) using Synaptic Package Manager.

---

