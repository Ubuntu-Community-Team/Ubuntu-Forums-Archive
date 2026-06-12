---
title: "New and learnig"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by CaliBeachBum on 2008-03-27
My earlier post was moved to "Recurring Discussions". I'm a forum virgin so apologies. Some people seemed irritated at me for venting. Again apologies frustration does that. I had some success with the GRUB file and thats a good thing. Bouncing back and forth from XP which accesses the net and Ubuntu which doesn't. I see the D-Link router but net tools and the features in Ubuntu for Internet access, manual setup have not resulted in success. I will keep going for a while its interesting. But not as user friendly as I was hopping for. Internet access will give me Ubuntu wings but until then I struggle. If I'm in the wrong place again sorry tried posting were the first post was moved to and couldn't. Peace

---

### Post by saj0577 on 2008-03-27
Could you please clearly outline the problem. Your setup?Whats not working?What you have tried?Has it ever worked?

Saj

---

### Post by ByteJuggler on 2008-03-27
There's a known issue with some consumer grade routers which do not cope well with some types IPv6 DNS queries which manifests as an apparent lack of internet connectivity on fresh 7.10 (Gutsy) installs. Can I thus ask you to boot up and perform the following commands  to help me determine whether or not you actually have any network connectivity and/or whether it's possibly the issue I've mentioned:

Open a terminal (Applications->Accessories->Terminal). Then copy and paste the following command into the terminal:

```

ping -c 3 64.233.183.147

```

Please copy the output and post it back here.

Then run the following command:

```

ping -c 3 [www.google.com](www.google.com)

```

Again please copy the output and post it back here.

Also, please explain exactly what problem you're having, and what version of Ubuntu you've installed.

---

### Post by CaliBeachBum on 2008-03-28
I tried ping get back host unreachable. In live CD and installed ubuntu. Says 3 packets transfered  0 received  +3 error  100% packet loss  time 2009ms  pipe 3. I'm thinking of uninstalling ubuntu and doing the install again encase there is something i missed in the beginning. I notice the sound doesn't work either. Only question is do I use the windows CD to repair MBR then just wipe second hard drive clean? Want to be safe about this XP on primary drive Ubuntu on slave.

---

### Post by ugm6hr on 2008-03-28
Can I offer some advice:

[http://ubuntucat.wordpress.com/2007/08/06/getting-the-best-help-on-linux-forums/](http://ubuntucat.wordpress.com/2007/08/06/getting-the-best-help-on-linux-forums/)

In general...

If you want help fixing something, give details and ask for help.

Ask 1 question per thread.

If you want to complain or moan, find somewhere else to do it.

Having said that, I'd suggest you start again.

If you want help getting online, you'll have to tell us how you connect to the router - wired or wireless?

If you want help removing Ubuntu, just ask that.

---

### Post by ByteJuggler on 2008-03-28
> **CaliBeachBum said:**
> I tried ping get back host unreachable. In live CD and installed ubuntu. Says 3 packets transfered  0 received  +3 error  100% packet loss  time 2009ms  pipe 3. I'm thinking of uninstalling ubuntu and doing the install again encase there is something i missed in the beginning. I notice the sound doesn't work either. Only question is do I use the windows CD to repair MBR then just wipe second hard drive clean? Want to be safe about this XP on primary drive Ubuntu on slave.

If you're having connectivity issues even when booted from the LiveCD, then it's likely that there's other problems keeping you from getting online with Ubuntu (other than installation issues), so a reinstallation is unlikely to fix them.  

You've still not explained exactly what hardware setup you've got, we need to understand exactly how your computer is set up/connected to your internet provider, what router etc. you're using etc. etc. in order to try and help you.  

(I'm actually tempted to suggest you try the Ubuntu 8.04 [Hardy] beta, to see if that works better for you...however it is still beta...)

---

### Post by sneeks on 2008-03-28
when you installed your gutsy,were you hard wired or just disc and wireless ?

---

### Post by CaliBeachBum on 2008-03-28
I have a D-Link router DI-624. Ubuntu shows a Realtek RTL8139 card. I'm wired to the router which is wired to the D-Link DCM-202 cable modem. My daughter is wireless from her room and my son laptops in wireless. I boot into windows to research then boot to ubuntu to experiment. Ubuntu shows D-Link System Inc RTL8139 Ethernet in the upper right connectivity area. In windows I retrieved all the network settings. In ubuntu Ive worked in net tools and manual settings. I'm going back to ubuntu when i finish this post and try to document things more. Its hard bouncing back and forth and trying to remember it all. ByteJuggler thanks for the  Patience I may have better success with the new release in a month. Its no big deal. {ugm6hr} please don't read post by me or offer help and have a nice day. OK back to ubuntu but first since I'm on the net I'm going to fire up HALO and shoot a few mates. Peace

---

