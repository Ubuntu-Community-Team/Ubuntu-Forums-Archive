---
title: "Extra Repositories in Pangolin"
date: 2012-08-03
forum: Apple Hardware Users
---

### Post by fblud on 2012-08-03
Hi,

I want to know how to add extra repositories in Pangolin, please.  My Airport card won't work.  I need the firmware and **bcm43xx-fwcutter** isn't in the apt-get repository. I read [this]("http://ubuntuforums.org/showthread.php?t=1095177&highlight=wifi+powerpc") thread and found a solution if I can add extra repositories.

I have a PowerPC G4 iBook 1.25.

Thanks in Advance

fb

---

### Post by 2blue on 2012-08-03
I have lubuntu 12.04 on much the same computer as you, iBook G4 1.42GHz. To get wireless working there are two restricted packages in package manager, I installed both of them, accepted all copyright stuff and after a reboot wireless was activated. Give the system a few seconds or even a minute after bootup to detect wireless, after that it will instaly be there at every bootup. However, apt-get should work too, you just have to get the correct name of the packages I suppose.  After the enormeous update everything was working except sound, I had to fuzz a bit to make alsamixer appear. It`s quick and easy to do this if you have a wired access to a network.

---

### Post by fblud on 2012-08-03
Thanks,

Do you know what the restricted packages are called.

---

### Post by 2blue on 2012-08-03
I did a simple search for *restricted* in synaptic package manager and found them on the list of packages. In lubuntu they are called, *lubuntu-restricted-extras* and *lubuntu-restricted-addons*. I think you only need to change *lubuntu* for your version of ubuntu (ubuntu, kubuntu, xubuntu, whatever it is called).

---

### Post by rsavage on 2012-08-03
[https://wiki.ubuntu.com/PowerPCFAQ#Will_my_wireless_work.3F](https://wiki.ubuntu.com/PowerPCFAQ#Will_my_wireless_work.3F)

---

### Post by fblud on 2012-08-03
Thanks rsavage,

Worked!

New to Ubuntu/Linux.  I didn't know this existed.  Bookmarked!


fb



> **rsavage said:**
> [https://wiki.ubuntu.com/PowerPCFAQ#Will_my_wireless_work.3F](https://wiki.ubuntu.com/PowerPCFAQ#Will_my_wireless_work.3F)

---

