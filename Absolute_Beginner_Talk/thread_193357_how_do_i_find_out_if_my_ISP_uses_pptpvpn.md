---
title: "how do i find out if my ISP uses pptp/vpn?"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by boon on 2006-06-09
Since my city ISP gave me a new dialup number I am not able to get a proper connection, with error messages like "cannot determine ethernet address for proxy arp". 

Possibly the ISP is using pptp/vpn? I could ask but the office is closed till tues and I want connection today.

Or can I just go ahead and experiment with pptp software without damaging my system.

---

### Post by daller on 2006-06-17
Have you contacted your ISP? (Since the thread is a week old!)

Any resolution?

---

### Post by boon on 2006-06-18
Well I found out that my ISP does use pptp/vpn as an option if needed, but not on the default dialin, so that doesnt seem to be the problem.

I can dial in, get a connection, PAP authentication, remote and local IP addresses, then it immediately fails. 

If there is something wrong with my configuration, I dont know what it is or why the problem suddenly appeared.

---

### Post by boon on 2006-06-18
ok I've got the ppp connection successfully working again. It didnt have anything to do with pptp/vpn. Sorry about the red herring.

After searching through some threads and trying a few things, I brought up the pppconfig utility and entered the new new dialin no and password. Command pon and Voila! it works.  O:) 

I had already entered these details manually in some configuration files so I dont know exactly why it didnt/does work.

It looks like I have at least 3 ppp configuration utilities on the system, pppconfig, wvdial, and gnome 'network settings'. I've touched on all of these and edited various text files, but if it is now working I won't complain. pppconfig and pon is go. :mrgreen:

---

### Post by daller on 2006-06-19
Nice!!!

Great that it works for you!

Have a nice day!

---

