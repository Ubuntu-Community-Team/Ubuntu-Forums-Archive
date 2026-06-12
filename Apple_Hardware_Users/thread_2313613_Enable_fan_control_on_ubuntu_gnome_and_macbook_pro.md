---
title: "Enable fan control on ubuntu gnome and macbook pro"
date: 2016-02-14
forum: Apple Hardware Users
---

### Post by nakadai2 on 2016-02-14
I come here after spending 3 good hours trying to make fan control work on a macbook pro and ubuntu gnome.  Some time before, I installed ubuntu unity on this same computer and fan control began immediately after installing macfanctld, nothing more.  I then wanted to have a full gnome experience, and installed ubuntu gnome 15.10 instead.  Now, no matter what daemon I install fan control do not want to activate. 

I tried macfanctld, mbpfan and even fancontrol which is not really supposed to work for macbook pro's. I went through the process of downloading applesmc dkms package which is not maintained anymore. It's PPA is not working with Wily and I had to install it by hand.  So I wonder what I missed, why fan control worked just after installing one package in ubuntu unity, and why with ubuntu gnome it wont activate at all ? 

If someone is able to help me on this situation, I would be really grateful.

Macfanctld reads in fact only the minimum speed for the fans : I change this value, macfanctld actually changes the fans rotation. BUT I managed to have it behave correctly (i.e: control fans speed depending on sensors reads) under ubuntu unity, so something must be missing in my configuration.

I'm now running ubuntu 16.04. I'd hope that it would fix the issue (new kernel etc...) but it is still the same scenario.

SOLVED: I forgot to install HDDTEMP package, and voila :-)

---

