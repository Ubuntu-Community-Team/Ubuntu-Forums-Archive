---
title: "No sound Asus N53jq-xv1"
date: 2011-08-27
forum: Asus Ubuntu Support (CLOSED)
---

### Post by thedave360 on 2011-08-27
I just installed 11.04 on my Asus n53jq. Everything works great except I cannot get sound out of my internal speakers. I have read most of the other posts about asus sound problems on this forum and others. I've done everything in all the posts I can find and nothing works. The headphones work fine, but I haven't tried the HDMI out. I can't find any solution that works. I'm beating my head against a wall. Any ideas??

---

### Post by jecelyin on 2011-08-31
My laptop is N53JQ, sound problems I have solved:
echo "

hda-verb /dev/snd/hwC0D0 0x1b SET_PIN_WIDGET_CONTROL 96
hda-verb /dev/snd/hwC0D0 0x1b SET_AMP 0xb000
"
>> /etc/rc.local

Hope to solve this problem 11.10.

Another problem is the notebook fan speed is very slow, Windows7 will work very well, who can help me :-(

---

