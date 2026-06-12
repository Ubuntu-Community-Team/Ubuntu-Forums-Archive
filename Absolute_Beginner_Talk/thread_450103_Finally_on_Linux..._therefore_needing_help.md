---
title: "Finally on Linux... therefore needing help"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by _deneb_ on 2007-05-21
Hi everybody..today I did it. No more Blue or Red Screens Of Death.. just UBUNTU!! ::KS

Anyway.. of course I'll be needing some help because I unfortunately I never used Linux and I really want to learn fast.

So.. I got some litl questions : 

1) I installed Dapper Drake (6.06) and when I got connected I downloaded and installed all the updates the system suggested. Does this mean that now I have the latest Ubuntu? 7.04... Feisty isn't it? How can I check it?

2) I'm registered to live365 and I want to play those remote playlists. I tried with XMMS and something else but I can't hear them, they don't work. Any suggestions? I would like something starting from the browser.. 

3) I would like to see online videos... like those of Nba.com for example. I installed some players using sinaptyc but I still can't see anything. Any suggestions? 

Thanks a lot.... 

CYA!
_deneb_

---

### Post by aysiu on 2007-05-21
#1. If you install all the updates, you have 6.06 still... just with security patches.

---

### Post by blackened on 2007-05-21
1) Go to System -> About Ubuntu, then select Version And Release Numbers. This should explain how Ubuntu numbers its versions, and also what version you are currently using.

2) If you're intent on using the latest version of Ubuntu, then I would ask this again when you install Feisty (because I assume you're still running Dapper). For Dapper start reading [here]("http://doc.gwos.org/index.php/MultimediaCustomizationGuide#FIRST_STAGE_:_MAKING_YOUR_SOURCES.LIST_READY"). Or you can install most of the necessary things through Automatix (see [here]("http://http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_6.06_.28Dapper_i386.29") and choose the package relevant to your architecture).

3) Most of this should be possible after completing #2.

---

### Post by _deneb_ on 2007-05-21
> **aysiu said:**
> #1. If you install all the updates, you have 6.06 still... just with security patches.

Oh... well.. I tried to upgrade to the 7.04 with the Upgrade Manager but it says that my version is up-to-date. Why? Shall I try using something else?

---

### Post by esoterica on 2007-05-21
If it's a brand new install already anyhow and you want version 7.04 why not just download the 7.04 ISO file and install 7.04 right from the start. This will make your system a lot cleaner for you. I'd do this rather than just trying to update another version you already have installed. The only time I'd suggest doing otherwise is if you already had the other version all set up and configured over an extent of time where doing an upgrade would only make more sense.

Either way you choose to go above, it sounds like though you're then going to want to follow these instructions, they'll get you there with no problems and no strange or hard to follow steps...

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by jiminycricket on 2007-05-21
LTS (long-term support) Dapper Drake only offers updates to other LTS releases.  

You have to type something in the terminal to upgrade to Feisty Fawn.  Anyway, you must go from Dapper -> Edgy -> Feisty; you can't upgrade directly.

First of all make sure all Dapper Drake updates are applied.  Then,

```
gksudo "update-manager -c -d"
```

---

### Post by Gmbrdilos on 2007-05-21
correct me if I am wrong:

sudo apt-get upgrade

in the terminal to upgrade to fiesty (seriously why install dapper on a new install?)

---

### Post by _deneb_ on 2007-05-21
Thx everybody..

I'll check if it is better to upgrade via terminal or downloading the new one

I'll let you know

_deneb_

---

### Post by Jimmyfj on 2007-05-21
Before even considering a dist-upgrade via apt-get I'd check the speed of both my computer and my Internet-connection. A dist-upgrade downloads a little over 600 MB before upgrading your system. So I'd  say that the best way for you is to get the ISO-file for 7.04 Feisty Fawn, make a live-cd and then make a clean install.

I upgraded my daughters old PII 266 with 192 MB of RAM and it took a little over six hours to complete even though I have a 4 MBit Internet-connection at my disposal.

---

### Post by andrew.46 on 2007-05-21
Hi deneb,

 Read your post with some interest:

> **_deneb_ said:**
> Thx everybody.. I'll check if it is better to upgrade via terminal or downloading the new one I'll let you know
_deneb_

 There is absolutely nothing wrong with using Dapper, which will be supported until 2009. IMHO it offers a degree of stability that will not be seen with Feisty (not simply because of its LTS label). I have in fact just 'downgraded' to Dapper from Feisty and I am much happier with my system now.

               Andrew

---

### Post by _deneb_ on 2007-05-21
well.. Now I'am on FESTY

and I'm having some troubles I didn't have with Dapper :(
I posted those troubles elsewhere in the forums

1)Session SUSPEND gives eternal sleep to my laptop. Have to remove the cell and then boot to be able to work again
2)Microsoft USB mouse oftenly stop to works.. (x_X)

byez
_deneb_

---

