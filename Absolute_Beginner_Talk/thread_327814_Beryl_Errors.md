---
title: "Beryl Errors"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by Blue_Sky on 2006-12-29
Hi,
Every time I try to install Beryl, I get the following message after I type "beryl-manager" into the terminal.

XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present

** (process:9185): WARNING **: get_setting_is_integrated not found in backend ini

** (process:9185): WARNING **: get_setting_is_read_only not found in backend ini

** (process:9185): WARNING **: get_setting_is_integrated not found in backend ini

** (process:9185): WARNING **: get_setting_is_read_only not found in backend ini
Initiating splash
Reloading all options.

I've tried the whole process of installing Beryl using four different Howto's, and this is the closest I've gotten to Beryl working. I used [http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851) this time. I know this is probably not the best place for this, but people in these forums have been the most helpful in the past. So, what have I done wrong this time?

Blue

---

### Post by kd7swh on 2006-12-29
It sounds like you don't have xgl or aixgl installed. I used the Beryl Wiki HowTo: 
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu)

make sure you follow the directions for your make of graphics card.

---

### Post by Blue_Sky on 2006-12-30
Ok, I've tried another two Howto's and that latest one has got Beryl working. What does the following error message mean?

XGL Present

** (process:8677): WARNING **: get_setting_is_integrated not found in backend ini

** (process:8677): WARNING **: get_setting_is_read_only not found in backend ini

** (process:8677): WARNING **: get_setting_is_integrated not found in backend ini

** (process:8677): WARNING **: get_setting_is_read_only not found in backend ini
Initiating splash
Reloading all options.

Regardless of how I install or configure the nvidia driver and Xgl, I still keep getting that message.

---

