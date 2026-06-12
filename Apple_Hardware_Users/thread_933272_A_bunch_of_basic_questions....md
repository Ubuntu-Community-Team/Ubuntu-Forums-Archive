---
title: "A bunch of basic questions..."
date: 2008-09-29
forum: Apple Hardware Users
---

### Post by skullmunky on 2008-09-29
I installed 7.04 on my macbook and it works pretty darn well, I'm pleased to say.  It did take me approx. forever because I didn't read the instructions well enough and missed the crucial step during partitioning where you set up GRUB properly, but all's well now.

Now I'd like to understand the intricacies well enough to give reliably solid instructions to students with macbooks who want to do this too.  This might be up to a few hundred or a thousand students, depending on how well I can sell the idea and how easy it is. 

- Is there an ubuntu variant specifically for Mactels?  Or if not, how hard would that be to do?  One with the various drivers for already installed, sensible defaults for Ctrl-Click and an option to map the Apple/Splat key to Alt, etc.

- I added that mactel-support PPA to try and get the ath9k drivers ( no dice, as have older kernel ).  but I see there's a lot of other great mactel stuff in there, should I install all of that?

thanks!

---

### Post by JetskiDude911 on 2008-09-29
Are you wanting to do this with Intel Macs or PPC Macs?

I can't really help you much with the PPC part, but I think there is a version of Ubuntu that will run on the PPC architecture. I don't think it's released by Ubuntu though.

As for the Intel Macs, I've found that with each version, Ubuntu seems to run better and better on them. 7.04 ran ok, 7.10 supported almost everything except for a few things. 8.04 seemed to run perfectly to me. The speed was great, and every piece of hardware worked from what I could tell.

---

### Post by snowpine on 2008-09-29
First of all, PowerPC Ubuntu is here (to answer Jetski's question): [https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

Skullmunky, I am glad Ubuntu is working for you on your computer! I personally would not be interested in a 7.04 install guide, since I believe support for that version ends next month. I would want a distro/version that receives security updates and bug fixes. So I'd suggest you base your tutorial on 8.04, since it is a long-term support version, or on something super-stable like Debian Etch. Good luck!

---

### Post by cyberdork33 on 2008-09-29
> **skullmunky said:**
> Is there an ubuntu variant specifically for Mactels?  Or if not, how hard would that be to do?  One with the various drivers for already installed, sensible defaults for Ctrl-Click and an option to map the Apple/Splat key to Alt, etc.
No. It could be done, to a point... Many of the drivers required for Macs need proprietary firmware which is incompatible with the GPL and may have legal issues if distributing. Having config file defaults set appropriately should not be all that difficult though.

> **skullmunky said:**
> I added that mactel-support PPA to try and get the ath9k drivers ( no dice, as have older kernel ).  but I see there's a lot of other great mactel stuff in there, should I install all of that?
No, most of that software is outdated. That PPA is only used when it is not relatively easy to get certain things elsewhere. Most anything in the Mactel-Support PPA is already part of Ubuntu proper.

P.S. for ath9k, checkout this thread. There are different newer ways to install now...
[http://ubuntuforums.org/showthread.php?t=874097](http://ubuntuforums.org/showthread.php?t=874097)

---

### Post by kosumi68 on 2008-09-29
I would like to second snowpine and suggest using Hardy 8.04 LTS with backports enabled, since it will give you the most stable and usable system so far. Regarding the Atheros drivers, this is hot news: [http://lkml.org/lkml/2008/9/26/321](http://lkml.org/lkml/2008/9/26/321)

---

### Post by skullmunky on 2008-09-30
Thanks!  Hardy Heron sounds like definitely the thing to use, to start with.  I'll try out Intrepid too.

These are all Intel MacBooks, mostly identical.

---

### Post by niaz2 on 2008-10-01
I have this. But i can not install this. how can i do this.
please help me.

---

