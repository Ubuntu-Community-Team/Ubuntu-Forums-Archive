---
title: "Ubuntu on iMac"
date: 2008-06-12
forum: Apple Hardware Users
---

### Post by Madman68 on 2008-06-12
Ok, I have an annoying problem here. I am trying to get Ubuntu to work on an old iMac G3. I have spent some time looking and reading and have already reset the HorizSync and VertRefresh in the  xorg.conf file. Now, I am able to get the login screen and I enter my user name and password and then the desktop background loads up and nothing comes up on the desktop. Also, the applications bar at the top of the screen doesn't show up either. Am I missing something?
Thanks for the help in advance!

---

### Post by stream303 on 2008-06-13
Sounds to me like the date-bug which stops gnome soon after the gdm login.  Have you checked:

[https://help.ubuntu.com/community/UbuntuDateBug](https://help.ubuntu.com/community/UbuntuDateBug)

Which version of Ubuntu are you running?

You may want to disable glx and/or dri too, and maybe some other ati-rage or ati-radeon specific tweaks found:
[https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8](https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8)
and
[https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec](https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec)

The G3 iMac ranks are growing, that's for sure!

---

### Post by Madman68 on 2008-06-13
Thanks for the heads up, I had heard about the date bug but had never encountered it before. I reset the date according to the instruction from the link you provided and then restarted the gdm,it didn't seem to get me all the way so I restarted and then disabled dri and then restated again and now everything seems to be running good, I can now login and get to the desktop, no more "brown screen of death". Thanks a lot for the help!

--This guide helped a lot [http://ubuntuforums.org/showthread.php?t=405934]("http://ubuntuforums.org/showthread.php?t=405934")

---

