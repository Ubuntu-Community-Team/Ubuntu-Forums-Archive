---
title: "Installing on a MacBook Pro the last stable release"
date: 2007-05-22
forum: Apple Intel Users
---

### Post by ThufirHawat on 2007-05-22
Dear all,
forgive me if I ask something obvious, but I cannot figure it out.
I am a slightly old former OS designer, so I used to know a thing or two about OSes.
Here with Linux, even with Ubuntu, I am finding that there is too much irrelevant information blanketing everything, unfortunately...
But anyway, here is the deal. I have a MacBook Pro i.e 2.33 GHz Intel Core Duo, with 2 GB RAM, and Mac OS X 10.4.9 patched. No firmware update required.
Installed BootCamp beta 1.2 and ReFit 0.9.
Used BootCamp to re-partition and have now a 91 GB (24 GB free) MacOS X partition. 
Created a second 20.5 GB partition with Boot Camp, where I intend to install Ubuntu.
Tried to find a right installer. No way. Naming convention are so sloppy that I had to use an AMD64 iso image for this computer which is 64 bit, but not with an AMD processor...).
However, much as Ubuntu is very jazzy graphically, it screws up big time when trying to load a graphic susbsystem.
1st simple question: which installation CD should I use, knowing I do not want to install Windows? A link rather than a whole speech would be nice.
2nd simple question: if I am booting from a CD, why somebody suggests to make incomprehensible manipulations to get the graphic subsystem (X-Windows) working? Shouldn't a bloody installer work without further ado? 
If an old 2005 Knoppix CD can understand my H/W, why Ubuntu cannot?
Sorry, venting frustration...
Any suggestion on how I may install Ubuntu without contemplating suicide?
Thank you.

---

### Post by ronocdh on 2007-05-22
First issue: you want the i386 build, which is the common Intel one. This is because while your processor (a Core Duo, **not** a Core2 Duo, correct?), while having two cores, is only 32-bit.

Second issue: X failure is due to ATI not releasing open source drivers for their hardware. Write them a letter if you object. The integrated graphics chipsets by Intel in the regular MacBooks work flawlessly, and Nvidia cards are much friendlier to Linux systems (though not entirely without hangups). See the link in my sig about that.

Good luck. Please post back with any questions, and hopefully we'll get you in working order in no time!

*Edit: Freaking killer name, dude!*

---

### Post by wigglydiggly on 2007-05-22
You reported that you have the MacBook Pro Core Dual (Yonha) not the Core 2 Dual (Merom).  If that is true you will need to use the 32 bit version of ubuntu  (x86 desktop) not AMD64.

---

### Post by ThufirHawat on 2007-05-23
> **wigglydiggly said:**
> You reported that you have the MacBook Pro Core Dual (Yonha) not the Core 2 Dual (Merom).  If that is true you will need to use the 32 bit version of ubuntu  (x86 desktop) not AMD64.

Sorry, sloppy writing.
System Profiler tells me I have 2.33 GHz Intel Core 2 Duo.
It should therefore be indeed a AMD64 distro.
Tnx for the recommendations.
Will try to do as indicated.

Cheers,

Thufir the European Mentat

---

### Post by ThufirHawat on 2007-05-23
Success!:D

My heartfelt thanks to Ronocdh!
Following the instructions in his signature it was easy...
I will now delve into the murky waters of getting the right drivers for my home WPA2 WiFi network, but I am quite confident that, with your support, I shall overcome.

Thank you all!

*Thufir, still the European Mentat*

---

### Post by ronocdh on 2007-05-23
> **ThufirHawat said:**
> Success!:D

My heartfelt thanks to Ronocdh!
Following the instructions in his signature it was easy...
I will now delve into the murky waters of getting the right drivers for my home WPA2 WiFi network, but I am quite confident that, with your support, I shall overcome.

Thank you all!

*Thufir, still the European Mentat*
Congratulations. I'm still stuck with WEP on my campus wireless network (with MAC authorization), and at home I only use WPA, because WPA2 gave me trouble. Nonetheless, there are those who've gotten it working. On principle, I should recommend you try madwifi before ndiswrapper, just because it's an open source solution. ;) Good luck!

---

