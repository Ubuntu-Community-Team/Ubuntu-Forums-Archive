---
title: "Seagate FreeAgent spindown fix! (May work for others as well)"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by kernel tom on 2008-01-26
Hey all,

I've been having spindown problems with my Seagate external hard drive.  But I found this site that had an explanation on how to turn off this powersaving feature...

[http://alienghic.livejournal.com/382903.html](http://alienghic.livejournal.com/382903.html)

to summarize...
```

sudo apt-get install sdparm

sudo sdparm -a /dev/sde
```
(not really sde but wherever ur drive is ie. sdb,sdg, etc)

you'll get an out put like this
    /dev/sde: Seagate   FreeAgent Pro  400A
Power condition mode page:
  IDLE        0  [cha: n, def:  0, sav:  0]
  STANDBY     1  [cha: y, def:  1, sav:  1]
  ICT         0  [cha: n, def:  0, sav:  0]
  SCT       9000  [cha: y, def:9000, sav:9000]

and we want to change STANDBY to 0 (this will also make SCT 0, i believe the 9000 is how many seconds until it spinsdown)```


sudo sdparm --command=start /dev/sde
sudo sdparm --clear STANDBY -6 /dev/sde
sudo sdparm -a /dev/sde

```
and the output now looks like this ...

    /dev/sde: Seagate   FreeAgent Pro  400A
Power condition mode page:
  IDLE        0  [cha: n, def:  0, sav:  0]
  STANDBY     0  [cha: n, def:  1, sav:  0]
  ICT         0  [cha: n, def:  0, sav:  0]
  SCT         0  [cha: n, def:9000, sav:  0]


as far as i've tested, this stays in effect even after umount/mount AND if ur dev file is different after another mount ... then again i mount using UUID so that could be why.

-kt

---

### Post by sammydadams on 2008-01-31
thanks....i know i saw this late, but it worked like a charm for me

---

### Post by LittleLORDevil on 2008-02-01
Thanks a lot I just switched to Ubuntu as my only OS and this is a great help to me staying!

---

### Post by LittleLORDevil on 2008-02-01
Actually mine isn't fixed anymore, I don't know why when I get the info after the fix and after a reboot the settings stay:

    /dev/sdb: Seagate   FreeAgentDesktop  100F
Power condition mode page:
  IDLE        0  [cha: n, def:  0, sav:  0]
  STANDBY     0  [cha: n, def:  1, sav:  0]
  ICT         0  [cha: n, def:  0, sav:  0]
  SCT         0  [cha: n, def:9000, sav:  0]

---

### Post by sammydadams on 2008-02-01
on mine, i have to run 
```
sudo /etc/init.d/hal restart
```
in the terminal sometimes cause it doesn't seem to want to mount the drive...give that a shot

---

### Post by kernel tom on 2008-02-05
> **LittleLORDevil said:**
> Actually mine isn't fixed anymore, I don't know why when I get the info after the fix and after a reboot the settings stay:

    /dev/sdb: Seagate   FreeAgentDesktop  100F
Power condition mode page:
  IDLE        0  [cha: n, def:  0, sav:  0]
  STANDBY     0  [cha: n, def:  1, sav:  0]
  ICT         0  [cha: n, def:  0, sav:  0]
  SCT         0  [cha: n, def:9000, sav:  0]

Yeah the purpose of this post was to show how to change these setting perminately.

but if you need to change anything back you should be able to reverse engineer the steps above

what exactly do you want as far as power settings on ur external?

-kt

---

### Post by LittleLORDevil on 2008-02-12
> **kernel tom said:**
> Yeah the purpose of this post was to show how to change these setting perminately.

but if you need to change anything back you should be able to reverse engineer the steps above

what exactly do you want as far as power settings on ur external?

-kt
I wanted the settings to stay and they did, my drive just didn't show up all the time.

---

### Post by kernel tom on 2008-02-14
do u mean "show up" as in not mounted, or as in no icon on the desktop?

-kt

---

