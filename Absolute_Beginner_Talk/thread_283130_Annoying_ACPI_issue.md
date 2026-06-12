---
title: "Annoying ACPI issue"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by unlokia on 2006-10-23
As always with Linux, there seems to be 100 ways to do ONE SIMPLE thing... annoying!. I have an ACER ASPIRE 1640zwlmi laptop - Edgy Eft installed - running on battery this evening and guess what?!!

WITHOUT warning etc, it just goes "zoom" and dies - and I mean LITERALLY shuts off, not shuts DOWN... battery runs outa juice and it went off in half a second.

WHAT IS GOING ON ](*,) ??

The battery Icon doesn't even display the proper charge state - it says 0% ALL the time, whatever thats meant to be :???: 

Why did my BRAND NEW laptop not talk to Ubuntu, and why did Ubuntu not warn me?. Just DIES when battery is dead. I would think this needs attention, but for my sake PLEASE don't talk in geek language - speak to me and tell me what I am doing wrong?!!!

Many many thanks!!

---

### Post by unlokia on 2006-10-23
Well??... :(

---

### Post by podunk on 2006-10-23
Edgy Eft is pretty much a beta still, plus it sounds like you have a bleeding edge computer? It may well be that you have found a bug, or that your computer is so new that Linux drivers don't support your battery. Cold comfort, but you can file bug reports here:
[https://launchpad.net/distros/ubuntu/+filebug/+login](https://launchpad.net/distros/ubuntu/+filebug/+login)

Another possibility is maybe you have the sensor configured improperly? It shows 0% all the time?

---

### Post by unlokia on 2006-10-24
I can't be THAT bleeding edge dude - Mandriva acpi works 110%!. What annoys me more than anything, is that when you type "acpi" or "battery" or "cpu" into synaptic, lo and behold, one hundred odd suggestions all pop up, every one of them vying for your attention and hoping to be installed! ](*,) 

Is it JUST me, or is this the usual case of too many tools for one job?!. Don't wanna have to abandon Ubuntu when I have JUST got to love it :)

Thanks

---

### Post by po0f on 2006-10-24
unlokia,

Are you sure this isn't a thermal issue?  Maybe Edgy's kernel is having problems with your hardware (you do know it isn't officially released yet, right?).  Does your laptop feel hot?

---

### Post by unlokia on 2006-10-24
Yeah I know its not released til Thurs :)

I wouldn't say it was hot, no. However I have come across times when the cpu fan ramps up to 100% for NO apparent reason at all :???: and it is not even that hot!.

This is just weirddddddddddd

---

### Post by jiberwabish on 2006-10-24
I would say that it just shut off because you're battery died. (obviously i know)

It didn't warn you because your ACPI isn't working and ubuntu has no clue what your batter is at (or even that you're running on one)

So you're problem lies in ACPI not working.

Add acpi=on  to you boot paramaters when starting up ubuntu, if that still doesn't work than you problem is too difficult for me to handle.

-J

---

