---
title: "wireless problem"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by Tom Whitbread on 2007-12-05
hi i have an acer aspire 3003wlmi and in my old house was connected to a netgear router through my laptops inbuilt receiver. . have just moved and am trying to get connected to a broadcom router but when i do a repair it won't generate a new ip and gives little info why. have tried dissabling wireless zero and enabling broadcom lan and vice versa and still not working. the receiver is picking up the router giving excellent strength etc and accepts the password, just not generating a new ip.. any ideas. i know very little about this sort of thing so speak slowly please!
ta

---

### Post by Papa-san on 2007-12-05
No clue as to whether or not it will help, but the "Wireless Help" link in my signature helped me a lot!

---

### Post by pmacd79 on 2007-12-05
Hi this is an ubuntu forum, but I will help you anyway, just because I'm such a nice guy!.
When you go to services.msc, keep the broadcom utility disabled, and use the wireless zero config, you will have more luck that way, trust me. I am A+ certified and used to work for an ISP. Using wireless zero instead, windows manages the connection. I am assuming it is XP. Windows actually does a great job managing wireless. Just make sure that you ethernet connection is disabled in network connection in the control panel or just go to device manager and diable it. It actually sounds like it is working until you put in the encyption password, that sounds like the issue. Just a wrong password. Also if you are running a security suite, especially something like zonealarm, it can see the new network as a security threat and block it. one other thing you could try is to l set a static IP. Check error logs as well. Control Panel > Admin tools > Event Viewer. Check the system errors. Hope this was some help. You can email me if you still can't get it working. [email]paul.m.79@gmail.com[/email]. Some people will get mad if you try to troubleshoot windows here. 
Break a Leg!:lolflag:


PS - try this link [http://support.microsoft.com/kb/870702]("http://support.microsoft.com/kb/870702")

---

### Post by Tom Whitbread on 2007-12-05
that looks a pretty step by step approach! will give it a go tonight and let you know how i get on!
cheers

---

### Post by Tom Whitbread on 2007-12-05
> **pmacd79 said:**
> Hi this is an ubuntu forum, but I will help you anyway, just because I'm such a nice guy!.
When you go to services.msc, keep the broadcom utility disabled, and use the wireless zero config, you will have more luck that way, trust me. I am A+ certified and used to work for an ISP. Using wireless zero instead, windows manages the connection. I am assuming it is XP. Windows actually does a great job managing wireless. Just make sure that you ethernet connection is disabled in network connection in the control panel or just go to device manager and diable it. It actually sounds like it is working until you put in the encyption password, that sounds like the issue. Just a wrong password. Also if you are running a security suite, especially something like zonealarm, it can see the new network as a security threat and block it. one other thing you could try is to l set a static IP. Check error logs as well. Control Panel > Admin tools > Event Viewer. Check the system errors. Hope this was some help. You can email me if you still can't get it working. [email]paul.m.79@gmail.com[/email]. Some people will get mad if you try to troubleshoot windows here. 
Break a Leg!:lolflag:


PS - try this link [http://support.microsoft.com/kb/870702]("http://support.microsoft.com/kb/870702")

oopss social pariah! wondered what ubuntu was! just came accross your site on a google search for wireless probs.. will check out your ideas thanks, may just be a WEP thing. yep running xp will dissable bdcm again and give it another go.
cheers

---

### Post by pmacd79 on 2007-12-05
Good Luck.

---

