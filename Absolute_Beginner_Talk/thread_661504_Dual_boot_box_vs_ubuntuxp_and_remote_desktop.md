---
title: "Dual boot box vs ubuntu/xp and remote desktop"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by juanzo007 on 2008-01-08
Hey Folks...

I have one ubuntu box on an old p4 system, and a newer xp box.  Only one monitor.  I'm preferring at this point to use my ubuntu system to keep learning, plus it is a hell of a lot faster than my more powerful xp box for web applications, but also need to use IE at times and other Office apps.

What is the best way to have access to both?  Dual-boot one of the systems?  Keep them seperate and use remote desktop?  I've used vnc before on these two systems when they both had win xp and found it to be pretty slow.

Any advice is appreciated.  It seems you're only limited by imagination with this stuff, huh?

---

### Post by HereInOz on 2008-01-08
I would tend to load Ubuntu on the better box of the two, then install VMWare server on that system, which would give you the ability to create several virtual machines (XP, Win2000, Win98, 3.11 - I could get carried away here!!) and run them as an application on Ubuntu.

I have Ubuntu running on a fairly old AMD Athlon XP 2800 system, with VMWare server running virtual machines of Win2K, XP and, would you believe, Vista!  The Vista performance, by the way, is absolutley atrocious, but the other two run quite nicely.

This is a good way to get around the need to have occasional access to Windows software, but do the majority of your work in Ubuntu.  I find that trying to run more than one virtual machine at a time is not really practical - not enough system grunt - but for your work, it would do fine.

You could also use VirtualBox, if you wished.  Similar deal.

---

### Post by bodhi.zazen on 2008-01-08
You can try to run your windows apps on wine.

[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

You can also try virtualization :

[https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)

---

### Post by moebob24 on 2008-01-08
There is no software needed here...just hardware. Go out (or online) and get a KVM switch. You can control 2 boxes from 1 keyboard mouse and screen (K.eyboard V.ideo M.ouse) you can get really expensive ones or basic ones. I personally like the basic ones but whatever floats your boat. You can get KVM switched that control 4 computer too.

---

### Post by juanzo007 on 2008-01-08
Wow, good stuff guys, exactly the kind of varied input i'm lookng for!  much appreciated!

---

