---
title: "Dapper live CD failure on iBook G3 700"
date: 2006-07-19
forum: Apple PPC Users
---

### Post by anothernewbie on 2006-07-19
Hi

After having given up with Breezy on my iBook G3 700 (install was easy indeed but then fumbling around with the system to get it to work properly was a quite dissatisfying experience) I now tried out the Dapper live CD. And, unfortunately I encountered the same main issues as with Breezy:

- no wake-up after sleep, instead total freeze (ok, the sleep option now is turned off by default, instead out-of-the-box it is set to blank screen only, but this does not solve the issue, it just hides it)
- int'l English keyboard not recognised and I did not find any in the properties dialogue which fits (my iBook has the ` and ~ key on the lower left of the keyboard and a paragraph and plusminus key on the upper left)
- internal modem not recognised (ok, not really expected to work out-of-the-box but would be nice if it did)

OTOH I saw a range of positive posts on this topic, so I believe that there must be some hope at least.

Question: Does the live CD not properly work with the iBook G3 700 so that I would have to do a full install of Dapper to get it work out-of-the-box (and after successful install possibly again give up frustrated as with Breezy, with a lot of time wasted), or is there for Dapper still the need to apply the range of well-known workarounds for the range of well-known issues as with Breezy (i.e. time consuming try&error based on postings), or am I just doing something wrong?

Is this an indication that nobody anymore cares for PPC architectures, in particular to resolve the above issues? (unfortunately I am not in the position to contribute bringing this forward so of course I must not complain; pls nobody misunderstand me)

I saw that another posting claims the opposite (generally speaking), but...

Is there anybody who can tell me from his/her own experience the effort to get Dapper to fully work on an iBook G3 700?

Many thanks in advance!

---

### Post by Skia_42 on 2006-07-19
I have tried to run a live cd on both my imac G3 and my eMac G4. I was not successfull on either computer. I decided to take a chance and I just installed Ubuntu. (I'm a former Mac user) I don't regret that decision one bit. Ubuntu is great. If you want to try out Ubuntu then either install it on an old computer you don't care about or backup up everything on your iBook and set Ubuntu up as a seperate partition. (dual boot)

---

### Post by anothernewbie on 2006-07-21
No doubts that Ubuntu or, more general, Linux is great. I am using Linux for many years on my ix86 PC, no other OS.

Referring to the issues mentioned: Do these occur on your Macs?

Anybody has experience with an iBook G3 700?

Anybody has answers to my original posting?

Thanks

---

### Post by avtolle on 2006-07-21
I have no experience with an iBook G3 700. However, what I have gleaned from reading various threads on this Forum is that the kernel on the Live CD is apparently different from that which is installed; and, in some cases, the mere installation to HDD cleared up issues the poster was having/did have with the Live CD.

---

### Post by Skia_42 on 2006-07-21
How big is your harddrive? Do you have enough room to create a partition for ubuntu adn install it there? (You would be able to boot from either your linux or mac partitions.)

---

### Post by anothernewbie on 2006-07-24
Thanks to you all---so to resume, if I did not misunderstand, the answer is that it either will work or will not, unfortunately unknown, subject to try&error---basically what I tried to avoid by posting here...

Nevertheless, once again many thanks!

Anybody out there who can tell me whether the mentioned issues get settled with an install, or whether they will remain?

---

### Post by oswaldo on 2006-07-25
I have an iBook 3G 700 too.

I'm wondering if i should install Ubuntu 6.06 on it.
When i run the Live CD, everything seems to be ok, but (there's always a but :p) it doesn't recongnize the airport card, so i can't connect to the net via wireless.

That's my story.

When i found the proper info i'll be back.

---

### Post by Skia_42 on 2006-07-25
> **oswaldo said:**
> I have an iBook 3G 700 too.

I'm wondering if i should install Ubuntu 6.06 on it.
When i run the Live CD, everything seems to be ok, but (there's always a but :p) it doesn't recongnize the airport card, so i can't connect to the net via wireless.

That's my story.

When i found the proper info i'll be back.

It is worth installing Ubuntu 6.06, it is only better when installed. And we'll help you get your Airport Card working, no worries.

---

### Post by liam_stoush on 2006-07-25
I'm running an iBook G3 700 with Dapper. I had the no-wake-from-sleep problem when I tried Breezy, and also upon installation with Dapper 6.06. Upgrading the kernel with synaptic fixed the problem for me.
I can also report total success getting airport to work out of the box.

---

### Post by anothernewbie on 2006-07-25
Hi oswaldo, also for me the airport card worked out-of-the-box, total success, even with the Dapper live CD.

Hi liam_stoush, what does "Upgrading the kernel with synaptic" mean? What about your modem, and what about your keyboard?

Thanks!

---

### Post by liam_stoush on 2006-07-25
> **anothernewbie said:**
> what does "Upgrading the kernel with synaptic" mean? What about your modem, and what about your keyboard?
Thanks!

After the CD install, I connected to the internet and updated *everything* using the [synaptic]("https://help.ubuntu.com/community/SynapticHowto") tool. Before the update, no wake-from-sleep, after, joy!
I've had no problems with my keyboard, which is the usual non-international version. I've no modem functionality to speak of at all, but then, I haven't tried.

Good luck with yours.

---

### Post by anothernewbie on 2006-07-26
Many thanks liam_stoush, this sounds excellent!!! Thus, most critical issue solved :p 

Anybody has an idea of how to get Apple's International English keyboard to work? (I would not want to invest into a US one)

Also, anybody has an idea of getting the iBook's built-in modem to work?

Thanks!

---

