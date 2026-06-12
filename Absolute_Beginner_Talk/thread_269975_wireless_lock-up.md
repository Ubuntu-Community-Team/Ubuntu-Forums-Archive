---
title: "wireless lock-up"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by Graham Gardner on 2006-10-02
I've just installed 6.06.1 and am using a Belkin FD7000v3 wireless card.  If I go to 'Networking' and then try to configure and/or activating the ra0 connection then the computer locks completley requiring me to power down to re-boot.  iwconfig shows that there is a RT25000 wireless ESSID:"". I have tried inputting the ESSID with static and DHCP configurations but as soon as I hit activate everything stops.  Any ideas anyone?

---

### Post by theratster on 2006-10-02
I had a very similar problem using a USB wireless dongle, where you select and click "activate" and the system freezes. So try this.

When you are in ubuntu, goto the terminal and use this:

> 
sudo iwconfig ra0 essid <yourIDhere>
sudo iwconfig ra0 key <yourkeyhere>
sudo dhclient ra0


If it connects fine (check by using firefox or whatever), then to make this permanent, type in "sudo gedit /etc/init.d/bootmisc.sh"

Then at the bottom before the exit 0, type in:

> iwconfig ra0 essid <yourIDhere>
iwconfig ra0 key <yourkeyhere>
dhclient ra0.

And it should work! (It did for me!)

---

### Post by blx_286 on 2006-10-02
> **Graham Gardner said:**
> I've just installed 6.06.1 and am using a Belkin FD7000v3 wireless card.  If I go to 'Networking' and then try to configure and/or activating the ra0 connection then the computer locks completley requiring me to power down to re-boot.  iwconfig shows that there is a RT25000 wireless ESSID:"". I have tried inputting the ESSID with static and DHCP configurations but as soon as I hit activate everything stops.  Any ideas anyone?

I had the same problem on my AirLink card, which uses the RT61 drivers. This [thread]("http://ubuntuforums.org/showthread.php?t=132980") got me going. But you cannot use the networking GUI.

---

