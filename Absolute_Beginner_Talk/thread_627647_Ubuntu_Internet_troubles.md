---
title: "Ubuntu Internet troubles"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by JumpmanRugs on 2007-11-30
Hey Guys! I was wondering if anybody could help me with my internet troubles on Ubuntu...Ok ive set up my network and im connected to it and everything but i cant get on the internet ( Just comes up with cannot find server/page when i open firefox)...And i dont know why. Is anybody able to help me please? I'm on a wireless network by the way :D Thanks Alot! Peace!

---

### Post by deep.tinker77 on 2007-11-30
What type of network adapter are you using (i.e. model and type of wireless adapter). Laptop or desktop? What version of Ubuntu are you using?

---

### Post by JumpmanRugs on 2007-11-30
Oh Yea my apolagies Lol! Its Wireless! :D

---

### Post by tinycamp on 2007-11-30
try this when connected

```

ifconfig
route -n
iwconfig
```

in the first you should see an IP address next to your wireless interface, (you'll see at least 3 if you have a wired and a wireless adapter), usually the wireless will be eth1
.
the output of the route -n  command should have a line that makes reference to the 0.0.0.0/0.0.0.0 destination, without that, you're stuck at local.... 

the third one, will give you the status of your wireless connections

please post the output of these commands!!!

good luck!

---

### Post by JumpmanRugs on 2007-11-30
Yea now heres the really newby part. My friend (IslandMassive) suggested i use Ubuntu and i liked the idea and what i saw on his comp but i dont understand how to use it completely as of yet. So could you break this down into simpler steps please?... Lol sorry to be a pain...Im getting used to it but as i onlt just started using it i dont fully understand yet. :) Thanks Alot! I appreciate the help! Peace!

---

### Post by tinycamp on 2007-11-30
its ok!, first open a text terminal, usually at Applications--> Accessories--> Terminal

then, type in the commands, one by one, when finished select all the output with the mouse, go to any text editor, or even this post interface and press both mouse buttons at the same time, this will paste all the selection on the screen.

good luck!, if you need more help, tell me please!!!!

---

### Post by JumpmanRugs on 2007-11-30
Thanks Alot! Ill get back to you with these! Thanks for your patience...such a nice community of people :D Like i said ill get back to you :) Thanks again, Muchly appreciated! Peace!

---

### Post by coldbluefusion on 2007-11-30
Hey, i am back in the world of Linux after being out of it for about 5 years so i am getting my feet wet all over again. I am trying to get my Novatel Merlin EX720 PC card to work in Ubuntu 7.10 but the directions that are on Sprint's page are no good, can some on help please... I cannot install KPPP its giving me an error "Either the application type requires special hardware features or the vendor decided not to support your computer type"
HELP

---

### Post by kamitsukai on 2007-11-30
> **coldbluefusion said:**
> Hey, i am back in the world of Linux after being out of it for about 5 years so i am getting my feet wet all over again. I am trying to get my Novatel Merlin EX720 PC card to work in Ubuntu 7.10 but the directions that are on Sprint's page are no good, can some on help please... I cannot install KPPP its giving me an error "Either the application type requires special hardware features or the vendor decided not to support your computer type"
HELP
 
You know you would get more help if you started your own thread as your problem sounds different to pete's (jumpmanrugs)

---

### Post by Drate on 2007-11-30
Also, it helps us to find the source of your problem if you can tell is exactly what wireless card you have... think of it like a car, and we need to know the make and model (Nissan Sentra, Toyota Camry).  Is your card a Linksys Wireless G with Speedbooster?  Is it a Netgear somethingorother?  Pray it's not the first (unless Gutsy has vastly improved in this area).

---

### Post by coldbluefusion on 2007-11-30
it says "Sprint Mobile Broadband Merlin EX720 by Novatel Wireless"

Thanks in advance

---

### Post by JumpmanRugs on 2007-11-30
Sorry put up wrong thing...Ill sort it out and put it back up :D

---

