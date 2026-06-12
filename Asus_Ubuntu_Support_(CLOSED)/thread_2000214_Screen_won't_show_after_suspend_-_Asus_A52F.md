---
title: "Screen won't show after suspend - Asus A52F"
date: 2012-06-09
forum: Asus Ubuntu Support (CLOSED)
---

### Post by joetait on 2012-06-09
Hi

I often suspend my laptop by shutting the lid, and it has an intermittent problem with restarting. It does restart (I will qualify what I mean by this in a second) but it won't show anything on the screen. When I say it restarts, my guess is that it is fully functioning, since I can see a cursor and move it, which changes according to what it is over, and I have also managed to shut down by guessing where to click. 

I can access tty1-6 fine, so if anyone knows a work around whereby I can go to one of these and restart X or something that would be grand.

I haven't been able to spot any sort of pattern as to when it happens with regards to power supply, programs running etc. It doesn't seem to happen if I suspend from the menu, but I haven't tried this enough to confirm whether it is the case for sure.

Any help would be much appreciated :)

edit: I am running 12.04

---

### Post by FirstByté on 2012-06-09
I share in the same issue.

**Case Scenario**
Whenever, the lid is closed (my laptop is set to DO NOTHING on Lid Close) my system get a 'white-screen-panic'-- It starts with blackout and gracefully moves through to all-white screen in a span of 10secs or thereabout.
**Scenario End**

In Ubuntu 11.04 & 11.10, I solved the issue using the suspend script on [this page]("https://help.ubuntu.com/community/Asus_U36SD"), but now, that don't work anymore.

It's personally saddening, I use my laptop for presentation everyday (cause I lecture) and use it almost 24 hours. It's painful to know that I HAVE to shutdown every now and then to avoid the 'white-screen-panic'. It's awful!

**Attempts/Discoveries**
[LIST]
[*]While using Unity 2D, this issue is taken care of (suggesting, it's got something to do with OpenGL or Compiz etc.) I tried Gnome Shell, the WSP showed up still.
[*]I also discovered that if I left the lid closed for a bit longer time, it might in many cases work when I open the lid (This, I guess has worked 40% of the times :'( )
[*]This issue also persists when Ubuntu tries to switch screens between projector and system screen. Interestingly, plugging the projector (VGA) cable back works on the projector but not on the system's display.
[/LIST]

My system's info
```

ikon@P34CE2:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04 LTS
Release:	12.04
Codename:	precise

ikon@P34CE2:~$ uname -ar 
Linux P34CE2 3.2.0-24-generic #39-Ubuntu SMP Mon May 21 16:52:17 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```
[LIST]
[*]Graphics card: Optimus Nvidia Geforce GT540M CUDA
[*]Model No.: U41SV Asus
[/LIST]

If additional info is required, we'll be willing to give.

Thanks

---

### Post by Plaidman on 2012-06-19
I've been having the same problem with my AOD150. When it enters suspended mode while open, no problem works fine, but whenever the lid closes the screen won't reactivate except as a momentary blip when I move the cursor or type something.

---

### Post by bart de jong on 2012-06-26
I have the smane problem with this Ubuntu version 11.10 running on a ASUS K52F P6100

---

### Post by iris-n on 2012-06-26
I had a similar issue with an Asus 1225B; I solved it by removing fgrlx and using the radeon driver. Hope that helps.

---

### Post by punkybouy on 2012-06-26
I have a system 76 running 12.04 with an Intel Graphics 4000 chip that does the same thing.  Try using the shutdown menu and choose suspend instead of closing the lid.  I had some success with that.

---

