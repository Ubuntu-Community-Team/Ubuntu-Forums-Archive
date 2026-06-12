---
title: "Trouble getting Airport Extreme Card working (Ubuntu Edgy)"
date: 2007-02-25
forum: Apple PPC Users
---

### Post by kingkool68 on 2007-02-25
Today I installed Ubuntu on to my 12" 867mhz PowerBook G4 and for the life of me I can't get wireless to work.  I've followed several how-to guides including this -> [http://www.ubuntuforums.org/showthread.php?t=142727](http://www.ubuntuforums.org/showthread.php?t=142727) and this -> [http://pinguin.uni-psych.gwdg.de/~ihrke/wiki/index.php/Installing_Ubuntu_on_iBook](http://pinguin.uni-psych.gwdg.de/~ihrke/wiki/index.php/Installing_Ubuntu_on_iBook)

Using Wifi Radar I can see my router however whenever I try to obtain an IP it always fails.  I even took off the WEP encryption and it still couldn't get an IP address.  Are there any other tricks to getting this working?

---

### Post by tgalati4 on 2007-02-26
Dapper 6.06.1 Live CD worked fine out-of-the-box on a 15" G4 1Ghz.  There were some wireless network architure changes in Edgy that may be throwing the hardware detection off.

Dapper works pretty well.  I personally used Tiger 10.4.8 and XDarwin with Gnome apps that run in it's own 4-panel Windowmaker.  This is on top of an 8-window 3D switcher using Desktop manager.  This allows me to remotely logged into several Ubuntu servers and remote display gtk apps such as audacity.  I am still trying to get the sound server to work remotely.  But the speed and display quality is impressive.

---

### Post by gnomeza on 2007-02-26
> Using Wifi Radar I can see my router however whenever I try to obtain an IP it always fails.

I had the same trouble with the stock Edgy kernel. As a workaround I used a static ip configuration. This helped -  I could get a net connection - but not much
Every few minutes the drivers would lose *(ahem, sorry, I mean loose)* their association with the access point and I'd have to manually
```
sudo iwconfig eth0 essid MY_ROUTER
```
to get it back.
Manually setting the rate
```
sudo iwconfig eth0 rate 54M
```
also seemed to help get the association back.

Eventually though I got frustrated and have now moved to 2.6.20 from kernel.org until Ubuntu catches up. It's a huge improvement - I'm typing this from my hotel lobby wireless (whilst on my skiing holiday - there's dedication for you!)

If you aren't comfortable setting up a custom kernel then just wait it out. Shouldn't be long.

In the meantime there's also a *looong* [thread](http://forums.gentoo.org/viewtopic-t-409194.html) worth searching on the Gentoo forums detailing various issues with the bcm43xx drivers...

---

