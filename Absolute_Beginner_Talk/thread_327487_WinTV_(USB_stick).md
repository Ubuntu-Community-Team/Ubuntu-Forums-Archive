---
title: "WinTV (USB stick)"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by staib on 2006-12-29
Hi all

My wife gave me another little gadget :rolleyes: on the 25th.  It's a "Hauppauge WinTV Nova - T". The description is about the same length as this little usb stick!  Comes with a cute little aerial as well for capturing digital terrestrial signals (aka as FreeView in the UK).

I would love to get it running in Ubuntu 6.10.   Is there any chance, or is this one of those linux hardware driver problems? In XP it includes the ability to record and "pause" TV and seems to work fine.

I have tried all sorts of searches, but most seem to point to their WinTV cards, and I suspect the digital usb drivers are very different :-?

Cheers,

Nick

---

### Post by anaconda on 2006-12-29
[http://www.ubuntuforums.org/showthread.php?t=321567&highlight=wintv](http://www.ubuntuforums.org/showthread.php?t=321567&highlight=wintv)

hauppauge WinTv Nova-T USB2
is well supported, but it is not the same model than hauppauge WinTv Nova-t USB2 stick.. which isn't yet completely supprted.

But if you get it working then it wll record and pause just fine. Easiest TV-watching program to install is probably kaffeine..

---

### Post by staib on 2006-12-30
Thanks - I finally got it working!  :)   

I found the advice on this [French website]("http://doc.ubuntu-fr.org/materiel/wintv_novat") worked perfectly - glad now I paid attention at school!

Happy New Year (et Bon Annee) all.

Nick

---

### Post by staib on 2006-12-31
Now that I have had a play with Kaffeine running under Edgy Eft displaying digital TV from a [Hauppauge WinTV Nova-T stick]("http://www.pcworld.co.uk/martprd/store/pcw_page.jsp?BV_SessionID=@@@@1565321356.1167564637@@@@&BV_EngineID=ccdeaddjkighdkmcflgceggdhhmdgml.0&page=Product&fm=null&sm=null&tm=null&sku=970228&category_oid="), I have to say it is just brilliant :p 

To any other Linux newbies out there, tempted by being able to watch or record digital TV, I say give it a try. Kaffeine (via Synaptic) includes a neat way of simply choosing a program (by name) up to a week ahead, and telling it to record it.  No faffing around with start times and end times etc. Picture quality is DVD like.

The included antenna (a tiny little whip aerial) could not get ALL the stations, but plugging in a slightly better one (from Waitrose) did the trick.

Instructions were followed to the letter from the French website mentioned in the post above.

Cheers,

Nick

---

### Post by anaconda on 2007-01-02
Good for you!
The only thing I would like to comment is that in the french instruction the firmware(driver) is copied to /lib/firmware/2.6.17.386'' -folder..
but in ubuntu it is enough to copy the driver to 
/lib/firmware  -folder
The difference is that if you have the driver in /lib/firmware you don't need to do anything when you change to a new kernel. Othervice you would have to copy the driver to the new kernels directory..

---

