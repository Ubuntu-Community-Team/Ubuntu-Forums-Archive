---
title: "Memory leak?"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by schraff on 2008-01-19
Greetings:
   My Gutsy Gibbon chokes generally within a minute of logging on. I think this has something to do with my video driver that may be creating some sort of memory leak. I have my machine set up as a dual boot with Windows XP Home as the other option. My specs are:
HP Pavilion
AMD Sempron processor
3000+
1.81 GHz, 384 MB Ram

The video card is integrated on to the motherboard. I think the driver is a Silicon Integrated Systems SIS760. I've gone to the SIS website and found what I think is a linux driver but I don't know how to install it. Newbie blues!

Thanx!
Schraff

---

### Post by ryanVickers on 2008-01-19
you should boot into recovery mode, and logon (as root).

You will then be left with a terminal instead of the graphical interface - this is waht you want.  Run the driver file you downloaded by going 
```

cd <path to driver, ex. /home/schraff/Desktop>

```and then top run it, go
```
./<driver filename, and extension, ex. driver.bin>
```could it also be tracker starting up?  ~45 seconds after logon it runs to index everything, and that could be overloading it.
To turn it off, go System > Preferences > Indexing Preferences and turn it off (basically, just turn OFF all checkmarks you find ;))

---

### Post by Hallvor on 2008-01-19
In my opinion you have too little RAM. That is probably why everything feels slow, especially with desktop effects enabled. There is just no way I would run regular Ubuntu with anything less than 512 mb of RAM.

---

### Post by ryanVickers on 2008-01-19
Very true - It is also very likely that if your using desktop effects without proper drivers it will just lock up from overload.  Integrated graphics can also pose a problem in any OS...

---

### Post by schraff on 2008-01-20
Thanks to both of you! Actually, I had forgotten that I only had 384MB so I think the first thing I'll do is slap some more memory in. Then I'll try figuring out about the drivers. Can I run the code from any virtual terminal (ctl-alt-F1, for example) or should I only run it from the recovery mode? I'm just figuring out some of this command line stuff and am not quite sure how to log in as root.
:redface:

---

### Post by philinux on 2008-01-20
Ubuntu runs fine on my old croc. No desktop effects though. Make sure they are turned off.

Also try suspending trackerd if its running. System>Admin>system monitor. Processes tab, highlight trackered right click and choose the options to stop the process. Or system>prefs>indexing options and turn it off see if that makes a difference.

---

### Post by ryanVickers on 2008-01-23
That's what I said first thing... :p

---

