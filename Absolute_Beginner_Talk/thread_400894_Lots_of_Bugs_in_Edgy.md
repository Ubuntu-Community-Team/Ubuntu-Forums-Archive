---
title: "Lots of Bugs in Edgy"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by campidg on 2007-04-04
I recently updated from Dapper to Edgy recently and it ran well.  

I then bought a new computer and installed Edgy from a disk I downloaded on my old system.  Since then I have had numerous crashes in, for example, firefox, the terminal (when right clicking), and in other miscellaneous situations.  

The installer also seems to be broken.  It will apparently install a program successfully but the program won't run and when I go looking for it is found to be completely absent from the system. 

My old system had a 8.5MHz processor.  Could it be that the distribution I downloaded was too slow for my new computer with a 3.2G Pentium 4 processor?

Cheers,

Cam

---

### Post by ndefontenay on 2007-04-04
You are describing a very strange behavior here...

Have you try to update your distribution?

It's apt-get something

do

```
man apt-get
``` for more info

---

### Post by WalmartSniperLX on 2007-04-04
For a Distro Upgrade (6.06 - 6.10, 6.10 - 7.04, etc)

```

sudo apt-get update
sudo apt-get dist-upgrade

```

Or a general upgrade-all-installed package option w/o a dist upgrade:
```

sudo apt-get update
sudo apt-get upgrade

```
I dont think the dist is too slow. That sounds more like missing links and possibly Xserver problems. Could also be unstable program packages that can be fixed by a package upgrade (2nd command) I could be wrong. Im not saying im right :)

---

### Post by campidg on 2007-04-04
Thanks for the reply.

I tried apt-get dist-upgrade and nothing happened.  

All I can think of as the cause of my problems is that I have downloaded an i386 version of edgy which was the speed of my old system and I am now running it on a 64bit system, but as far as I know my new processor is not 64bit.  I think I have to re-download and start again.

Cheers,

Cam

---

### Post by WalmartSniperLX on 2007-04-04
> **campidg said:**
> Thanks for the reply.

I tried apt-get dist-upgrade and nothing happened.  

All I can think of as the cause of my problems is that I have downloaded an i386 version of edgy which was the speed of my old system and I am now running it on a 64bit system, but as far as I know my new processor is not 64bit.  I think I have to re-download and start again.

Cheers,

Cam

If you are running Edgy now, then dist-upgrade will only work from Dapper -> Edgy since doing it in Edgy will try and do Edgy -> Feisty which wont happen until 4/2007. You can try that. Im not exactly sure what you mean. Whats your hardware? :)

EDIT - Sorry OK you have a P4 right? Didn't see that. The i386 install of edgy should work just perfectly. What about your RAM, GPU, etc? Could be GPU/Drivers. You use ATI?

---

### Post by ndefontenay on 2007-04-04
x64 processors are backward compatible.

I've installed Kubuntu x32 on my amd64 architecture and it worked fine.

I still prefer using Kubuntu x64 for my amd64 ^^

Your problem might be from graphic card side?

---

### Post by campidg on 2007-04-06
Thanks for the replies,

Your are both right.  I had tried to recycle a very old graphics card in my new machine.  I have pulled it out and everything thing seems to be fine now.  

Thanks for the suggestion,

Cam

---

