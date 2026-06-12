---
title: "Bluetooth Problems"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by RapMasterC on 2008-01-03
I tried to install my bluetooth adaptor.  It was showing up earlier when I would plug it in but I could not connect to my phone, so I installed gnome-obex-server and tried to get blueman installed, now the bluetooth icon doesnt show up at all, when I try to install  bluez-utils I get the following error:
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  bluez-utils: Depends: libc6 (>= 2.7-1) but 2.6.1-1ubuntu10 is to be installed
E: Broken packages

Also when I try to install Blueman through synaptic I keep getting the following errors:
blueman:
 Depends: bluez-utils but it is not going to be installed

if I try to install bluez-utils I get this error:
bluez-utils:
  Depends: libc6 (>=2.7-1) but 2.6.1-1ubuntu10 is to be installed

its like some sort of vicious circle.  

Any help would be appreciated.

---

### Post by RapMasterC on 2008-01-07
never mind got it working.  Ubuntu is working excellently now, just gotta get my front headphone port working.

---

### Post by john6six on 2008-01-20
I am having the same issue. Would you mind telling me how you got this working?

Thanks

---

### Post by Kebabman on 2008-04-03
Hi, I am also having this problem. It would be handy if you could post how you got this working!

---

### Post by Desmo UK on 2008-04-13
Same problem here, help would be appreciated.

I'm stuck on installing libc6 as it say I need 2.7 and only have 2.6 installed but it's the latest apparently.

---

### Post by itsme_n8 on 2008-04-14
So... anything?  I'm having the same problem.

Nate

---

### Post by Desmo UK on 2008-04-14
All I've done so far is download an old version of Blueman (0.1.9) as this doesn't need the latest versions of the other files. Not sure what I'm missing out on though.

---

