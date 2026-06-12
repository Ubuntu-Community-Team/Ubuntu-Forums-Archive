---
title: "daylight saving issues"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by ozPATT on 2006-12-02
hi all, 

well, daylight saving has finally hit western australia, and the time as come for me to adjust all my clocks... 

i tried changing the clock on my laptop last night, and it just comes up with the bug reporting tool. i thought maybe something hadnt loaded properly, so i left it to try again today. 

same thing though. bug reporting tool. does anyone know how i can change the time on my clock? im using edgy.

thanks

Patrick

---

### Post by codypumper on 2006-12-02
Are you right-clicking on the clock and selecting adjust time/date?

---

### Post by iball on 2006-12-02
I installed the tzdata package from Debian Unstable.  This has worked perfectly.

You can get it [Here]("http://ftp.wa.au.debian.org/debian/pool/main/t/tzdata/tzdata_2006p-1_all.deb")

There is probably a better way, but this works.

I am really looking forward to daylight saving - an extra hour of daylight won't go amiss.

I hope this helps
--Ian

---

### Post by 3rdalbum on 2006-12-02
I did it last night without troubles by right-clicking on the clock, but here's the command-line version:

```
sudo date MMddHHmm
```

(obviously, MM is the two digits of the month, dd is the two digits of the day, HH is the two digits of the hour etc)

---

### Post by iball on 2006-12-02
> **3rdalbum said:**
> I did it last night without troubles by right-clicking on the clock, but here's the command-line version:

```
sudo date MMddHHmm
```

(obviously, MM is the two digits of the month, dd is the two digits of the day, HH is the two digits of the hour etc)

If you use NTP to sync your clock, this won't work because NTP will keep setting the clock to the "correct" time for the +8 time zone.

Using the patch that I linked to above, Daylight Saving is automatically accounted for.  NTP still syncs your clock correctly, and the clock still shows the correct time for WDST.

--Ian

---

### Post by max.diems on 2006-12-03
> **iball said:**
> 
I am really looking forward to daylight saving - an extra hour of daylight won't go amiss.

DST doesn't give an extra hour of daylight, though:(

---

### Post by ozPATT on 2006-12-05
haha, too true, still the same amount of daylight. ahh well... in 3 years time they will hold another referendum, everyone will say no and we can go back to normal time... 

that is, unless they forget to hold the referendum...

got the clock sorted thanks, had to go through the system > admin though, as right clicking on the clock just brings up bug reporting. must be some error with my install or something.

---

### Post by iball on 2006-12-06
> **ozPATT said:**
> haha, too true, still the same amount of daylight. ahh well... in 3 years time they will hold another referendum, everyone will say no and we can go back to normal time... 

that is, unless they forget to hold the referendum...

got the clock sorted thanks, had to go through the system > admin though, as right clicking on the clock just brings up bug reporting. must be some error with my install or something.

Glad to see you got your clock sorted.

With any luck, people will enjoy daylight savings.  A 3 year trial should be long enough for the proletariat to get their collective heads around the idea of adjusting the clock.  I love it.

An old lady said to me the other day in Perth, that it is beyond here that people are making a fuss about adjusting something that doesn't exist.  Time is a man-made invention, and is completely arbitrary.  I think many people forget that the clock is not have a divine origin, so it is not heresy to adjust it.

--Ian

---

### Post by Josh1 on 2006-12-07
> **iball said:**
> I installed the tzdata package from Debian Unstable.  This has worked perfectly.

You can get it [Here]("http://ftp.wa.au.debian.org/debian/pool/main/t/tzdata/tzdata_2006p-1_all.deb")

There is probably a better way, but this works.

I am really looking forward to daylight saving - an extra hour of daylight won't go amiss.

I hope this helps
--Ian

Just get up an hour earlier then. :rolleyes:

---

### Post by iball on 2006-12-07
> **Josh1 said:**
> Just get up an hour earlier then. :rolleyes:

I take it you are against daylight savings then?  Why?
I don't see me getting up much earlier than 6am.

--Ian

---

