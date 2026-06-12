---
title: "Just installed Ubuntu 6.10"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by Termajin on 2006-11-14
I just installed Ubuntu 6.10 on my Dell Inspiron 5100. The install went fine(from what I can tell). I can open all the software and use it without any problems. But, when I go to the device manager its not detecting any of the hardware. Its all unknown. What do I need to do to change this? I need it to see my wireless card so I can connect to the net. Any suggestions?

---

### Post by steve.horsley on 2006-11-14
Wireless cards are a bit of a minefield because so few makers release Linux drivers or the information needed for Linux developers to write the drivers. Search this forum for threads on wireless, and include the make of your card/chipset too. You will likeky find many threads on the subject. Some cards can be driven natively, others have to use the winsows driver under ndiswrapper, others are just paperweights.

---

### Post by JReagan1990 on 2006-11-14
Are you asking about the device manager, or the networking option in the system menu?

---

### Post by jhenager on 2006-11-14
> **steve.horsley said:**
> Wireless cards are a bit of a minefield because so few makers release Linux drivers or the information needed for Linux developers to write the drivers. Search this forum for threads on wireless, and include the make of your card/chipset too. You will likeky find many threads on the subject. Some cards can be driven natively, others have to use the winsows driver under ndiswrapper, others are just paperweights.

I had a no-name wireless PCI card that only needed to be activated to work fine. It seems that wireless either works great or it is a real pain - not much in the middle.
If worse comes to worse, you can always try Linuxant - [http://www.linuxant.com/driverloader/](http://www.linuxant.com/driverloader/). I had to use it under SuSE 9.0 for my wireless. A license is only twenty bucks. You can try it out for free to make sure it is worth the money.

---

### Post by marx2k on 2006-11-14
My device manager also sees a huge list of everything 'Unknown' on my Compaq Evo N610C

The second half of the list gets somewhat more specific.  Especially if you run through the tabs.

But yeah, I wonder why Device Manager has the first half of the list populated with everything 'Unknown'

Everything works great though, so it doesn't seem to be a big deal.

---

### Post by Termajin on 2006-11-14
hmmm, well I hate to say this but what if I don't know exaclty what model and chipset I have? Its a dell laptop. How many different cards could they have used?

---

### Post by Termajin on 2006-11-15
Ok, so I went into the router and I notice the laptop is connected. Its still not working tho. I'll open firefox in ubuntu and all I get is server not found. 

What am I doing wrong?

---

### Post by gjtoth on 2006-11-15
Have you tried putting in the DNS IPs?  That worked for me.

---

### Post by Termajin on 2006-11-15
Yes.

---

### Post by Termajin on 2006-11-15
I noticed something..

Network Connection: lo

Is this what it should be set at?

I'm just now learning about linux. So I have no clue.

---

