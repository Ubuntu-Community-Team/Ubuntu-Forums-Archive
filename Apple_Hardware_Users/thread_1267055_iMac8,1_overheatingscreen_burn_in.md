---
title: "iMac8,1 overheating/screen burn in"
date: 2009-09-15
forum: Apple Hardware Users
---

### Post by skaplan77 on 2009-09-15
Hello,

I have an IMac8,1 (24"), and after using it for several hours, it experiences "screen burn-in".  That is, the images of windows and icons remain visible even when they are closed or moved.

I notice that the back-side of the top-left of the computer becomes very hot which may be related.  After turning off the computer for several hours (or letting it idle via "lock screen"), the problem goes away.

Has anyone else experienced this problem?  Suggestions welcome!

Thanks,

Sam

---

### Post by skaplan77 on 2009-09-15
I ran the 'sensors' program.  Do these temperatures and fan-speeds look sensible, or could they be the problem, causing the burn-in?  Thanks!

Output of 'sensors':
```

applesmc-isa-0300
Adapter: ISA adapter
ODD :        698 RPM  (min =  700 RPM)
HDD :       1199 RPM  (min = 1200 RPM)
CPU :       1200 RPM  (min = 1200 RPM)
temp1:       +24.2°C                                    
temp2:       +41.0°C                                    
temp3:       +41.8°C                                    
temp4:       +45.0°C                                    
temp5:       +55.8°C                                    
temp6:       +49.5°C                                    
temp7:       +50.0°C                                    
temp8:       +55.2°C                                    
temp9:       +51.5°C                                    
temp10:      +46.8°C                                    
temp11:      +68.5°C                                    
temp12:      +47.0°C                                    
temp13:      +63.5°C      

```

---

### Post by skaplan77 on 2009-09-16
I ran the sensors program again, this time after letting the computer idel ("lock screen") for the evening.  Right after unlocking the screen, I ran the 'sensors' program, giving the following output.  On some sensors there is a difference of 20 degrees C.  Is this too much?  Thanks!

```

applesmc-isa-0300
Adapter: ISA adapter
ODD :        700 RPM  (min =  700 RPM)
HDD :       1199 RPM  (min = 1200 RPM)
CPU :       1199 RPM  (min = 1200 RPM)
temp1:       +20.8°C                                    
temp2:       +31.5°C                                    
temp3:       +32.5°C                                    
temp4:       +34.0°C                                    
temp5:       +44.0°C                                    
temp6:       +37.8°C                                    
temp7:       +36.0°C                                    
temp8:       +44.2°C                                    
temp9:       +28.2°C                                    
temp10:      +32.2°C                                    
temp11:      +62.5°C                                    
temp12:      +33.8°C                                    
temp13:      +41.8°C

```

---

### Post by nazar2k2 on 2009-09-16
Great Post , Thanks a lot , it is very much elaborated and all can easily follow up this tips
Thank you for your posting

---

### Post by skaplan77 on 2009-09-17
> **nazar2k2 said:**
> Great Post , Thanks a lot , it is very much elaborated and all can easily follow up this tips
Thank you for your posting

Hi nazar2k2.  Thanks for your post.  Are you experiencing screen burn-in on an imac?

Thanks,

Sam

EDIT:  It would be also useful to know if others that are using the imac8,1 with Ubuntu are having _no_ problems with screen burn-in.  If so, please post.  Thanks!

---

### Post by vitoreiji on 2009-09-18
Hi skaplan77,
I have this problem with an iMac too. I'm not sure if it is 8,1, I'll check it tomorrow (or next week, not sure if I can get there at the weekend) and come back to you. All I can say is that I do feel it getting hot, but I never saw the video problems, although someone once told me they turned it off because they saw it had "video problems" and it was hot.
I left it on, and logging remotely and running sensors I get this:
```

applesmc-isa-0300
Adapter: ISA adapter
ODD :        998 RPM  (min = 1000 RPM)
HDD :       1199 RPM  (min = 1200 RPM)
CPU :       1200 RPM  (min = 1200 RPM)
temp1:       +25.5°C                                    
temp2:       +44.0°C                                    
temp3:       +42.8°C                                    
temp4:       +44.0°C                                    
temp5:       +72.2°C                                    
temp6:       +63.2°C                                    
temp7:       +62.0°C                                    
temp8:       +49.5°C                                    
temp9:       +36.0°C                                    
temp10:      +36.0°C                                    
temp11:      +41.5°C                                    
temp12:      +46.8°C                                    
temp13:      +64.5°C

```I guess I'll poweroff before it melts...
Anyway, do you have some other solution?
I found this thread, that looks promising, but didn't read it through yet.
[http://ubuntuforums.org/showthread.php?p=7600145](http://ubuntuforums.org/showthread.php?p=7600145)

I'll come back to you with more details and tell if I found a solution.

---

### Post by skaplan77 on 2009-09-19
Hi,

I don't have a solution yet.  But, I did the following (I'll report back whe I find out if this helps or harms the situation) *** EDIT: THE FOLLOWING PROCEDURE DOES NOT WORK ***: 

1) install applesmc-dkms from the mactel ppa ([https://launchpad.net/~mactel-support/+archive/ppa](https://launchpad.net/~mactel-support/+archive/ppa)).  

2) Reboot. 

3) Run
```
 
sudo sensors-detect

```

4) Reboot

5) Run 'sensors':
```

Adapter: ISA adapter
Core 0:      +37.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +37.0°C  (high = +100.0°C, crit = +100.0°C)  

```

Vitoreiji: Thanks-so-much for the link. I checked it and scrolled back a few post where there was a link ([http://ubuntuforums.org/showthread.php?t=1102465](http://ubuntuforums.org/showthread.php?t=1102465)) to a "fan-control script".

I have not yet tried the 'fan-control script'.  I will try the recipe that I've described in this post first.

If anyone sees that I'm doing something stupid, please let me know!  Thanks!

---

### Post by skaplan77 on 2009-09-20
The procedure that I tried (written down in the previous post) did not work.

Using the script from [http://ubuntuforums.org/showthread.php?t=1102465](http://ubuntuforums.org/showthread.php?t=1102465) allowed me to sets the fan speed, and is keeping the computer much cooler which is great, but...

The "screen burn-in" problem persists even when the computer remains cool.  I found the link ([http://discussions.apple.com/thread.jspa?threadID=1446926&tstart=1](http://discussions.apple.com/thread.jspa?threadID=1446926&tstart=1)) on a mac forum which suggests that the screen burn-in is a common problem and also says that the burn-in is not permanent.  In my experience shutting down the computer over-night removes the burn-in the next morning, and it returns by mid-way through the work-day).

---

### Post by vitoreiji on 2009-09-22
Thanks skaplan77, I'll try the script.

And yes, I'm on iMac8,1.

---

