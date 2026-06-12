---
title: "Added more memory, xubuntu still won't login to the console"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by abouttogiveup on 2007-04-18
It was recommended that I added more memory to my old DELL Dimension XPS T500 to take it above 128mb.  So  i have added another 128mb, but the problem still exists.

When i login it starts to load the desktop, but then the arrow/cursor disapears, and i get take back to the login screen..   

Any other suggestions please?  i've been ages trying to get my first Ubuntu install working..

M

---

### Post by Terl on 2007-04-18
What are the other specs on your pc?  What kind of video card?

Have you configured the X server?  Has the pc ever gotten to the desktop?  Can you start from the cd and get to the live desktop?

---

### Post by abouttogiveup on 2007-04-18
> **Terl said:**
> What are the other specs on your pc?  What kind of video card?

Have you configured the X server?  Has the pc ever gotten to the desktop?  Can you start from the cd and get to the live desktop?

The PC is a pentium III 500mhz or so.  It is now dual boot with about 7-8 gig allocated to the linux partitions, so plenty of space.  The graphics card is a Voodo 3D-FX 16mb.. (not wonderful eh.., but was good in its day ;) )

I have no idea about configuring x-server.

Every now and then the login does make it to the desktop.  But as soon as i try a few things it goes to a black screen and takes me back to the login..

With regards to the Live CD, I did try an install with the live CD at first, and "eventually" it did get to the desktop, but I could not install from the CD due to the fact that at the time i had only 128mb RAM.   I eventually installed it from the alternative ISO.  If i remember rightly, i may have been knocked out the the login whilst using the live CD too..  which of course was odd, as at that point you don't even have a username and password set which happens in the install.

Cheers
M

---

### Post by meborc on 2007-04-18
128mb ram is more than enough to run xubuntu... it might be slow, but it will run nicely... i had a very old lappy and although the specs were low, i still managed to use it to some simple office work...

what kind of ubuntu version are you trying to run? dapper? edgy? feisty? and was it the final release or a daily build? where did you download the cd and did the live-cd work?

a lot of Q's, but the problem could be anywhere :)

---

### Post by meborc on 2007-04-18
try ```
sudo dpkg-reconfigure xserver-xorg
```in the command line... probably the problem is with the video drivers

---

### Post by abouttogiveup on 2007-04-18
> **meborc said:**
> 128mb ram is more than enough to run xubuntu... it might be slow, but it will run nicely... i had a very old lappy and although the specs were low, i still managed to use it to some simple office work...

what kind of ubuntu version are you trying to run? dapper? edgy? feisty? and was it the final release or a daily build? where did you download the cd and did the live-cd work?

a lot of Q's, but the problem could be anywhere :)



I installed "xubuntu-6.10-alternate-i386.iso" which i think is the edgy eft???  i downloaded from the UK mirror off of the xubuntu site link about a week or so ago.  Should i have gone for 6.06?

I now have 256mb RAM and i get the problem much quicker now ;)

Cheers
M

---

### Post by meborc on 2007-04-18
> **abouttogiveup said:**
> I installed "xubuntu-6.10-alternate-i386.iso" which i think is the edgy eft???  i downloaded from the UK mirror off of the xubuntu site link about a week or so ago.  Should i have gone for 6.06?

I now have 256mb RAM and i get the problem much quicker now ;)

Cheers
M

the 6.10 is probably a better choice then 6.06 because although 6.06 is a long term support release, the 6.10 includes newer programs and kernel...

i suggest you try to reconfigure X as i posted previously :)

good luck

---

### Post by abouttogiveup on 2007-04-18
Oh dear..    manual configs and me don't seem to get on with each other.

I went throught the X reconfiguring, and managed to confiure it to not even get me to the login screen now..  well done me.  I have tried a few times but still failing.

Where would the config file be?  is there a way i can post the config for people to see if I have made any stupid errors??

Cheers
M

---

### Post by abouttogiveup on 2007-04-18
> **abouttogiveup said:**
> Oh dear..    manual configs and me don't seem to get on with each other.

I went throught the X reconfiguring, and managed to confiure it to not even get me to the login screen now..  well done me.  I have tried a few times but still failing.

Where would the config file be?  is there a way i can post the config for people to see if I have made any stupid errors??

Cheers
M

Sorry to bump this, but i'm still having problems

Cheers
M

---

