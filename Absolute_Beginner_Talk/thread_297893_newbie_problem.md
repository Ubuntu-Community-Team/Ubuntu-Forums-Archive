---
title: "newbie problem"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by gustav213 on 2006-11-11
hey well, i just got xubuntu for an old laptop i had lying around and i must say first of all i love it up to now. i have tried other linux os and they were just driving me nuts never detected my internet, were always causing problems and i almost left until i found this, love it.

well to my problem i use my regular desktop with p for games and that sort of stuff but wanted to use this laptop since its a small screen and just low weight for taking notes at school, i could easily email them to me no problem, but wanted to see if i could save them to a floopy and then just put them in my computer toprint and save for later. i just cant seem to mount the floopy and move files into it, could someone give me a step by step on how to do that i wiki it but coulndt find it. 

the other thing is i was wondering if i needed antivirus wel how could i get one and also what about firewall and spyware toolds ? i am new to linux so im not sure how that works.
thanx in advance for all your help  and keep up the good work with ubuntu and xubuntu.

gud

---

### Post by digby on 2006-11-11
I'm kind of surprised that it isn't automounting floppies, but if you need to do it by hand, you just use this.```
sudo mount  -t  auto  /dev/fd0  /media/floppy
```  As for anti-virus and spyware?  You don't need them.  From a practical standpoint, they don't exist for linux.  Isn't it great?  As for a firewall, you can most likely do without one of those as well unless you plan on running a few server programs off your laptop.  I'd bet against this, so you're probably safe w/ the default config.

---

### Post by d3v1ant_0n3 on 2006-11-11
No idea about the floppy issue. A quick search for ** mount floppy** found [ THIS ](http://ubuntuforums.org/showthread.php?t=104259&highlight=mounting+floppy) thread, which hopefully will have some pertinant information. 

I didn't know people still used floppies- don't they give USB thumbdrives away free with cornflakes now? :p

Security wise, Ubuntu comes with a firewall built in (iptables), you can download a front end for it (called 'firestarter') from the repos I believe. 

ClamAV is also available by way of an antivirus, although you mainly only need it if you're sharing files between your linux box and your windows box.

Spyware wise, you don't need anything.

I run with iptables at its defaults (I assume at least, I've never touched it), no AV, and a hardware firewall.

Hope that helped a little.

---

### Post by The Creator on 2006-11-11
hello, i am unable to tell you how to mount a floppy but you probably should not need antivirus for your computer. You also should not require spyware software. As linux is not half as widely used as windows it is simply not as much of a target. Why go for 10% of computers when you can go for 80% of computers which run windows? It simply does not make sense to try and nail that 10%. When i was running windows i simply was not stupid about what i downloaded and used noscript and adblock in firefox. Now there may be a virus for linux which i am unaware of but i have not heard of any. Linux is probably more secure than mac os which only has about 4 known viruses. If you are looking for antivirus though search for clamantivirus,or i belive avg has put out a linux edition. Welcome to linux!

---

