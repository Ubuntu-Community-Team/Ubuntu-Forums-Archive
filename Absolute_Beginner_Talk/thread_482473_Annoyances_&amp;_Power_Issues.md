---
title: "Annoyances &amp; Power Issues"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by linuxnovice on 2007-06-23
Hi,
Its been a week since I installed Kubuntu into the laptop I got from EBay...and I am enjoying every minute of it. I am seeing myself working on this laptop old it might be than my windows xp laptop. With samba I dont need to worry about accessing my stuff on the other laptop.

That said, I have certain things that I would like to get fixed:

1) Neither suspend nor hibernate seems to work. When I select either one of them, the laptop screen goes blank (as it should I suppose) but after then when I try to log back, the system crashes. KDM doesnt show up and nothing really happens. So I am forced to power off my laptop and start all over again. 

2) I would also like to be pointed to the place where I could set my preferences w.r.t. what happenes when my laptop lid is closed or if the power button is pressed.

3) The battery on this laptop is not that great so it doesnt give me much time out of AC. One time when my mother (to whom I was trying to show how great Kubuntu is) the system swtiched off. Apparently, the battery drained out. The thing is there was no warning message that power is less or something like that. I was wondering if this is an isolated issue or that kubuntu doesnt give that warning at all.

4) Sometimes when I start Adept, it doesnt start at all. It just says loading and then disappears. Then I have to start it again and everything is alright. I noticed a lot this happens after I have used other update programs like apt-get or using install a deb package using kubuntu package manager. Maybe they are related?

These are some of the major ones. If I come accross anything that I cant solve, I know where to come :)

Thanks.

---

### Post by phr0ze on 2007-06-23
> **linuxnovice said:**
> Hi,
Its been a week since I installed Kubuntu into the laptop I got from EBay...and I am enjoying every minute of it. I am seeing myself working on this laptop old it might be than my windows xp laptop. With samba I dont need to worry about accessing my stuff on the other laptop.

That said, I have certain things that I would like to get fixed:

1) Neither suspend nor hibernate seems to work. When I select either one of them, the laptop screen goes blank (as it should I suppose) but after then when I try to log back, the system crashes. KDM doesnt show up and nothing really happens. So I am forced to power off my laptop and start all over again. 

2) I would also like to be pointed to the place where I could set my preferences w.r.t. what happenes when my laptop lid is closed or if the power button is pressed.

3) The battery on this laptop is not that great so it doesnt give me much time out of AC. One time when my mother (to whom I was trying to show how great Kubuntu is) the system swtiched off. Apparently, the battery drained out. The thing is there was no warning message that power is less or something like that. I was wondering if this is an isolated issue or that kubuntu doesnt give that warning at all.

4) Sometimes when I start Adept, it doesnt start at all. It just says loading and then disappears. Then I have to start it again and everything is alright. I noticed a lot this happens after I have used other update programs like apt-get or using install a deb package using kubuntu package manager. Maybe they are related?

These are some of the major ones. If I come accross anything that I cant solve, I know where to come :)

Thanks.

1. dont have an answer. Lots of people have trouble with this even in windows. Keep working at it.

2. System ]> preferences -> power management

3. Probably cause the battery is so old, it doesn't even trip the warning. I get the warning on my laptop

4. I dont know.

---

### Post by mikesignguy on 2007-06-23
1. acpi is used to save battery in laptops .... i have had the same problem, my laptop would even overheat... updated to version 7.10 and may of my problems disappeared

---

### Post by mikesignguy on 2007-06-23
correction  version 7.04

4. You should consider using aptitude... it is faster and handles dependencies better
the problem with the gui is it has to do so much to give you a pretty picture of what is on the system as well as what is available to install on your system.  Not a bad thing for a beginner but a drag if u want instant gratification.


pychocats site explains it

see link below

---

### Post by linuxnovice on 2007-06-24
You may be true in that but many a times  I have been stumped because I dont exactly know the code to enter for apitude. In adept, as you say it does give a pretty picture. I guess I consider myself an experienced beginner... :)

---

