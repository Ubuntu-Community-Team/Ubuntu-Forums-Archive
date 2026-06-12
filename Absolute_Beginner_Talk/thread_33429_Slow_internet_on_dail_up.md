---
title: "Slow internet on dail up"
date: 2005-05-10
forum: Absolute Beginner Talk
---

### Post by rromie on 2005-05-10
Hi, I just got an external modem last week (my previous modem is a winmodem) and manage to surf the net on ubuntu 4. However the speed is much slower compared to surfing using Windows XP. Based on test at testmy.net, windows speed is 20 to 24 Kbps but Ubuntu only 7 Kbps. I've tried ifconfig comand and the result is this:

Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5579 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5579 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:406647 (397.1 KiB)  TX bytes:406647 (397.1 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:219.92.92.106  P-t-P:219.93.164.54  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:17675 (17.2 KiB)  TX bytes:2149 (2.0 KiB)

Any ideas?

Thanks.

---

### Post by defkewl on 2005-05-10
Are you sure that Ubuntu cause this? Because I use Linux for internet connection and it is much faster than when I use windows. Try turning off unused services such as isdn, etc. :)

---

### Post by Stormy Eyes on 2005-05-11
[QUOTE=rromie]Based on test at testmy.net, windows speed is 20 to 24 Kbps but Ubuntu only 7 Kbps. I've tried ifconfig comand and the result is this:[/QUOTE]

You're talking about dialup, right? When I used dialup, I considered myself lucky to get between 5 and 6.5 Kbps, and normally got 4.5 to 4.9 Kbps. I tend to be skeptical of benchmarks; you should be too. You're using *dialup*. Slow internet is to be expected.

---

### Post by XDevHald on 2005-05-11
[QUOTE=Stormy Eyes]You're talking about dialup, right? When I used dialup, I considered myself lucky to get between 5 and 6.5 Kbps, and normally got 4.5 to 4.9 Kbps. I tend to be skeptical of benchmarks; you should be too. You're using *dialup*. Slow internet is to be expected.[/QUOTE]
 I understand you're trying to help, but we're needing to keep this at a pause of tech support until the mods have come to a final decision of what will happen based on results of use for this forum.

[http://www.ubuntuforums.org/showthread.php?t=33441](http://www.ubuntuforums.org/showthread.php?t=33441)

---

### Post by rromie on 2005-05-11
[QUOTE=defkewl] Try turning off unused services such as isdn, etc. :)[/QUOTE]

Can you recommend some more unused service?

And errr... how to turn them off?

---

### Post by Jace on 2005-05-11
AS a newbie to this and really needing help. So far this is where I am coming to. So please let it be a newbie tech support forum.. Thanks

---

### Post by Nexxus6 on 2005-05-12
$ sudo gedit /etc/ppp/peers/ppp0
and add the following line at the end:

115200

(only the number, nothing else)

Check here
[https://bugzilla.ubuntu.com/show_bug.cgi?id=8890](https://bugzilla.ubuntu.com/show_bug.cgi?id=8890)

---

### Post by rromie on 2005-05-16
[QUOTE=Nexxus6]$ sudo gedit /etc/ppp/peers/ppp0
and add the following line at the end:

115200

(only the number, nothing else)
[/QUOTE]

Yup, that works, now the speed has improve simmilar to under Windows XP! Thanks :)

---

### Post by zippy_nz on 2006-06-28
Hi there.

Check out this product, OnSpeed. its an internet accelerator which is compatible for both Mac and PC. It sits quietly on your pc/laptop in the background, and flexible enough for you to turn it on or off. Trials have showed that it increases dial-up speed to up to 10 times, some times, even more. Go and have a look - [http://www.onspeedasia.com](http://www.onspeedasia.com)

---

