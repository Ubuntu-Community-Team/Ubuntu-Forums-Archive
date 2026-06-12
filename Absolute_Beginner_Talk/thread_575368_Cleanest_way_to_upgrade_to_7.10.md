---
title: "Cleanest way to upgrade to 7.10"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by Shlomir on 2007-10-13
Hi Ubuntu-heads,

Being quite in-experienced with this fun OS, I'm curious to know the cleanest way to Upgrade my 7.04 distro to 7.10..Here are my pressing questions:

1. Can you do a straight upgrade over the Net via command line? I am on a 512K connection, how many Meg is the online upgrade and how long would it take?

2. I run Ubuntu Studio, will 7.10 upgrade break it?

3. How do I preserve all my current settings and programs installed?

4. Can I build a boot DVD from work for 7.10, and basically do a 'clean' upgrade over the top of 7.04 and preserve my files and settings?

Thanks

---

### Post by arrrghhh on 2007-10-14
> **Shlomir said:**
> Hi Ubuntu-heads,

Being quite in-experienced with this fun OS, I'm curious to know the cleanest way to Upgrade my 7.04 distro to 7.10..Here are my pressing questions:

1. Can you do a straight upgrade over the Net via command line? I am on a 512K connection, how many Meg is the online upgrade and how long would it take?

2. I run Ubuntu Studio, will 7.10 upgrade break it?

3. How do I preserve all my current settings and programs installed?

4. Can I build a boot DVD from work for 7.10, and basically do a 'clean' upgrade over the top of 7.04 and preserve my files and settings?

Thanks

1. I used "sudo update-manager -c -d" which launched a gui... i'm sure there is a CLI method.
it was ~500 megs I want to say?  so i have 5mbit down and it took ~35min to download (it hovered around 470kbps).
2. I have no idea
3. It preserved everything perfectly!  I did 3 feisty->gusty (all xubuntu) upgrades today and they were all painless and smooth.  all my settings were preserved, programs, cron tasks, files, even my apache web server, torrentflux, mysql, php5, everything is working perfectly as it was before.  and the bulletproof-X is pretty nifty!
4. Certainly, just download an ISO and burn it!

---

### Post by vishzilla on 2007-10-14
Firstly check this page out [https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

to Q.1 you can upgrade to 7.10 via the update manager/CLI, be sure to complete all your feisty updates before this.

If you talk about a clean upgrade, its better if you back up all ur personal files and do a clean install (format and install).

---

### Post by shae on 2007-10-14
Before you upgrade, you need to consider any non-ubuntu repositories you added or if you used Automatrix.  If you did either of those, you might need to reinstall rather than upgrade depending on what you installed.  Otherwise you might experience some problems.  Also make sure you still have the ubuntu-desktop meta-package installed.

---

### Post by Shlomir on 2007-10-15
I tried to upgrade according to that link, and it missed all these packages from the Aussie mirror. Now it asks to upgrade, but requests a partial upgrade, which kicks off, and then just bombs out..then it asks to install over 7809meg of packages...

I think I'll wait until Thursday and download and image and build it off that locally, doing  a nearly 1gig upgrade over a 512K connection isn't a good idea!

---

### Post by jazz1 on 2007-10-15
> **arrrghhh said:**
> 1. I used "sudo update-manager -c -d" which launched a gui... i'm sure there is a CLI method.
it was ~500 megs I want to say?  so i have 5mbit down and it took ~35min to download (it hovered around 470kbps).
2. I have no idea
3. It preserved everything perfectly!  I did 3 feisty->gusty (all xubuntu) upgrades today and they were all painless and smooth.  all my settings were preserved, programs, cron tasks, files, even my apache web server, torrentflux, mysql, php5, everything is working perfectly as it was before.  and the bulletproof-X is pretty nifty!
4. Certainly, just download an ISO and burn it!

I did this also. Everything was preserved. Initially I saw no speed difference, but after a few hours things seem to get bogged down. How can I burp this thing? Am I in for a clean install?

---

### Post by JOWIROMA on 2007-10-17
I just have a question, I did an upgrade on one of the old versions of ubuntu and my computer got all bugged... what I am going to try now is a clean install but I have /home in a different partition, I know that if I do not format this partition nothing is going to happen to it but Do you guys think that I am going to have any problems after installing 7.10? (like not being able to access the home partition)

I think the better way to upgrade is to do a fresh install, I had problems in the past... and 
this is the reason why I put /home in a different partition so I could try a new install without losing 
any of my stuff and I'll  be sure that I won't have a bugged OS upgrade...

---

### Post by kooldino on 2007-10-19
Try: sudo apt-get install update-manager

once that's installed, run update-manager

---

