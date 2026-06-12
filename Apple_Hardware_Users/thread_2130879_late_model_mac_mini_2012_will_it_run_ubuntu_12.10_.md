---
title: "late model mac mini 2012 will it run ubuntu 12.10 as only operating system?  HOW?"
date: 2013-03-30
forum: Apple Hardware Users
---

### Post by craymore on 2013-03-30
late model mac mini 2012 will it run ubuntu 12.10 as only operating system?  HOW?

if not do i just resize mac os x install refit then use a external dvd drive to install ?  i assume the hard drive is GPT and am unsure how to partition for GFT so it works with EFI. 

thank you

---

### Post by Vinodh Moodley on 2013-04-01
You can install it using the Mac specific version without using refit.  Boot from a Mountain Lion USB installer and use Disk Utility to format to fat32. Then boot from the Mac specific version of Ubuntu, I used the newest 13.04. You won't need refit. Install Ubuntu as per normal.

---

### Post by JonasNorway on 2013-05-04
> **Vinodh Moodley said:**
> You can install it using the Mac specific version without using refit.  Boot from a Mountain Lion USB installer and use Disk Utility to format to fat32. Then boot from the Mac specific version of Ubuntu, I used the newest 13.04. You won't need refit. Install Ubuntu as per normal.
But how did you get the network interface to work? I'm struggling with it, get "No network interfaces detected" message during installation. see more on [http://askubuntu.com/q/290658/4692](http://askubuntu.com/q/290658/4692)

---

