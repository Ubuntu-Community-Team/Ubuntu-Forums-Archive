---
title: "??help?? pci:cannot allocate resource region 2 0f device"
date: 2007-05-20
forum: Apple PPC Users
---

### Post by mattyinthevalley on 2007-05-20
I am lost to where I can figure this out. So here I am again with this post.

When I start upp my g4 12inch powerbook. It goes through the whole booting process, it begins to go into the username screen, atleast the color of it comes up, then this message comes up with a black screen "??help?? pci:cannot allocate resource region 2 0f device"t
Then it just sits there,

I have downloaded the alternate cd I tried to load it in, I hit the c key, it goes into booting, then when the language part comes up, it skips through it so fast i cannot read it, and goes straigt into the blackscreen that says the above cannot allocate.....................

any ideas matty, 
any questions?

tanks alot, 
matty

---

### Post by kidders on 2007-05-21
Hi there,

I get a similar message on mine immediately after my bootloader hands things over to the OS. Whatever is wrong doesn't seem to have any particular impact, but I've often wondered what the cause of the message is.

Anyhow, now that your thread is back on top of the recent post lists (hehe), perhaps we'll attract the attention of someone who can answer your question. :-P

---

### Post by Xenner on 2007-05-22
i get the same message on my ibook g4, but i also get a similar one on my AMD X2 desktop, so who knows..

---

### Post by Twiggy003 on 2007-07-19
Just thought i'd say also, i get this message, it has no noticeable affect on anything, but I do wonder why it says it.

---

### Post by reh4c on 2007-07-19
I get the message on my iBook G4 as well.  If I remember correctly, I filed a bug report in Malone or at least added a comment to an existing one.

---

### Post by gvigorus on 2007-07-29
Same trouble on Xubuntu Feisty Fawn Powerbook G3 Lombard. And my pci wireless card isn't recognized...

---

### Post by reh4c on 2007-07-30
Issue still exists on Ubuntu Gutsy 7.10 Alpha 3.

---

### Post by damn66 on 2007-07-30
> **Twiggy003 said:**
> Just thought i'd say also, i get this message, it has no noticeable affect on anything, but I do wonder why it says it.
yup..same here but no noticeable affect as well :confused:

---

### Post by johng4 on 2007-07-30
I get it as well.  I've always assumed it had something to do with onboard video on my iBook G4.

---

### Post by gvigorus on 2007-07-31
I was just looking around online for some solutions and came across something interesting. I read that "Bios fails to tell Linux to reserve RAM for card bus controller. "PCI failed to allocate resource..." in dmesg tells the memory address in question. One should start kernel with parameter reserve=_____,_____ where first spot is for start address and second is for lenght"

I don't know what to make of it as of right now. Still looking for some answers.
Here's the link to the post where i got the above info from:
[http://www.linuxquestions.org/questions/showthread.php?s=&forumid=41&threadid=166982#4](http://www.linuxquestions.org/questions/showthread.php?s=&forumid=41&threadid=166982#4)

Hope some can be sorted out:)
Serge

---

### Post by stmiller on 2007-08-01
I'd say don't worry about this if you video comes on and it boots up okay. 

You can do 

$ less /var/log/messages 

to review kernel boot up messages if you are concerned.

---

### Post by benkong2 on 2007-09-23
Just a question. Would this make the synaptics driver not work on my G4 ubnutu feisty install? I get the errors for 0001:10:18.0 and 19.0 both seem to be Apple Keylargo UHCI devices.

---

