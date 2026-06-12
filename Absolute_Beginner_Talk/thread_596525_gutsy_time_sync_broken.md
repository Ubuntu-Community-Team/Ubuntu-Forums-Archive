---
title: "gutsy time sync broken"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by biomedtech on 2007-10-29
Since upgrading to Gutsy a couple of days ago, my clock no longer updates automatically. 
When I select configuration to 'keep time synchronized with Internet Time Servers', the 'Synchronize Now' button is shadowed.  I can change the listing of locations, but the button stays shadowed.  Manual time setting works,

---

### Post by llamakc on 2007-10-29
sudo apt-get install ntp

---

### Post by biomedtech on 2007-10-29
Thank you , but that didn't work. Here's what happened. 

administrator@PD:~$ sudo apt-get install ntp
[sudo] password for administrator:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntp is already the newest version.
The following packages were automatically installed and are no longer required:
  libswfdec0.3 libflac++5c2 liboggflac3 libjack0.100.0-0 libpostproc0d
  libavformat0d libgoffice-0-3 libavcodec0d libquicktime0 libntfs-3g0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
administrator@PD:~$ 

I did the autoremove.. The Synchroize Now button is still shadowed. 

Time sync is still broken  :(

---

### Post by llamakc on 2007-10-29
Sorry, I had hoped that helped as your symptoms were the same I had, which was fixed by installing ntp. Is "ntpdate" also installed?

---

### Post by markharding557 on 2007-10-29
try setting it in the ajust time and date tab on the clock just right click on it here you can select ntp servers and time zone

---

### Post by biomedtech on 2007-10-29
In Manual, the Sychronize Now button is not shadowed. It doesn't do anything when selected, but it can be 'clicked'. 

In the other option (to let the internet keep the time), it is shadowed irregardless of how many time servers are checked. 

Feisty didn't have this problem.

---

### Post by kitchenguy on 2008-01-06
Same problem here - it was fine in Fawn, broken in Gibbon.  Tried apt-get etc, and downloaded a new ISO and reinstalled (first time I ever reinstalled linux...)

Any ideas anyone?



PS - if anyone can think of a way to rename this system to "Funky Gibbon" I'd be eternally grateful (as would most other Goodies fans I guess)

---

### Post by kitchenguy on 2008-01-06
I think I solved it...don't know why it worked, but this did:

1.  Change preferences to "Use UTC  Time"
2.  Change your time zone to London (which is close enough to Greewhich to be GMT or UTC as our friends in the states like to call it - do they really hate england that much still)
3.  Change back to your local time zone
4.  Get rid of "Use UTC"

Mine is now spot on.

Still needs fixing - one point to Microsoft I guess.

---

### Post by Difranco1911 on 2008-02-18
This helped me...  Mine was 4 hours off for some reason so I checked the box "USE UTC" and now it's dead on.  TZ is America/Los Angeles, NTP Servers syncing with are in WA State and Nevada.

---

### Post by epeeist01 on 2008-04-05
When I follow these steps it does indeed fix my time being off, but my "synchronize now" button never becomes active.  When is the "synchronize now" button broken?  Someone mentioned something with dual booting Windows (which I do) but I couldn't find that thread in the forum.

---

### Post by epeeist01 on 2008-04-05
> **epeeist01 said:**
> When I follow these steps it does indeed fix my time being off, but my "synchronize now" button never becomes active.  When is the "synchronize now" button broken?  Someone mentioned something with dual booting Windows (which I do) but I couldn't find that thread in the forum.

I see now.  I couldn't find threads that blame dual-booting, but I did find the answer.  The button is _supposed_ to be grayed out when you are in auto-sync mode.  You cannot force it to contact a server through this interface when it is in auto-sync mode.  It is poor interface design in that when you are selecting a server to sync to and there is a button telling it to "sync now" you expect to be able to use it.  But it is only for use when you are in manual mode.  This does not explain why you have to futz with the time zones to get it to work while dual-booting, but I am sure that info is in the forums somewhere

---

