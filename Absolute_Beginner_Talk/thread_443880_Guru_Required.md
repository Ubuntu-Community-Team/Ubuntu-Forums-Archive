---
title: "Guru Required"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by makiroll on 2007-05-14
hi! I'm new to linux and really need a guru who can guide me in my Ubuntu-ing!

good knowledge of Bash and Driver fixing stuff required! Please reply soon! I need you!

---

### Post by BarfBag on 2007-05-14
I don't think I'm a Guru, but I might be able to help.  Here's a suggestion - post all information possible in your first post.  If you wait, less people will notice your topic.

---

### Post by starcraft.man on 2007-05-14
Are you trying to request someone come over to your house? (I actually saw a request like that a few days ago...) Cuz if your not, you will need to give quite a bit more information to get a serious response that is useful....

Like to start your computers hardware, what graphics card (i assume thats the driver your referring to) you are using, and any anomalous error messages you got and what you did to get them i.e. how you tried to install them if you did.

---

### Post by reacocard on 2007-05-14
How about the forums as whole? Collectively we're a much better guru than any of us are on our own. Just post your exact problems (with details!) and you'll almost certainly get help.

EDIT: for others who come across this thread, here are his problem threads (as of this writing):
[Resolution problems (driver??)]("http://ubuntuforums.org/showthread.php?t=443658")
[problems with IPW2200 wireless card!...]("http://ubuntuforums.org/showthread.php?t=328405")

---

### Post by earobinson on 2007-05-14
google and the fourms are your 2 new best friends!

---

### Post by Happy_Man on 2007-05-14
there is always [http://linuxcommand.org](http://linuxcommand.org) for intro to bash....

---

### Post by makiroll on 2007-05-14
well, i'd made a post or two in the past without response, so I was hoping that i might find someone who would be willing to MSN or IRC me as I work through problems that i'm solving right now.

I'm trying to sort out a nvidia problem (or rather a resolution problem in general). alas though, it's not MY computer, so i do not have it on me at the moment. not until the weekend where I will need intense quick response- my GF bought a new pc; got annoyed with vista and let me put ubuntu on it; and I havent been able to sort out the resolution issues as it's stuck in standard 1280×800 whereas it should be 1440 x 800. And she is getting really annoyed with ubunutu and I fear she'll wantto go back to linux before her system is even ready to judge.

I've treid doing a lot of things but each time i seem to just screw up the xorg and either the x server cant initiate or the screen is black (still makes the login noise)

but, to begin with: (off the top of my head)

its an acer aspire 9300,
Geforce go 6100
17" widescreen crystalbrite display
1Gb RAM

Trying to run Ubuntu 6.06 Dapper Drake

Can anyone help me? where hath i gone wrong? I'm not very good at linux as I'm a real n00b. geek is my second name, but i'm finding myself floundering a lot and need to get this fixed asap x_X

---

### Post by reacocard on 2007-05-15
> **makiroll said:**
> well, i'd made a post or two in the past without response, so I was hoping that i might find someone who would be willing to MSN or IRC me as I work through problems that i'm solving right now.

I'm trying to sort out a nvidia problem (or rather a resolution problem in general). alas though, it's not MY computer, so i do not have it on me at the moment. not until the weekend where I will need intense quick response- my GF bought a new pc; got annoyed with vista and let me put ubuntu on it; and I havent been able to sort out the resolution issues as it's stuck in standard 1280×800 whereas it should be 1440 x 800. And she is getting really annoyed with ubunutu and I fear she'll wantto go back to linux before her system is even ready to judge.

I've treid doing a lot of things but each time i seem to just screw up the xorg and either the x server cant initiate or the screen is black (still makes the login noise)

but, to begin with: (off the top of my head)

its an acer aspire 9300,
Geforce go 6100
17" widescreen crystalbrite display
1Gb RAM

Trying to run Ubuntu 6.06 Dapper Drake

Can anyone help me? where hath i gone wrong? I'm not very good at linux as I'm a real n00b. geek is my second name, but i'm finding myself floundering a lot and need to get this fixed asap x_X

Can't you just edit /etc/X11/xorg.conf to add that resolution? The setting is in the 'Screen' section.

As for live help, I'm not an expert in these areas, but I'm willing to help as I can. My jabber ID is [email]reacocard@jabber.org[/email], and I'm also reacocard on IRC.

---

### Post by ikonia on 2007-05-15
ask specific questions and you'll get good answers, ask someone into private chats to teach you - and you'll get a bill.

---

### Post by makiroll on 2007-05-15
> **reacocard said:**
> Can't you just edit /etc/X11/xorg.conf to add that resolution? The setting is in the 'Screen' section.

As for live help, I'm not an expert in these areas, but I'm willing to help as I can. My jabber ID is [email]reacocard@jabber.org[/email], and I'm also reacocard on IRC.

I've tried changing the resolution with xorg.conf but the x server wont accept the new resolution and reverts to giving800x600 instead and removes the resolution i've tried to replace.

---

### Post by bobplano on 2007-05-15
why don't you try the easy way of editing the xorg? just
```
sudo dpkg-reconfigure xserver-xorg
```
and answer the questions as best you can

---

### Post by chamberlain2006 on 2007-05-15
If you need some help on MSN, I'd be happy to help/

---

### Post by makiroll on 2007-05-15
> **chamberlain2006 said:**
> If you need some help on MSN, I'd be happy to help/

I'd really appreciate it. my msn is [email]room304@homail.co.uk[/email]

---

### Post by chamberlain2006 on 2007-05-15
There, i just added you.  See you in a minute.

---

### Post by makiroll on 2007-05-15
> **chamberlain2006 said:**
> There, i just added you.  See you in a minute.

not seeing you online yet, did you type it in right? [my addy]

---

### Post by chamberlain2006 on 2007-05-15
Copied it directly from the browser.  [email]room304@hotmail.co.uk[/email]?

---

### Post by makiroll on 2007-05-15
> **chamberlain2006 said:**
> Copied it directly from the browser.  [email]room304@hotmail.co.uk[/email]?

well, i'm online now, if I dont appear online, let me know yours and I'll add ye

---

### Post by chamberlain2006 on 2007-05-15
Youre not online.  Try adding me, [email]chamberlain2007@gmail.com[/email]

---

