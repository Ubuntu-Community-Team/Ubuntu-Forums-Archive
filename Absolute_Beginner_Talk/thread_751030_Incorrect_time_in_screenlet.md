---
title: "Incorrect time in screenlet"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by sayakb on 2008-04-10
I have 2 screenlets: Clock and KClock. I like clock better but it shows about (minus) 5 hrs 45 mins deviation from the time. I can set the hour hand to have a 5 hour deviation but not the minutes. So theres always a +/- 45 mins deviation. Why is it giving wrong time indication when my system clock is showing the time correctly?

---

### Post by christianxxx on 2008-04-10
Have you set the correct timezone for the screenlet? I had a similar problem, but when I set the timezone (CET for mine) it showed the correct time. No need to set time deviation for me.

Seems a little peculiar with a 45 min deviation, but I know some timezones are not full hours, though I always believed these to be half hour ones...

---

### Post by ichbinesderelch on 2008-04-10
did you set the correct timezone during installation/in the rc file?(or whereever it is declared in ubuntu ;) )

---

### Post by sayakb on 2008-04-10
> **ichbinesderelch said:**
> did you set the correct timezone during installation/in the rc file?(or whereever it is declared in ubuntu ;) )
 
During Ubuntu installation? Yes, I did! :)
 I do have a timezone option in the screenlet properties, but what exactly should I enter. My timezone is ASIA/CALCUTTA.

---

### Post by iblazev on 2008-04-25
I have a similar problem. During install I set local for time zone (since I have dual boot) but for some reason it looks like that the timezone is set as if it is in UTC. When I changed timezone to Zagreb/Croatia where I am, I get 2 hours offset (one hour extra cause the daylight savings). Problem is that I cannot set that as my main timezone. I checked in rcS and UTC there is set to **no**. Changing it to yes didn't make any difference. I still have 2 hours offset. 
Now, what to do to setup time so it can show BIOS time as my local (zagreb/cro) and not as the UTC time to which it adds +2 hr?

---

### Post by revant.one on 2008-04-26
set your timezone to "localtime" (without the quotes)

---

### Post by ZMorgan on 2008-05-05
localtime worked for me too, thanks!

---

