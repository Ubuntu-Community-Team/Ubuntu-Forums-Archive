---
title: "Rescuing Ubuntu"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by awthomp on 2008-01-01
I run both Windows Vista and Ubuntu on my computer (each has its own dedicated harddrive).  A few weeks ago, Ubuntu was running great (with Compiz and all of the nice apps that everyone loves so much!).  Anyways, I turned off my computer to move it to a different city and kept it off for around two weeks.  When I booted up my machine yesterday, Ubuntu was hosed!  Some problems I saw:

-Menu bar had disappeared
-Desktop background had disappeared
-Kiba dock had also disappeared
-Gnome-do and Yakuake did not start

I thought Gnome just had a problem loading so rebooted.  Then I saw:

-Menu bar was there
-Still no desktop wallpaper
-Yakuake started

I tried enabling compiz, but nothing happened.

I rebooted again and noticed the same problems as seen in the first instance.

My gut tells me that somehow my graphics driver somehow got corrupted.  I don't think there's a hardware failure because Vista seems to be working just fine (for Vista, of course).

I tried unmounting the drive and running fsck to correct any problems, but this did nothing to help.  I'd appreciate a suggestion.  I really don't want to reinstall Ubuntu!

---

### Post by bcrom on 2008-01-01
Wow, that's a lot of strange symptoms.  If you think it's a problem with your graphics driver try booting to command line and running 

```
sudo dpkg-reconfigure xserver-xorg

```
and see if that fixes anything.

---

