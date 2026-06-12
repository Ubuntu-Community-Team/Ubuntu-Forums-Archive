---
title: "Ubuntu 10.10 Powerbook 15&quot; 1.67Ghz"
date: 2011-03-20
forum: Apple Hardware Users
---

### Post by bd1308 on 2011-03-20
Installed Ubuntu 10.10 on my new-to-me Powerbook 1.67Ghz.

First, let me say that PowerPC, as a platform, is most definately *not* dead.

Installation went normal. I installed with network connected to Ethernet rather than Wireless.

Installed Wireless firmware. Then I had wireless.

Backlighting didnt work until i added 'i2c-dev' to /etc/modules. Restart, and backlight works, although its a little too sensitive.

Hardware acceleraton wasnt enabled, so i had to add this to a file called Radeon-kms.conf in /etc/modprobe.d/

"radeon options modeset=0"

Reboot. Then I had hardware acceleration and Compiz.

Install/run sensors and sensors-detect. Run as root. Detected HD temp, CPU, GPU temps and fan speed. 

Make sure this is in /etc/modules: therm_adt746x. Thats the thermal control stuffs. 

I then installed openjdk and netbeans and eclipse. OpenJDK is slow, but I feel that is due to OpenJDK itself, and not PowerPC.

This gave me a working CPU ondemand throttling:
apt-get install cpufrequtils


Installing this gave me a working battery-applet that reported a percentage:

sudo add-apt-repository ppa:iaz/battery-status && sudo apt-get update
sudo apt-get install battery-status
/usr/lib/battery-status/battery-status --indicator


I get really good battery life, and everything that shipped on this laptop actually works as designed. 


Forever PowerPC, Forever Ubuntu

---

### Post by bd1308 on 2011-03-20
I might add that ive been using Ubuntu/PPC since 6.06 on a ibook, a 12inch Powerbook G4 1.33 and now this machine, and i run several servers and workstations on Ubuntu (and CentOS for my customers)

---

