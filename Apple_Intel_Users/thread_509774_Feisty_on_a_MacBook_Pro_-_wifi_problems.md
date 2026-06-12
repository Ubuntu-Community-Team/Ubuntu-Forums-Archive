---
title: "Feisty on a MacBook Pro - wifi problems"
date: 2007-07-25
forum: Apple Intel Users
---

### Post by ramoutar on 2007-07-25
I have a MacBook Pro, but the wifi isn't working.

When I go to Network Manager, there is no wireless option.

When I run "iwlist scan" I get the following results:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

There is no mention of ath0.

I'm confused and don't know what do to, any help would be appreciated!

Thanks.

---

### Post by metallicamaster3 on 2007-07-25
try looking in the restricted drivers menu. Maybe one is needed.

System > Administration > Restricted Drivers

---

### Post by cyberdork33 on 2007-07-25
If that method does not work, you will have to look here:
[http://ubuntuforums.org/showthread.php?t=485579](http://ubuntuforums.org/showthread.php?t=485579)

---

### Post by ramoutar on 2007-07-27
Hey again,

I checked the Restricted Drivers, and the only thing that shows up is my ATI card.

I followed the directions that you linked to for installing the mad wifi drivers, and everything installed okay (I didn't receive any error messages) but there is still no wireless option in Network Manager and when:

iwlist scan

It still doesn't say anything about ath0.  And when I do "iwlist scan ath0", I'm told that ath0 doesn't support scanning.

Is this something I might have goofed up during the initial install?  Does it matter that I had ethernet plugged in when I was installing Ubuntu?

Help...

Thank you again.

---

### Post by cyberdork33 on 2007-07-27
Yours sounds like the same as other people are having. Look in that thread I linked for help. 

If you can 'iwconfig' and you have an entry for ath0 then you hardware is recognized, but for some reason network-manager is not seeing it. Did you reboot?

---

### Post by russo.mic on 2007-07-30
Have you installed NDISWrapper or madwifi?  

There are no native drivers in linux for that adapter,  sorry to ask a dumb question, but you never mention what method of installation of which driver your using.

If your running 32 bit, NDISwrapper or madwifi will work.  if your 64-bit, run madwifi.  
Just for your reference, iwlist doesn't report that there is no adapter, just that it can't support scanning.  since you havene't installed a driver yet, ath0 doesn't exist.  i.e., you could type iwlist scan ath0 or iwlist scan dickfore and it would say the same thing.

Russo

---

### Post by ronocdh on 2007-07-30
Although I roundly encourage you to try the MadWifi guide Cyberdork provided the link for, I'll drop a link to an ndiswrapper guide which you could use as a fallback. [See here]("http://www.thinkwiki.org/wiki/How_to_install_ndiswrapper_for_the_ThinkPad_11a/b/g/n_Wireless_LAN_Mini_Express_Adapter").

---

### Post by cyberdork33 on 2007-07-30
Just curious, why does ndiswrapper not work for 64-bit? are there no 64-bit windows drivers?

---

### Post by ronocdh on 2007-07-30
> **cyberdork33 said:**
> Just curious, why does ndiswrapper not work for 64-bit? are there no 64-bit windows drivers?
This is my understanding of it, yes. The long reign of 32-bit Windows XP probably led to this disaster.

---

### Post by ramoutar on 2007-07-31
Hey,

Okay so I tried the tips in the linked MadWifi article and the post that Benanzo had written.  Neither worked.

I also tried the ndiswrapper that ronocdh linked to.  That seems to have worked and I am now happily using wifi on my macbook pro!

Thanks for all the help, much appreciated.

:D

---

