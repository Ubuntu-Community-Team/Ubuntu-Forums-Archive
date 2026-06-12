---
title: "Cannot set clock"
date: 2006-09-17
forum: Apple PPC Users
---

### Post by Dreyco on 2006-09-17
So a lot of things are crashing because my date is set at:
December 31st 1903

So after extensive Googling I tried to find how to change the time in terminal and came across this:

sudo /sbin/hwclock --set --date "08/04/2000 08:33:25"

But it says "RTC cannot be found by any known means"

So is there another way to set my clock on my G3 imac seeing as all my GUI crashes because of the date?

---

### Post by ristosu on 2006-09-18
Try:

```
sudo modprobe rtc
```

or:

```
sudo modprobe genrtc
```

before running hwclock.

---

### Post by linear on 2006-09-18
Have you tried "sudo date"?

You also need to replace your PRAM battery.

---

### Post by Dreyco on 2006-09-18
So heres what happens now.

sudo modprobe rtc
FATAL: Module RTC not found

Then I try:

sudo modprobe genrtc
sudo: Timestamp too far in the future: December 31 23:03:09 1903 

I also try this afterward.

sudo /sbin/hwclock --set --date "09/18/2006 09:33:25"
sudo: Timestamp too far in the future: December 31 23:03:09 1903

I also try:

sudo date
sudo: Timestamp too far in the future: December 31 23:03:09 1903



So what is this "PRAM Battery" that I need to replace?

EDIT: bought a new battery off ebay should be in this week...

---

### Post by Dreyco on 2006-09-19
Bump! Anyone know about the "Timestamp" issue?

---

### Post by linear on 2006-09-19
Try "sudo date" with a date/time string, to see if you can set the clock, for example:

**sudo date "Tue Sep 19 22:06:21 GMT 2006"**

---

### Post by Dreyco on 2006-09-20
I still get the "Timestamp too far in the Future: Dec 31st 1903"

I'll try again once I have those batteries (tomorrow perhaps)

---

### Post by linear on 2006-09-20
Some new info. Look at [this thread]("http://www.ubuntuforums.org/showthread.php?t=173505"), as apparently it's more than the clock.

---

