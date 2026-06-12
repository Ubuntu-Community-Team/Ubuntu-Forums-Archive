---
title: "gpsdrive issues"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by allnew on 2007-07-15
I just installed Ubuntu and also installed GPSDrive. GPSDrive is not seeing my gps unit, I can see the data coming in on com1 at 4800 baud in a terminal program, I have set the preferences to /dev/ttsy0 at 4800 baud but GPSDrive only runs in simulation mode. Any help would be greatly appreciated

---

### Post by Pragmatist on 2007-07-15
What gps device do you have?  Did you look through the resources at the gpsdrive websites?:
The wiki: [http://www.livingresource.net/gpsdrive/index.php/Main_Page](http://www.livingresource.net/gpsdrive/index.php/Main_Page)
Archives: [http://s2.selwerd.nl/~dirk-jan/gpsdrive/]("http://s2.selwerd.nl/%7Edirk-jan/gpsdrive/")

---

### Post by allnew on 2007-07-15
I have a Garmin GPS17, it is progrqammed for NMEA at 4800 baud, I have tried quite a few place including the ones you listed but cannot find anything that has helped. I will go through them again. I saw something about a configuration file gpsdrivec that may be wrong but I cabn't seem to find it either.

---

### Post by Pragmatist on 2007-07-15
Is gpsd running?  Type this to find out:
```
ps -ef |grep gpsd
```

---

### Post by allnew on 2007-07-15
I typed it in and got this reply: 24941 24899 0 11:37 grep pts/0

I also just installed wine and ran seaclear and it5 immediately picked up the gps and gave me coordinates

---

### Post by Pragmatist on 2007-07-15
> **allnew said:**
> I typed it in and got this reply: 24941 24899 0 11:37 grep pts/0

I also just installed wine and ran seaclear and it5 immediately picked up the gps and gave me coordinates

Does this mean you have solved your problem and this thread is closed?

---

### Post by allnew on 2007-07-15
I would really prefer to use GPSDrive if I can find a way to make it work

---

### Post by haylocki on 2007-12-19
Hi,

> I saw something about a configuration file gpsdrivec that may be wrong but I can't seem to find it either.

First load a terminal :

Applications > Accessories > terminal


Then type :

```
gedit ~/.gpsdrive/gpsdriverc
```

Cheers, Ian

---

