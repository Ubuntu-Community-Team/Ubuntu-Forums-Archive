---
title: "How to Spped up Internet"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by gigaferz on 2006-11-20
[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)


Well, I just did this and It really Works!!!

Man!!!

Just helping new linux users like me!!!!!!

---

### Post by wildsrv on 2006-11-20
thanks

---

### Post by STREETURCHINE on 2006-11-20
yes it really does work.

 thanks :D

---

### Post by RobNyc on 2006-11-20
Thanks I dsiable IPV6 on my osx86 too :)

---

### Post by 56phil on 2006-11-20
Thanks for the info. I made the changes and rebooted. Nothing is broke - as far as I can tell. But any speed increase is indeterminable. What kind of connection are you using? I'm using a cable modem and a router.

---

### Post by STREETURCHINE on 2006-11-20
i am using a twoway vsat connection at 512/2000 kbs .i dont think it was 4 times the speed i got but it is compareable with my firefox in windows now'
 i found firefox seemed to lag a bit in ubuntu.:D

---

### Post by Cardmaster91 on 2006-11-20
will this work with edgy to?

---

### Post by 56phil on 2006-11-20
Yes, it works in edgy too.

---

### Post by Cardmaster91 on 2006-11-20
cool

---

### Post by Fittersman on 2006-11-20
my file is full of stuff like lots of stuff... so i comment all of it? and just add those four lines in?

---

### Post by Cardmaster91 on 2006-11-20
how do you get permission to edit the file? it says

You do not have the permissions necessary to save the file. Please, check that you typed the location correctly and try again.

---

### Post by nonpareilpearl on 2006-11-20
I tried it with no noticeable difference, which is unfortunate because for some reason the internets is really slow in Linux.

---

### Post by 56phil on 2006-11-20
:o NO!:o  Just comment out that one line and add the other four.

---

### Post by BLTicklemonster on 2006-11-20
Does this increase my speed on the internet, or just increase my speed when using firefox? 

Is there something I can do to increase my speed in the internet in games?

---

### Post by gigaferz on 2006-11-21
Well Im not a PC gamer, but I will tell you about the speed of the place I have Ubutnu 6.06lts.

Im using it at my workplace. All the windows computers have to be @ 10mbps Full duplex, so I edited a file so my settings are permanent in ubuntu.  

Last time I checked the speed at my work place is like 3xx kbs. It is a very slow connection, Its a bussines conneciton... and maybe because the router is very old.

---

### Post by snapcase16 on 2006-11-21
Thanks for this information! I've noticed a rather considerable improvement in speed since editing the file. For the first time in Ubuntu, Firefox is working as quickly as it did for me in Windows.

---

### Post by CupofDice on 2006-11-21
I am wondering if this has the same effect as setting to true "network.dns.disableIPv6" from the firefox howto.
[http://ubuntuforums.org/showthread.php?t=179540&highlight=Howto+speed+up+firefox]("http://ubuntuforums.org/showthread.php?t=179540&highlight=Howto+speed+up+firefox")

---

### Post by gigaferz on 2006-11-21
Well , Im not a pro on networking, but there are many things to consider when trying to improve the speed on a machine.

The browser settings,
The device settings,
Number of requests and/or connections...
The media speed....and many more I dont know about

So, I guess any tweak you do to your system will boost the Internet.

---

### Post by gigaferz on 2006-11-29
Im just replying to this to keep this post alive!!!

---

### Post by bappi on 2006-12-11
hi, i am new to linux, and my cable modem connection is really slow compare to what it is when i run xp and i tried to disable the ipv6 but everytime i wanna save it says that i do not have the permission. can someone help me on this plz

---

### Post by vgrisham on 2006-12-11
> **bappi said:**
> hi, i am new to linux, and my cable modem connection is really slow compare to what it is when i run xp and i tried to disable the ipv6 but everytime i wanna save it says that i do not have the permission. can someone help me on this plz

I'm new to ubuntu as well, but I believe you just preface those commands with the word sudo. Please correct me if I'm wrong.

---

### Post by Westies on 2006-12-11
open the file from the terminal using "sudo nano aliases" when inside the proper directory.

---

### Post by g3k0 on 2006-12-11
Hmm at first it seemed faster... but then I realized it was just the placebo effect..

---

### Post by dolphinsonar on 2006-12-11
I can fly!

---

### Post by darco on 2006-12-12
I have been using Fedora Core for awhile and disabling IPV6 was one of the first things you did. Since I have been out of the game for awhile I wasnt sure if anything had changed because I noticed IPV6 enabled in Ubuntu so I just assumed it was ok. I just disabled it and I do see a speed difference.

dr

---

### Post by marx2k on 2006-12-12
This is what /etc/modprobe.d/aliases looks like at the moment as far as ipv6:

alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off


However, ifconfig still has an ipv6 address on my ethernet card:
```

ath0      Link encap:Ethernet  HWaddr 00:11:50:D4:FD:E8  
          inet addr:192.168.11.8  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:fed4:fde8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:88667 errors:0 dropped:0 overruns:0 frame:0
          TX packets:133207 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10436266 (9.9 MiB)  TX bytes:184709275 (176.1 MiB)

```

So does that mean it's off or not? Because there has been no speed increase over the lan at all.

---

### Post by gigaferz on 2006-12-12
hi everybody!

---

### Post by adamJ5 on 2006-12-14
Um..hi gigaferz...


Anyways, this helped me a bit, going from 3-4kb/s to 60kb/s, but it still isn't on the same level as it used to be (400kb/s and up). When I use uTorrent the lamp never turns green. How can I fix that?

---

### Post by marx2k on 2006-12-14
What does the lamp signify? In Azureus, green lights not turning green usually means your ports are blocked (or in the worst case scenario, your net provider is blocking p2p traffic) -- make sure to check that your incoming p2p ports are opened

---

### Post by adamJ5 on 2006-12-15
Thanks for the reply Marx,

How do I check if those ports are open?

Edit: I was using BitTornado, not uTorrent as I previously posted. My bad.

---

### Post by insane_alien on 2006-12-15
ok i did this and DID get a measurable speed difference, BUT it could just be random traffic delays that lead to this. before, i got an 83kB/s average on a file, after i has 83.2kB/s average for the same file. hardly conclusive though.

---

### Post by gigaferz on 2007-02-16
bump

---

### Post by r4ik on 2007-02-16
> **gigaferz said:**
> [http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)


Well, I just did this and It really Works!!!

Man!!!

Just helping new linux users like me!!!!!!


Also try about:config in the adresbar and set the "pipe" maxrequest to 8

---

### Post by gigaferz on 2007-02-16
in firefox??

what about the konqueror?

---

### Post by r4ik on 2007-02-16
I don't use konqueror got no idea,sorry.

---

### Post by gigaferz on 2007-05-01
[http://www.cnettv.com/9710-1_53-27253.html?tag=nl.e415](http://www.cnettv.com/9710-1_53-27253.html?tag=nl.e415)

pretty simple, huh?

I did notice a difference..

---

