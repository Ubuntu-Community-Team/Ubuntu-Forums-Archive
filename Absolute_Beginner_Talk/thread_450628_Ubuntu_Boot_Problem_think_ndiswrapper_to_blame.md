---
title: "Ubuntu Boot Problem think ndiswrapper to blame"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by haw730 on 2007-05-21
Ok here is what my problem is. I got everything installed with ndiswrapper and had a problem booting so I booted to the GNOME Failsafe config. After that I was able to get internet and everything working just fine. I installed updates and everything. Then when I tried to reboot into normal mode I am coming across an error. I end up with: starting avahi mDNS/DNS-SD Daemon:avahi-daemon . it says that the process timed out. so then I go in under safe mode and look at the problems that ndiswrapper is having a problem with . I get this error 161.394116 setting essid failed set-essid:59. I dont know why everything isnt working when I was able to boot fine yesterday. Any help would be appreciated. Thanks

---

### Post by Ferrat on 2007-05-22
Don't really know of a solution but you are correct in assuming that it is ndiswrapper that hauntung you, feist doesn't really like ndiswrapper I think, especially if it was installed first on Edgy, then you update.

Try changing the Essid or setting a new one (name of your network) in the network settings

---

### Post by haw730 on 2007-05-22
I realized that the problem i think comes from me changing the display to 1440x900 i think it has a problem with the GNOME display which is why booting into anything except the kernel safemode doesnt work. I am going to try and reformat the drive and work around the problem. I figured out the networking issues as well and it seems fine. But again I think that my problem is the changing of the display options.

---

### Post by beow on 2007-06-14
> **haw730 said:**
>  I figured out the networking issues as well and it seems fine.

How did you fix the problem with "setting essid failed" ? Have that also and have not found a solution.

/Bengt

---

