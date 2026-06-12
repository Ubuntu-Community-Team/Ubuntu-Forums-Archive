---
title: "[SOLVED] weird question.. lock my computer!!"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by vnkatesh on 2007-08-29
hi all,

i'm a self-obsessed ubuntu addict. i simply can't turn my PC off!..

This is more of a general linux question..

now, since my exams are nearby, i need ur help..  i want some shell-script stuff that does this functionality :- during startup, checks if the date is > sep 6th 2007, and then continue booting.. else shuts down automatically... and there should be no possible way of me bypassing it :)

i did think abt it, and got some idea abt creating a new script it /etc/init.id/ and linking it with /etc/rc2.d/ which checks the present date.. and continues only if the date is > sep 6 2007... 

Please do help me!!

---

### Post by christhemonkey on 2007-08-29
Im not sure this is possible, to have it so that there is no possible way of you bypassing it. How about i take your computer off your hands for a bit?! Haha!

Or just get someone else to look after your power supply or something?

---

### Post by goodbyewindows on 2007-08-29
send yourself your power supply in the mail and set it to deliver it on the 6th

---

### Post by viciouslime on 2007-08-29
I think you mean self-confessed, no? :p

---

### Post by insane_alien on 2007-08-29
yeah, mail yourself your powersupply, failing that, get a friend to hide it for a couple of weeks.

---

### Post by mysticmatrix on 2007-08-29
> **vnkatesh said:**
> hi all,

i'm a self-obsessed ubuntu addict. i simply can't turn my PC off!..

This is more of a general linux question..

now, since my exams are nearby, i need ur help..  i want some shell-script stuff that does this functionality :- during startup, checks if the date is > sep 6th 2007, and then continue booting.. else shuts down automatically... and there should be no possible way of me bypassing it :)

i did think abt it, and got some idea abt creating a new script it /etc/init.id/ and linking it with /etc/rc2.d/ which checks the present date.. and continues only if the date is > sep 6 2007... 

Please do help me!!

If you happen to be in a college hostel, just inform your professors. They would be more than happy to confiscated your PC and lock it up permanantly :lolflag:
(It would be atleat in my college IIT :) )

---

### Post by vnkatesh on 2007-08-29
SOLVED!!...

i did this..

created a shell script..
```

#!/bin/sh
set `date`
if [ $3 >=6 -a "$2" = "Sep" ]
then
{
        banner "Hello there"
}
else
{
        banner "NO....."
        /etc/init.d/rc 0
}
fi

```
and then linked a new file named S65check_date to this... hence, upon entering the startup runlevel, it checks the date, and month, and shuts down automatically..

:)

@alltheguys
don't think the power-supply method shall work with me :)

@mysticmatrix
which IIT are u in?? me in IIT Roorkee..

---

