---
title: "feisty fawn ad-hoc"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by blindmist on 2007-04-29
so i have searched for about 20 mins trying to find a how to on setting up an ad-hoc network using feisty fawn and havent found anything

What is the easiest way of setting one up and being able to connect to it?

---

### Post by NeoTaoistTechnoPagan on 2007-05-01
This is assuming your wireless card is configured and is at /dev/wlan0.

```
iwconfig wlan0 mode Ad-Hoc
iwconfig wlan0 essid "<whatever your ESSID is>"
iwconfig wlan0 channel <whatever channel you are using>
```

Check it with
```
iwconfig wlan0
```
Look for the "Mode" setting to make sure it's ad-hoc.

---

