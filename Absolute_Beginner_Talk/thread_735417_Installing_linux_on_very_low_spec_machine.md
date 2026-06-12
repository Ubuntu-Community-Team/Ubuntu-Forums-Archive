---
title: "Installing linux on very low spec machine"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by bzzzzz on 2008-03-25
My father has an old Gateway P5 166 pc with 48MB RAM.

He only needs to use it for occasional web browsing and checking email, as well as the odd bit of word processing.  I was wondering if there was any stripped down linux operating system that would allow him to achieve his needs better and faster than windows 98.

Also would it be possible for him to use the same system for upgrading to broadband instead of using dial up as he currently does.

---

### Post by FrozenFox on 2008-03-25
Try puppy linux or damn small linux, in that order. If his machine used broadband instead, I don't imagine it would be an issue.

---

### Post by The Titan on 2008-03-25
damn small linux and puppy are both really good and i have installed puppy on a machine only a bit faster than that, so it should work fine

---

### Post by Jareth on 2008-03-25
Try puppy, use puppy!

---

### Post by PinkFloyd102489 on 2008-03-25
Ive only used DSL and it flies on old computers. Had it on an old 66Mhz 32MB RAM laptop that my friend picked up at a thrift store.

---

### Post by BL00dFox on 2008-03-25
I think that PC is a bit too weak for Ubuntu, I suggest you try PUPPY!

---

### Post by Helios38 on 2008-03-25
> **Jareth said:**
> Try puppy, use puppy!

agreed.



i have puppy on a usb stick, use it on any machine thats unbootable.




but for a machine like that, puppy would be perfect for it all.

---

### Post by donnyblaze1 on 2008-03-25
Once more for the record, try Puppy!

---

### Post by bzzzzz on 2008-03-26
Right thanks for your replies.  I can't quite get the gist of what you're all trying to say, but I think that I may try Puppy anyway.

---

### Post by kerry_s on 2008-03-26
go dsl, it's the standard-> 
[http://damnsmalllinux.org/](http://damnsmalllinux.org/)

---

### Post by bzzzzz on 2008-03-26
Thanks for all the help.

I just wondered does anyone know if the machine could be used for a broadband connection.  I realise it falls below the spec's that are recommended by the provider we were looking at, but I presume that the ISP are aniticipating most people using there service with a windows computer.

---

### Post by Otto-C on 2008-03-26
Take a look at [www.slitaz.org](www.slitaz.org)
It's a fast little distro.

hth
oldcity

---

### Post by ukripper on 2008-03-26
i would suggest [http://www.slackware.com/](http://www.slackware.com/) for your hardware will be perfect.

---

### Post by northern lights on 2008-03-26
In the Ubuntu family, there's [Fluxbuntu]("http://fluxbuntu.org/"), which you could also consider. [Puppy Linux]("http://www.puppylinux.org") and [DSL]("damnsmalllinux.org") have certainly been mentioned enough, thought I'd provide you with some links though.

Puppy requires a minimum 48 megs of RAM and recommended are 128, so +1 for DSL from my side.

As far as your recent question is concerned: Nothing to worry about. Any, virtually any PC with an ethernet card is capable of browsing the web - bandwith is only limited by your ISP...

---

### Post by Junglizer on 2008-03-26
> **Otto-C said:**
> Take a look at [www.slitaz.org](www.slitaz.org)
It's a fast little distro.

hth
oldcity

Yeah that looks pretty neat, I'll have to give that a shot too.

---

### Post by N1N31NCHN41L5 on 2008-03-26
Puppy - use puppy - it rocks old machines.:guitar:

---

### Post by LowSky on 2008-03-26
> **bzzzzz said:**
> My father has an old Gateway P5 166 pc with 48MB RAM.
 

May I suggest you upgrade your dad's computer, for under$200 You could build a new box that can run any distro you want, just use your old monitor
Newegg.com
 see picture

---

### Post by Sukarn on 2008-03-26
There's a sticky in this forum for this - [http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

---

### Post by northern lights on 2008-03-26
> **N1N31NCHN41L5 said:**
> Puppy - use puppy - it rocks old machines.:guitar:

> **bzzzzz said:**
> old Gateway P5 166 pc with 48MB RAM

> **northern lights said:**
> recommended are 128

...

---

### Post by bzzzzz on 2008-03-26
> **LowSky said:**
> May I suggest you upgrade your dad's computer, for under$200 You could build a new box that can run any distro you want, just use your old monitor
Newegg.com
 see picture

If it were me that's what I'd do, but as my father is adverse to spending too much cash on anything then the solution does need to be one that fits that machine.

---

### Post by Nano Geek on 2008-03-26
> **bzzzzz said:**
> Thanks for all the help.

I just wondered does anyone know if the machine could be used for a broadband connection.  I realise it falls below the spec's that are recommended by the provider we were looking at, but I presume that the ISP are aniticipating most people using there service with a windows computer.If it has the right port on the back then it should work, but I don't know how well anything will run on that PC. 

About how old is it?

---

### Post by ugm6hr on 2008-03-26
> **asjdfwejqrfjcvm msz34rq33 said:**
> If it has the right port on the back then it should work, but I don't know how well anything will run on that PC. 

I have tried DSL (damnsmalllinux) 3.4 and PuppyLinux 2.14 on very similar hardware in the past (P2, 48MB RAM).

I would suggest you **not** use PuppyLinux despite all the other pro votes, cos it will be unbearably slow on that machine (as I found out), unless you use Puppy v1.x.

The reason for this is the kernel in modern Linux distros (including Puppy 2.x and 3.x) is 2.6.  This kernel in combination with any window manager just won't cope with 48MB RAM.

Puppy 1.x is apparently still usable, but given it is no longer officially supported, I would recommend DSL.  I haven't tried DSL 4.6 on that kind of hardware, but given that it uses the 2.4 kernel (with JWM or Fluxbox), it shouldn't have greater hardware requirements than v3.4 that I used.

The other option that no one has suggested is DeliLinux.  Unfortunately, I could never get it to work on my old computer, but I gather it is designed as a Win95/98 replacement, and is more fully featured in terms of software than DSL.

Nevertheless, I'd start with DSL4.6 and see how that performs.  Web browsing (Firefox 1.x) and email (Sylpheed) is no problem with it, although word processing with Ted is less than ideal (although perhaps sufficient for the odd letter).  You can install additional software through my-DSL extensions if necessary (although I don't know what is available).

As for broadband - no problem at all.

You do need an ethernet card (if not already present) and an ethernet modem-router (ideally, rather than a simple USB modem), and it should be no problem at all with any Linux distro.

---

### Post by northern lights on 2008-03-26
> **ugm6hr said:**
> I would suggest you **not** use PuppyLinux despite all the other pro votes, cos it will be unbearably slow on that machine

+1

Finally someone agrees! What I don't get is why people would recommend Puppy (or anything else) if they haven't run that OS on similar hardware...

---

### Post by ugm6hr on 2008-03-26
> **northern lights said:**
> Finally someone agrees! What I don't get is why people would recommend Puppy (or anything else) if they haven't run that OS on similar hardware...

Don't misunderstand me though.... PuppyLinux is an *excellent* distro for *low-end* hardware (it was my primary OS before my current laptop).

However, what is described here is essentially ***obsolete*** hardware - hence my vote for DSL rather than Puppy.

---

### Post by northern lights on 2008-03-26
Exactly my point earlier -

never meant to diss Puppy - it's simply daft to recommend something for a machine with 48 megs of RAM on the basis of having loved it on a machine with 128 - which is exactly what people have done.

Enough OT though, I guess we agree anyways...

---

### Post by sleepingdragon on 2008-03-26
+1 for DSL. I would go for v3.x. 

As for the word processing thing, you should find Abiword available in the DSL repos, that seems to keep inside 48Mb quite nicely. I've had DSL on 32Mb RAM / 266Mhz running quite smoothly. 

Broadband isn't a problem, ethernet is configured easily enough - so long as you have that ethernet socket in the back!

The only pig I found about DSL is configuring printers. On the upside though DSL has some halfway decent forums and there's usually someone there to give you a hand. I seem to recall HP printers did better in DSL that most other things (pretty much the same for Ubuntu).

---

### Post by ugm6hr on 2008-03-26
> **sleepingdragon said:**
> +1 for DSL. I would go for v3.x. 

Out of interest... why v3.x?

Is v4.x actually any heavier in resource use?  Unfortunately, I have given my 48MB machine away, so can't test v4.x on it, but I do think that it has a slicker feel to it than 3.x.

Glad to hear Abiword is in the repo - probably the best basic Word Processor I have used.

> **northern lights said:**
> Enough OT though, I guess we agree anyways...

Great minds think alike, eh?

---

### Post by sleepingdragon on 2008-03-27
Why DSL v3? 

Well, I've found the HD-Install in v4 to be buggy. I had nothing but problems trying to install in VMWare - and a real install was just as problematic. Perhaps it's fixed now, I might look again, but v4 has put me off for the time being.

I'm not a great fan of the new desktop, the v3 interface just seems to look better, but that's just my opinion. 

They've moved some menu items around that IMO makes DSL a little but more awkward to use. I might just be a stickler for liking what I know, but some common features/apps are now in further sub-menus. I just don't like it.

DSL v4 takes up no more resources (well, nothing noticeable), and is a solid distro, but the interface is just plain ol' nasty to me.

---

### Post by ugm6hr on 2008-03-27
> **sleepingdragon said:**
> DSL v4 takes up no more resources (well, nothing noticeable), and is a solid distro, but the interface is just plain ol' nasty to me.

Obviously a personal taste issue.... I like v4 better!

Also, JWM (which I prefer to Fluxbox) didn't work properly for me on v3, while v4 works (and is now default).

I know that Fluxbox menus can be easily edited - never tried in JWM, but I'm sure it can't be that hard.

I installed straight to USB device from unetbootin ([http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html) v4.2.4), so can't comment on the LiveCD experience.

---

### Post by kerry_s on 2008-03-27
i agree v4 is nicer and shows dsl can still go places.

yes, jwm menus are a cinch to edit. there plain xml format. i always do my own from the start, instead of using the debian menus.

i love jwm, learning to do things with it is great. i've found it to be the most versatile window manager out there. i use jwm on my custom debian install, but i thank dsl for opening the door to it, other wise i would still be using fluxbox.
ps: you can have icons, i'm just feeling minimal, so i removed all except the 1's for rox and the 1 on the desktop to turn my screen off. :)

---

### Post by intel on 2008-03-27
You want to run Firefox ?
(with 48MB RAM ?)

Linux is not the problem here....

Don't run any window manager like GDM/KDM/ etc
(or any Desktop Environment like Gnome/KDE etc)
start the X server and directly launch a lightweight browser
(your choice is limited to Opera Browser)

As you said, the h/w is fixed.

Modern Day Linux distros do NOT run well on ancient desktop computers
(changes in s/w to take greater advantage of typical h/w & match applications usage)
if you want to give linux a fair chance to succeed for you, 
you need to throw similiar h/w its way as you would for windows.

You will need to custom compile everything, for this hardware
(or use a version used in embedded linux machines like cellphone etc)

Even after doing all this, the experience would still be a bit below using windows 95 on that h/w.

(lets face it, windows95 was a revolutionary product for its time)

---

### Post by ugm6hr on 2008-03-27
> **intel said:**
> You want to run Firefox ?
(with 48MB RAM ?)

From memory, Firefox 1.x (DSL default) works OK with 48MB.

If not, Dillo is on there too (although too basic for regular use).

---

### Post by heartburnkid on 2008-03-27
IMHO, it'd be a mistake to try using Firefox with that machine.  I love the Fox and all, but it is rather bloaty.

Opera might be a better bet if you want a modern, full-featured browser, but I'm not even too sure of that on a system that far in the past.

---

### Post by lawentzel on 2008-03-27
I've done the DSL (Damn Small Linux) on a similar machine and was really impressed.  So I say go with it!  Plus it has a very cool name.

---

### Post by bzzzzz on 2008-03-28
OK I'm grateful for all the advice.  Now do I go for a boot from disk version, or (as I would prefer) can I install it.

To install it will I be able to download the operating system and then copy it to a cd so that I can install it.  I will do a bit of experimentation with browsers myself, but I really need a very user friendly browser. 

I've looked on ebay and it looks like you pick up a pci ethernet card for less than £10.  Am I right in thinking that this will not only fit but also be likely to be compatible with the pc.  The pc does have pci slots as there is a pci modem (dial up).

---

### Post by ugm6hr on 2008-03-28
> **bzzzzz said:**
> OK I'm grateful for all the advice.  Now do I go for a boot from disk version, or (as I would prefer) can I install it.

To install it will I be able to download the operating system and then copy it to a cd so that I can install it.  I will do a bit of experimentation with browsers myself, but I really need a very user friendly browser. 

I've looked on ebay and it looks like you pick up a pci ethernet card for less than £10.  Am I right in thinking that this will not only fit but also be likely to be compatible with the pc.  The pc does have pci slots as there is a pci modem (dial up).

DSL is available for download to CD here: [http://www.damnsmalllinux.org/download.html](http://www.damnsmalllinux.org/download.html)

Just download the latest number .iso file and write to CD.

You can boot from CD to try it out, but you will probably have to install to HD with a swap file to get decent performance.

You can probably get an ethernet card for even less than £10.  And about 99% ethernet cards work with Linux.  I would try and get a genuine Realtek card.

You would obviously need a broadband modem-router to go with it.

EDIT:
For example: [http://www.pcworld.co.uk/martprd/product/seo/685029](http://www.pcworld.co.uk/martprd/product/seo/685029)
Which is a Realtek card (I think): [http://www.sheffieldforum.co.uk/showthread.php?t=104007](http://www.sheffieldforum.co.uk/showthread.php?t=104007)

EDIT 2:
Actually, ebay has cheaper options than £10 too: [http://cgi.ebay.co.uk/Dynamode-Realtek-10-100-Lan-Network-Card-BNIB_W0QQitemZ300210159043QQihZ020QQcategoryZ51195QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.co.uk/Dynamode-Realtek-10-100-Lan-Network-Card-BNIB_W0QQitemZ300210159043QQihZ020QQcategoryZ51195QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)

---

### Post by cookbooking it on 2008-03-28
Have you considered just increasing the ram? I have an old P166 laptop that I want to put Linux on. I found memory that will go in that laptop pretty cheap on ebay, and not all of it is used. It pays to look around. Official sources for the memory had ridiculously high prices.
I look forward to reading how things work out with your father's computer!

---

### Post by daberger on 2008-03-28
try xubuntu.
get it with wubi and u can dual boot and decide which is faster

---

