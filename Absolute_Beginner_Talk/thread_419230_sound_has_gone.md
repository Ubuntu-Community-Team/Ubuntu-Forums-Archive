---
title: "sound has gone"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by up_quark on 2007-04-22
hi, im soldiering on with my ubuntu, so far so good, except suddenly i have no sound!
first time i used rythmbox it worked perfectly, but suddenly i have:
no sound.
no system sounds.
as far as i know i havent removed any packages.
i have reinstalled easy ubuntu, this didnt work.
no doubt this is something obvious (yes, my speakers are switched on and plugged in!)

thanks for any tips.
loving ubuntu!

if this is any help i just noticed that the timer on rythmbox is going way to fast and is
a bit irregular - the seconds are going at about twice the correct speed.

?

---

### Post by lonce on 2007-04-22
i had this issue on my toshiba laptop.  Turns out the sound wasnt gone, just really low.  If you do a search on here you will find it.  You have to add a line to a file to make it all happy. It takes less than a minute to do and all is fine afterwards.

---

### Post by marko_4454 on 2007-04-22
> **up_quark said:**
> hi, im soldiering on with my ubuntu, so far so good, except suddenly i have no sound!
first time i used rythmbox it worked perfectly, but suddenly i have:
no sound.
no system sounds.
as far as i know i havent removed any packages.
i have reinstalled easy ubuntu, this didnt work.
no doubt this is something obvious (yes, my speakers are switched on and plugged in!)

thanks for any tips.
loving ubuntu!

have you seen the options in alsamixer:
```
alsamixer
```
Make sure nothing is muted. Also, raise volume in that menu.

---

### Post by up_quark on 2007-04-23
thanks lonce
i have actually searched the forums quite thoroughly.
youre right, there are a few posts addressing similar problems,
most of which i read before posting.
instead of saying "you can find the answer on the forums"
it would be really helpful if you just posted the answer.
turns out i dont have a toshiba laptop.
i have a msi k7n2g, using onboard sound card.
this is recognised by ubuntu in alsamixer, which ive just checked
levels are all up.
i dont understand why the sound would just suddenly stop working.

oh and i have also just upgraded to 6.10 this morning, still doesnt work.

---

### Post by STREETURCHINE on 2007-04-23
hi i have edgy 6.10 and i have the same problem but i can get it back by rebooting a few times it then works till i shut down next.
i have actually asked about this a couple of times and still have no real solution.

so i hope you find the awnser,and post it here

---

### Post by Sef on 2007-04-23
I have had problems too with sound.  Both of these idea worked for me.  I hope one or both work for you.

[Idea 1]("http://ubuntuforums.org/showthread.php?t=160576")

[Idea 2]("http://ubuntuforums.org/showthread.php?t=134041")


To check your alsa-base list, from the terminal (Applications > Accessories > Terminal), type in this command:

```
gksudo gedit /etc/modproble.d/alsa-base
```

---

