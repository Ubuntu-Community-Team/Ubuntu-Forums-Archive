---
title: "installation is slow...then hangs"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by ishift on 2006-08-23
hey there..

i'm having some problems installing ubuntu on my amd desktop. i previously installed it on my t20 thinkpad without any major problems (besides the usual wireless and media stuff).

ok, so, on my desktop, the installation is very slow. it's like the cd is being read very slowly. not only that, the "time remaining" increases and only decreases when the percentage goes up 1%. then, it got so slow that it eventually hangs up. it hung up on 49%, showing "34:36 remaining". i did a cd check (this is the same cd i used for my thinkpad) and a couple of files show mismatch. i don't get it.

any ideas? ](*,) 

thanks!

---

### Post by coolclassic on 2006-08-23
What are the specs for your pc

---

### Post by ishift on 2006-08-23
processor:  amd 2200+
memory:     2.6 gb
vid card:   nvidia geforce2

dvd drive

hd:         70 gb (ubuntu hd)
            20 gb (xp install)

i installed xp first on the 20 gb hd. it's the slave hd. could that be a problem?

---

### Post by nixclusive on 2006-08-23
> **ishift said:**
> processor:  amd 2200+
memory:     2.6 gb
vid card:   nvidia geforce2

dvd drive

hd:         70 gb (ubuntu hd)
            20 gb (xp install)

i installed xp first on the 20 gb hd. it's the slave hd. could that be a problem?

try to take the installation procedure nice and slow, use hdparm:

```
sudo hdparm -d 0 /dev/hd?
```

where '?' is your cd drive...sometimes blazing drives create read errors.

---

### Post by ishift on 2006-08-23
> **nixclusive said:**
> try to take the installation procedure nice and slow, use hdparm:

```
sudo hdparm -d 0 /dev/hd?
```

where '?' is your cd drive...sometimes blazing drives create read errors.

what do you mean "nice and slow"? sorry, i'm kind of a n00b when it comes to linux.

---

### Post by Turgon on 2006-08-23
Sounds like the cd has been damaged since you installed it on you laptop. I guess you just need to burn a new one.

---

### Post by ishift on 2006-08-23
hmm...ok. i'll try that out.

btw, does it matter what speed i burn the new copy? because on the kubuntu forums, i read that 16x works best, and it did on my laptop.

ps. now i'm wondering if (and how) my cd got damaged...:confused:

---

### Post by coolclassic on 2006-08-24
Is your dvd a slave? try it as master also
Is it a slave to your 20gb drive? try making it a slave to your 70gb

---

### Post by ishift on 2006-08-24
hmm...i'm not sure. however, some things have come up that need my attention, so i'm putting my desktop installation on hold for a while. thanks for the help though!

on a related note, i'm half-considering trying gentoo for my desktop.

again, thanks! i'll try those suggestions out and let you guys know what happens.

---

### Post by TrendyDark on 2006-08-24
If you reburn the CD, use a slow write speed to avoid errors.

---

### Post by TrendyDark on 2006-08-24
If you reburn the CD, use a slow write speed to avoid errors.

---

### Post by ishift on 2006-08-24
will do. thanks!

---

### Post by ishift on 2006-08-27
all right, so i tried to install a dualboot again. the live cd boots up slowly, even to the point where it does it in text mode. then, as it's in the process of installing, it slows down to a crawl and then just stops. i tried it twice. i have tried to do with a newly burned cd, but it's the same thing. the specs for the pc again are:

cpu1: amd 2200+
cpu2: amd 2200+

video: nvidia geforce2
memory: 2.6 gb

2 scsi hds:

hda: 17gb (win xp installation)
hdb: 70gb (ubuntu installation)

what do you guys think?

---

### Post by ishift on 2006-08-27
ok, so i got another hd for ubuntu..same thing happened. it gets stuck midway. could it be that my dvd-rom is "too fast" for the live cd?

help!

---

### Post by ishift on 2006-08-27
well, final update...

i replaced the dvd-rom with an old cd-rom. worked like a charm. ubuntu installed in less than 30 mins. not only that, i know have a dual-boot with windows xp.

moral of the story:  ***[COLOR="DarkRed"]don't give up[/COLOR]***

---

### Post by bjkd on 2007-04-04
Hey ishift.
Thanks for working that one out! :)  I was having similar problems installing 6.06 on an Acer Veriton 3600G P4 2.6GHz 512MB. Installation would hang at a different point every time I tried. Not at the same point every time which made it confusing. I tried all of the other usual things suggested in other threads such as noapic, nolapic, VGA screen, safe video mode etc but still no joy. Then I found your thread and thought I'd give that a go. So I disconnected the DVD drive hooked up an old CD drive and, bingo, it installed first try. So does anyone know why this was the case? Maybe it's a bug that needs to be sorted. I was nearly ready to give up trying. I'm glad I finally got it to work.

---

