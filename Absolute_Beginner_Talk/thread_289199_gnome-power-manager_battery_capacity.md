---
title: "gnome-power-manager: battery capacity?"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by neocookie on 2006-10-30
Hi guys

So, I´ve made the move to edgy, and I´ve been looking at the new features in  gnome-power-manager.

One of the things I´ve noticed is that in further information, it says my battery capacity is ¨78% (Fair)¨. I noticed it has gone up from ¨69% (Poor)¨ since leaving it on AC power for a few nights.

Can anyone tell me exactly what this means, and how to improve it?

---

### Post by neocookie on 2006-10-31
No help with this?

---

### Post by miobio on 2006-10-31
I have the same problem on an IBM z60... it must be a bug!

Which laptop is yours?

---

### Post by neocookie on 2006-10-31
I have an Advent 7096. At this point, my capacity is 75% (Fair)... down from the other day.

I'm going to attempt to drain the batter completely, then leave it on charge for a day or two, see whether that helps.

---

### Post by pwaller on 2006-11-06
So, neocookies, did it help?

---

### Post by teaker1s on 2006-11-11
I'm interested to as mine is brand new laptop and the battery says it's 15 hours to charge then 15 minutes.
trying battery charge monitor also to see if that works better](*,) has to bug in program

---

### Post by neocookie on 2006-11-12
> **pwaller said:**
> So, neocookies, did it help?
Nope, not really. It moves between 75 and 78%, but stays in that range. Doesn't seem as though there's anything I can do. :(

---

### Post by santo on 2006-11-27
My laptop (Dell Inspiron 9300) is hardly one year old now and I'm noticing very poor battery capacities (appr 1h30 when fully charged).

Therefore I decided to take a look at the "Power Information" tool of Ubuntu and it's telling me my battery capacity is only "57% (Poor)". Remaining Time: 1 hour, 24 minutes
(see screenshot)
And the battery was fully charged according to Gnome Power Manager.

Does this mean my battery is dying already ?

---

### Post by teaker1s on 2006-11-27
bug in software=incorrect results don't worry about it

---

### Post by Spif on 2006-11-27
I remember reading somewhere that the estimated values concerning battery life, charge time, etc. have been improved a lot. We will likely see the changes in Feisty.

Please note that I'm not entirely sure if this is correct. Can't find a source that backs this up either.

---

### Post by mcduck on 2006-11-27
Actually a typical lifetime for laptop battery is about 2 years, so 57% capacity is fairly normal for a year-old battery.

The capacity is just estimated value, so it changes a bit, but it's normal that it decreases over time and some day you'll just have to buy a new battery. Batteries do not last forever.

---

### Post by sloggerkhan on 2006-11-27
I agree that capacity is most likely a measure of actual charge as compared to theoretical actual possible charge when the thing was new.

That said, on my computer, the battery life got MUCH better in edgy eft. I also enabled user controllable throttling in the configuration so my gnome cpu applet lets me have pretty tight control over frequency scaling now.

On my comp, the power information charts don't seem to use the correct symbols all the time. It seems to display the "resume" colored line instead of the "on battery" colored one.

---

### Post by santo on 2006-11-28
@teaker1s:
"bug in software."
Might this mean that Edgy thinks my battery is almost empty and display a warning message, while it actually isn't empty at all ?

@sloggerkhan:
"the battery life got MUCH better in edgy eft"
It's since I switched to edgy that I'm noticing low battery capacity, and apparently I'm not the only one :-k (search for battery life or something)

---

### Post by sloggerkhan on 2006-11-28
I agree that there is some sort of flaw in the power management,I am only saying that under edgy, my laptop lasts a lot longer on battery than it did with dapper. It does display incorrect information in some locations, though.

---

### Post by shutterbc on 2007-01-28
I hope you don't mind I'm reviving this thread.  I noticed that my battery life on a new Dell D620 was far less than 3 hours when I first tested it out (in both Ubuntu and Windows).  Gnome power information told me that it was at 80% of capacity, then about a week later 74%, and then a few days ago 67%.  I called Dell and asked if I could get a replacement battery.

Now with this new battery I'm noticing a similar pattern, I think.  **What I'm wondering is: does this info come from the battery unit itself**?

$ cat /proc/acpi/battery/BAT0/info 
present:                 yes
design capacity:         5100 mAh
last full capacity:      4404 mAh
battery technology:      rechargeable
design voltage:          11100 mV
design capacity warning: 510 mAh
design capacity low:     154 mAh
capacity granularity 1:  51 mAh
capacity granularity 2:  51 mAh
model number:            DELL JD6067
serial number:           1262
battery type:            LION
OEM info:                Panasonic

Currently Gnome is telling me that the capacity is 86% (fair).  I think it's calculating this off the design capacity vs. last full capacity.  By the way this is after one charge cycle... though I may have actually missed a full charge by a few minutes.

---

### Post by Blaster95 on 2007-01-28
I don't have a problem on my lap top. The battery seems fine.

---

### Post by idlewild on 2007-02-05
> **shutterbc said:**
> Now with this new battery I'm noticing a similar pattern, I think.  **What I'm wondering is: does this info come from the battery unit itself**?

Indeed it does, modern batteries have a chip inside them that holds all this information and I believe it is the laptop's bios that updates it. If the value is jumping around a bit it is probably the laptop's fault not gpm.

---

### Post by shutterbc on 2007-02-05
Thanks to all who replied; after going through a couple of recharge cycles I'm sure the old battery was just plain defective.  My new battery is much more sensible:

$ cat /proc/acpi/battery/BAT0/info
present:                 yes
design capacity:         5100 mAh
last full capacity:      4992 mAh

Hooray for (almost) 3 hours of battery use.

---

### Post by gganitis on 2008-02-02
In my two weeks new laptop, the g-nome power manager says that the capacity is poor in percentage from 48% to 56%!

What does it mean? Should I call the hp waranty???

Thank you

---

### Post by gganitis on 2008-02-02
first time the battery capacity is 60% (too high!).

Is there any reason to worry? Have a look in the attachment please.

---

