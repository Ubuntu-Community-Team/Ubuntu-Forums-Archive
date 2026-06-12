---
title: "Stuck with Setting up Dlink usb modem"
date: 2005-10-05
forum: Absolute Beginner Talk
---

### Post by happychap on 2005-10-05
I am in the process of setting up my Dlink 200 Rev B1 modem, but am stuck.

I have printed out the instructions at [http://users.tpg.com.au/johnd/dsl200.html](http://users.tpg.com.au/johnd/dsl200.html) as well as the thread [http://www.ubuntuforums.org/showthread.php?t=68695](http://www.ubuntuforums.org/showthread.php?t=68695) where Dradul has given a good rundown.

I am using Breezy, no DHCP installed, am a single user, no network. My box has an ASUS board, AMD Athlon 2100 chip, and I installed the i386 version. I use ADSL.

Everything has gone OK up to and including running the command:
```

sudo eciadsl-start

```

I got this response:
```

 [EciAdsl 1/5] Setting up USB support...

Preliminary USB device filesystem is OK
Loading tun/tap module...
tun loaded successfully

[EciAdsl 2/5] Uploading firmware...

Process skipped .. no more needed
firmware loaded successfully

[EciAdsl 3/5] Synchronization...

OK eciadsl-synch: success
Synchronization successful

[EciAdsl 4/5] Connecting to provider...

Connection successful

[EciAdsl 5/5] Setting up route table...

Waiting for tap0...
ERROR: couldn't set your static IP or your external gateway
If you don't use PPPoE, please check your configuration.

```

It is lying. I am not connected, even though both lights are lit on the modem. Firefox will not connect to my home page. Nor will the mail program run, etc.

I issued the command:
```

$ sudo ifconfig

``` 
and got this response:
```

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10448 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10448 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:947561 (925.3 KiB)  TX bytes:947561 (925.3 KiB)

```

No tap0.
I don't know how to proceed. Can some kind and patient person give me some explicit instructions on how to go on from here, please?

Thanks

---

### Post by mlomker on 2005-10-05
I haven't set one of these up before but I did read through the docs.  It sounds like you need the driver in addition to a pppoe configuration to actually get an IP address.  The ubuntuforum post doesn't discuss that, but I found this [wiki page.]("https://wiki.ubuntu.com/ADSLPPPoE")

---

### Post by happychap on 2005-10-05
Thanks, Mlomker. That page talks about having an ethernet network card. I don't have one. My connection is through usb. 

I have already downloaded and setup the dirver for it from eciadsl, and synched the modem.

I know this type of connection is regarded as a mongrel, but from scouring the posts here, and also the outside post to which I referred, it can be/has been done succcessfully. I just cannot find any posting which addresses this particular hiccup that I have met, and being a Linux 'illiterate' I don't know how to overcome it.

---

### Post by mlomker on 2005-10-05
[QUOTE=happychap]Thanks, Mlomker. That page talks about having an ethernet network card. I don't have one. My connection is through usb. [/QUOTE]

I know, but the [link that you provided]("http://users.tpg.com.au/johnd/dsl200.html#configuring-rp-ppoe") mentioned having to use a pppoe client in addition to the driver.  The TUN interface is just a virtual ethernet interface...

---

### Post by happychap on 2005-10-05
Thanks, Mlomker.

I didn't mention above that I had downloaded rp-pppoe and (hopefully) set it up correctly. Then when I hit the 'start' button, it timed out. So I thought the problem lay in not getting tap0 in ifconfig. Maybe I haven't set up rp-pppoe correctly.

Now I have printed out the page you referred to, I will follow that, and see how I go. Will let you know how it pans out.

Thanks again.

---

### Post by happychap on 2005-10-06
Here's my latest update. I've spent all day installing, uninstalling, trying pppoeconf, pulling that little plug out of the back of the modem and then putting it back in, etc., but all to no avail. I have not been able to progress one iota. I cannot get tap0 to appear when I run ifconfig. It has to be hiding in there somewhere - I put tap0 in as the interface when configuring rp-pppoe - but the little so-and-so just doesn't want to show its face.

Help.

---

### Post by happychap on 2005-10-17
Yay!!!!

I'm typing this through Ubuntu. Success at last.

For anyone who's interested - I had to wait for the release of Breezy and do a full re-install. Having done that, I followed the procedures for setting up my D-Link DSL-200 Rev B1, and here we are!!

Great. Now to learn about Linux and ubuntu in depth - apart from doing the other things one does on the internet. :D

---

### Post by mlomker on 2005-10-17
> Great. Now to learn about Linux and ubuntu in depth - apart from doing the other things one does on the internet.

Congrats!  Happy surfing.

---

