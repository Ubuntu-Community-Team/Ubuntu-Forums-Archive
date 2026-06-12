---
title: "firestarter &amp; networking tip for newbies (no reply needed) like me..."
date: 2005-11-22
forum: Absolute Beginner Talk
---

### Post by towsonu2003 on 2005-11-22
Hi,

I usually use dial up (ppp0). Today, I was struggling to connect via wireless networking (wlan0) using ndiswrapper module and I just couldn't. Very frustrating as sudo ifconfig and sudo iwconfig showed I was connected but no ping, no firefox, no epiphany!.. I was about to quit trying, thinking it was about a kernel upgrade I did a month ago, or the Bastille setup, when it HIT me: firestarter! :rolleyes: 

For those who use firestarter, just a hint: after connecting on wlan0, launch firestarter and change its interface from ppp0 (or whatever you had previously) to wlan0 (or whatever you will have then)... To do that: Applications > System Tools > Firestarter > Preferences > Network Settings > (Internet Connected Devices) Detected Devices > change the setting from old interface (ppp0 in my case) to new interface (wlan0 in my case)... 

I did not wanna put this in howtos, as this is basically me being newbie and very stupid... Wouldn't be a brilliant howto :)

Thanks.

---

### Post by Kapre on 2005-11-22
[QUOTE=towsonu2003]Hi,

I usually use dial up (ppp0). Today, I was struggling to connect via wireless networking (wlan0) using ndiswrapper module and I just couldn't. Very frustrating as sudo ifconfig and sudo iwconfig showed I was connected but no ping, no firefox, no epiphany!.. I was about to quit trying, thinking it was about a kernel upgrade I did a month ago, when it HIT me: firestarter! :rolleyes: 

For those who use firestarter, just a hint: after connecting on wlan0, launch firestarter and change its interface from ppp0 (or whatever you had previously) to wlan0 (or whatever you will have then)... To do that: Applications > System Tools > Firestarter > Preferences > Network Settings > (Internet Connected Devices) Detected Devices > change the setting from old interface (ppp0 in my case) to new interface (wlan0 in my case)... 

I did not wanna put this in howtos, as this is basically me being newbie and very stupid... Wouldn't be a brilliant howto :)

Thanks.[/QUOTE]


towns - thanks for the info. I'm sure this will be a good info for us beginers.

K

---

### Post by Griff on 2005-11-22
Heh.  That would have probably gotten me stuck.  Thanks for the tip.  When it comes to things like this, it is best the info is shared than lost.  Even if it does seem trivial.:)

---

