---
title: "latest stable release of ubuntu?"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by mahela007 on 2008-03-21
what is the latest stable ubuntu release ? 
and what is the next upcoming stable release and when will it be available?
Also i Would like to know where i can information about such things? (eg a weekly or monthly news letter)

---

### Post by philinux on 2008-03-21
[http://www.ubuntu.com/](http://www.ubuntu.com/)

7.1 Gutsy is the current stable but 8.04 Hardy is due shortly.

---

### Post by N1N31NCHN41L5 on 2008-03-21
When Hardy comes out do you have to start over or can you upgrade from Gutsy Gibbon

---

### Post by Jimmyfj on 2008-03-21
The latest stable version of Ubuntu would be 7.10 Gutsy Gibbon - The next stable release, which also is the next LTS version is Ubuntu 8.04 Hardy Heron which is out now in Alpha 6. Else you could keep an eye on the adress [http://www.ubuntu.com](http://www.ubuntu.com)

The nicest thing is that you need not start over. You can simply do an upgrade online. But, as always, a clean install will provide the best result.

---

### Post by Myglaren on 2008-03-21
You can upgrade from Gutsy.  I did it experimentally, had the discs just in case but it went swimmingly and works better now than it did with Dapper, which was going a bit wonky.

---

### Post by bumanie on 2008-03-21
Ubuntu havve a new stable release come out every six months. One comes in April and the other in October. In between, if you want to help with testing the next release you can use the alpha versions and report any bugs you find. It is best not to use this as your main OS, as some bugs break the OS. Hardy heron is due for release on 24th of April. The beta version is due out in about 10-14 days (don't know exact date).

---

### Post by philinux on 2008-03-21
> **N1N31NCHN41L5 said:**
> When Hardy comes out do you have to start over or can you upgrade from Gutsy Gibbon

The latest release of Hardy is now not alpha 6 it's a beta.

I updated last night using

update-manager -d

I have home on it's own partition so re-installing is easy, if this dont work out.

---

### Post by mahela007 on 2008-03-21
have any of you guys used hardy ? Is it good?

---

### Post by pieisgood4589 on 2008-03-21
Well, Hardy isn't the newest release, Gutsy is, although Gutsy does have a bug with the startup splash screen not showing up on some video cards, so what I always do is just install Hardy, then upgrade to Gutsy. :)

---

### Post by PmDematagoda on 2008-03-21
> **mahela007 said:**
> have any of you guys used hardy ? Is it good?

In my opinion it is very good. But my advice to you is, if you are still not comfortable with the terminal or do not want to face many problems on Ubuntu then use the current stable version of Ubuntu(that being Ubuntu7.10) until Ubuntu Hardy Heron is released.

---

### Post by philinux on 2008-03-21
> **mahela007 said:**
> have any of you guys used hardy ? Is it good?

Like I said I upgrade my gutsy last night.  Also did a clean install of alpha6 last week that got borked with an update. Not for the faint hearted.

As of yesterday it went to a beta version, first time ever I think, so I did the upgrade. So should be a bit better now.

To be honest. I've not noticed much difference yet. Still testing.

FF3 was quicker when it was in alpha, now its 3.0b4 it seems slower.

[http://www.ubuntu.com/testing/hardy/beta](http://www.ubuntu.com/testing/hardy/beta)

---

### Post by k01 on 2008-03-21
Love it! ;)

---

### Post by philinux on 2008-03-21
I definitely need a new pc, this one is from 1999. Hardy takes longer to boot and longer to log in. But when I get my new pc later this month it should fly.

I'm only using this old croc as a test bed, If it breaks I've got winblows ME on my other HD. 

And the miracle of linux the live cd.

p.s. the hardy live cd needs more memory to run than gutsy.

---

### Post by Jimmyfj on 2008-03-21
philinux

I haven't noticed that Hardy went from Alpha to Beta - I've been on hardy since Alpha 1 and got that freaking update that crashed my system too. All a'board - Once more - Alpha, and Beta software MAY break and we all know that. But overall Hardy IS a great improvement from Gutsy or Feisty. I loved running Ubuntu before, now I just love it twice as much. Even my previous problems with Compiz Fusion on my 256 MB ATI Radeon 9500 Graphics card is in the past now. But whether Hardy is Alpha or Beta I couldn't care less. It's still the best OS ever.

---

### Post by philinux on 2008-03-21
> **Jimmyfj said:**
> I haven't noticed that Hardy went from Alpha to Beta - I've been on hardy since Alpha 1 and got that freaking update that crashed my system too. All a'board - Once more - Alpha, and Beta software MAY break and we all know that. But overall Hardy IS a great improvement from Gutsy or Feisty. I loved running Ubuntu before, now I just love it twice as much. Even my previous problems with Compiz Fusion on my 256 MB ATI Radeon 9500 Graphics card is in the past now. But whether Hardy is Alpha or Beta I couldn't care less. It's still the best OS ever.

[http://www.ubuntu.com/testing](http://www.ubuntu.com/testing)

I'm just glad they fixed the libc6 which borked it last week.

---

### Post by Jimmyfj on 2008-03-21
> **philinux said:**
> [http://www.ubuntu.com/testing](http://www.ubuntu.com/testing)

I'm just glad they fixed the libc6 which borked it last week.

It was borked alright - SLAM and the sys went walkabout.

---

### Post by mahela007 on 2008-03-21
see the problem is I accidentally changed the refresh rate of my monitor on ubuntu . and now I cant see anything .. just weird lines on the monitor. So i dont have anyway of changing the refresh rate back to the proper value. I'm thinking of reinstalling ubuntu. But that would change the GRUB loader. and to fix the GRUB loader i have to have the windows disk. I dont have the windows disk. So I am stuck. Any suggestions?

---

### Post by PmDematagoda on 2008-03-22
An Ubuntu reinstall is not required, just boot Ubuntu in Recovery Mode and then execute this command:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
This will return the X-Server to it's defaults(pretty much).

After that is completed, test the X-Server with:-
```
sudo startx
```

---

### Post by mahela007 on 2008-03-22
I tried that. It just says "warning, file may be ....(something something"" and then says backup made in (something something).

---

### Post by PmDematagoda on 2008-03-22
That is fine, did you just check the X-Server?

---

### Post by SunnyRabbiera on 2008-03-22
Me i would never label gutsy as stable, if its stability you want go with dapper though its on its way out.
My advice is to hold out if you want stability and a more recent release in the form of hardy.

---

