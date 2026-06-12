---
title: "PeoplePC + Actiontec External= GTFO?"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by fruitsofherwomb on 2007-05-01
Well, My friend gave me a Actiontec USB/Serial 56k External Modem (model EX600). I have People PC.

First I used [google]("www.google.com") (cause its my friend ;) ) and Found this [guide]("http://ubuntuforums.org/showthread.php?t=220173"). 

Followed it. I got to ask me if I wanted it to dial out or Disconnect. Here is some of the problems. First of all it doesn't connect (lol) it just makes a bunch of noises and then disconnects me. Second is that Pulse and Tone, automatically chooses pulse even though I set it to Tone. 

I had a conversation with a Friend and said it could be the ISP, and Might need a dialer. I don't think so cause I found [this]("http://forum.freespire.org/showthread.php?p=54425") (check the last guys post) also I connect through window dialer *don't know the official name* and even got it working on my Dreamcast (brother was hogging the PC with frets of Fire.) 

So people got the Action-tec modem I have working and they also have signed on Ubuntu with People PC, So what is wrong with it or does Tux just hate me :( . 

**Short List of Haves (if you are lazy to read above): **
- Windows XP Home Edition and Ubuntu 7.04 dual boot
- Actiontec USB/Serial 56k External Modem 
- ISP People PC

**Problem:** 
- Dials then drops

---

### Post by NeoTaoistTechnoPagan on 2007-05-01
I tried to get Ubuntu working with PeoplePC and had one hell of a time. I read in some far-off forum that someone once got it working, but that ISP uses some weird sort of dialer that rehashes the username to something strange. I have notes about it on my home forum, so to save me some typing feel free to check there.

Good luck!

---

### Post by fruitsofherwomb on 2007-05-01
Linux is a struggle, lol its going to be great when I get it up and running. 

Does anyone know a good ISP that is Linux 'friendly'

---

### Post by fruitsofherwomb on 2007-05-01
[-o<

---

### Post by fruitsofherwomb on 2007-05-01
Dial Guard does nothing for me. I start my connection and it pops a window that has *, I press OK then it starts to dial, then it connects... what is it suppose to do? 

anyway, btw i'm not connecting with people pc software. tis full of aids and failure.

---

### Post by Bartender on 2007-05-03
That little problem you mentioned where "Tones" keeps going back to "Pulse" - that's a bug in Feisty and Edgy.  The GUI dialer is broken and nobody at Ubuntu seems to care.  You either find a way around it or go back to Dapper or go to another distro.

---

### Post by westburian on 2007-06-30
First thing you need to do is ditch People's PC. Here's why. People PC is one of those ISP's that do not let you connect directly via the ppp (point to point) protocol like a 'real' ISP, where you simply need just a few pieces of information, your username, password, dns numbers, and the number to dialup and connect. Instead, in order to 'simplify' things in an otherwise 'windows' world, they require you to download THEIR windows software in order to connect, you enter your username/password, their software redirects it to their own (hidden) ppp software to connect you, you not only lose direct control, but are restricted to using windows. This is easily solvable by using a REAL ISP. Other ISP's that use this required log-on scheme are juno, netzero, and aohell. To prove my point, look at this page from freedomlist.com - - -

[http://www.freedomlist.com/find.php3?cheap_dialup_national=166&row=6](http://www.freedomlist.com/find.php3?cheap_dialup_national=166&row=6)

you'll notice that in the DUN (dial up networking category) that everything on that page is checked in the DUN column except juno and netzero, go to about page 10 or 11, you'll see that people pc is also unchecked. You have to use THEIR (windows) software to connect.....

now go to page one, you'll see that dialup.cc is $4.94 a month, I've been with them almost a year now, mail in a check/money order (they may not let you do that anymore) and have had ZERO problems. I use DOS, yes DOS internet, linux, and (lowering head) windoze.

I ended up here because I am waiting on a new computer and was googling for actiontec's serial external modems to see what kind of success people are having wtih them.... the fact that it dials and connects, means ubuntu has found it and using it, it disconnects because people pc is expecting it's hidden/rehashed usernmae password....

if anyone signs up with dialup.cc and you wanna refer me so I can get a free month, I'll graciously accept...

btw, I installed UBUNTU on a p 350 mhz and like it so far, the modem on that box is an ISA rockwell modem, no problems connecting to dialup.cc whatsoever....

---

### Post by Tuxtur on 2007-06-30
for what its worth I have AT&T dialup and couldn't get Ubuntu to connect until I used synaptic to get the KDE dialer KPPP. it just works, easy to configure, ended the tone to pulse issue.

---

### Post by westburian on 2007-06-30
> **fruitsofherwomb said:**
> Linux is a struggle, lol its going to be great when I get it up and running. 

Does anyone know a good ISP that is Linux 'friendly'


yep.... see my other post. Ditch people pc and use an ISP that does not require their proprietary windows software to connect.... avoid "ISP's" such as netzero, juno, aol (LOTS of other reasons to avoid aol, that's another topic!).

you can find a cheap dialup ISP at freedomlist.com

I've been with dialup.cc for about 9 months, and connect with no problems using many linux distros, as well as DOS and whingdoze...

if you go with dialup.cc lemme know so I can say I referred you (yes, I'll get a free month's service :)

---

### Post by Bartender on 2007-07-02
Also, you don't need to get your Linux PC connected to the internet to get gnome-ppp installed
[http://ubuntuforums.org/showthread.php?t=480717](http://ubuntuforums.org/showthread.php?t=480717)

EDIT:  I googled "Actiontec ex600" - all I got was links to this thread!!  That modem must be pretty scarce.  Are you sure it's a full hardware modem?  If it's serial it should be but I think some aren't, especially if they have a USB outlet also.

---

