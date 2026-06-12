---
title: "Updating Ubuntu to latest version"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by Fingerz91 on 2007-01-07
Hey All!

I am new to ubuntu, and have edgy running on my PC at home. I was just wondering, will the update utility update the existing OS, or do I have to re-download the .iso and start fresh?

---

### Post by kebes on 2007-01-07
If you are running Ubuntu 6.10 (Edgy Eft) then you are running the most up-to-date stable version. The next version (Feisty) is currently in development and is not stable. Once it becomes stable you will be able to update to it in the usual official way (using update-manager), and you will not need to download a new .iso.

(Are you asking how to start using the unstable Feisty now...?)

---

### Post by jpeddicord on 2007-01-07
The update utility will update everything on your system, including the OS itself.

However, it will not provide an OS upgrade until April, when Feisty (the next version) comes out.

You are also able to not upgrade to the next OS version if you wish.

---

### Post by oyvindaa on 2007-01-07
One way is to update your /etc/apt/sources.list manually, then do a

```
sudo apt-get dist-upgrade
```

You can also download the ISO and burn it to a cd.

---

### Post by Jussi Kukkonen on 2007-01-07
You will be notified when the next version is available and you can upgrade. Opinions differ on which method is better (upgrade or reinstall), personally I prefer upgrading unless there has been much systems changes "by hand" (like installing non-ubuntu software)

EDIT: man, was I slow!

---

### Post by vf514 on 2007-01-07
A google search on the subject returned a promising article that may be of assistance:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Upgrading_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Upgrading_Ubuntu)

---

### Post by Fingerz91 on 2007-01-07
Thanks guys :)

I was just wondering, and you answered my question to the tee.

I switched to Ubuntu from windows about 2 days ago and I love it. Combinations of Automatix and Synaptic made finding the needed software painless. I installed firestarter and clamav (though i know I wont need them) and am able to use wine to run Quickbooks without a hassle. Ubuntu is a godsend in my opinion, and if you are willing to work at it, the profits outweigh the problems 10 fold (The only issue I had was with an ATI driver...)

---

### Post by Frank Golden on 2007-01-07
> **Fingerz91 said:**
> Thanks guys :)

I was just wondering, and you answered my question to the tee.

I switched to Ubuntu from windows about 2 days ago and I love it. Combinations of Automatix and Synaptic made finding the needed software painless. I installed firestarter and clamav (though i know I wont need them) and am able to use wine to run Quickbooks without a hassle. Ubuntu is a godsend in my opinion, and if you are willing to work at it, the profits outweigh the problems 10 fold (The only issue I had was with an ATI driver...)
Did you get past the ATi problem ok. If you are still not satisfied see this

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

The instructions to manual install worked perfectly for me with my X1400 Radeon Mobility.
(See sig for system spcs.) I get full 3-D and hardware acceleration.

---

### Post by Fingerz91 on 2007-01-08
> **Frank Golden said:**
> Did you get past the ATi problem ok. If you are still not satisfied see this

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

The instructions to manual install worked perfectly for me with my X1400 Radeon Mobility.
(See sig for system spcs.) I get full 3-D and hardware acceleration.

Yup. That was the guide I used and my ATI card works fine...

---

### Post by Frank Golden on 2007-01-09
> **Fingerz91 said:**
> Yup. That was the guide I used and my ATI card works fine...
I couldn't agree with you more about sticking with Ubuntu. I stated my journey about 2 years ago with Breezy Badger. Back then I was an extreme noob. I am still learning today
but am much more fluent in Linux today. I am up to Dapper on one HDD for my machine.
(see sig. for specs) and I have Edgy installed on an external drive for testing purposes.
Will probably update to Feisty when it is released in April. It was rough at first but got better as I learned more.

---

