---
title: "Disappearing Network Settings"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by philferrar on 2008-02-20
I've built Ubuntu with Kubuntu 7.10 on my laptop and everything has gone well - after persevering with NDISWrapper I'm up and running with my Linksys WPC54G WiFi card o.k. The snag is every time I re-boot I lose some of the network configuration details and have to go back into "Network Settings" to re-configure - a total pain.

Basically two bits of information are dropped.

a) My 'Default Gateway' address on one of the tabs called "Route" re-sets the IP address to "0,0,0,0" and I need to re-enter "208.67.222.222" in order to get the connection back

b) Whilst doing the above, 9 times out of 10 another tab that holds my 'eth1' [Wifi] sign-on details [including ESSIS and WEP key] for my ADSL router also changes. It retains the ESSIS o.k. but it loses the WEP key value. Note this is actually a WPA-Personal ASCII key and I'm assuming it's just out of date labeling that appears on the form.

Can anyone let me know how to preserve this information across re-boots ?

Many thanks in anticipation.

Cheers

Phil

---

### Post by max renn on 2008-02-21
I had a similar prob with route.  Always wanted to default back to the eth0 route, not the eth1 route.  eth1 being my INET connection.  What I did was remove the eth0 so that eth1 became eth0 during install (eth0 likes to be the INET interface). You might try to force your eth0 to the same ip scheme as the wifi, then at least the route would be the same.  Else, can you turn off eth0 in the BIOS?  might be helpful to get wifi working.

No clue about lost wifi settings.

---

### Post by spiderbatdad on 2008-02-21
came across this today. talks about preserving network settings..maybe of some help to you.
[https://www.opendns.com/start/ubuntu.php](https://www.opendns.com/start/ubuntu.php)

---

### Post by philferrar on 2008-02-21
Thanks for the info Max. I have tried disabling eth0 but it didn't make any difference. Another thing I've noticed since my first post is that if a 'hibernate' the laptop the settings are preserved [as you'd expect] and all I need to do it go to Network Settings [where eth1 shows as enabled] disable eth1 [2 seconds] and then enable eth1 [about 3 or 4 seconds] which seems to work all the time. I've noticed other online comments hoping that the 8.04 release may address Wifi in a more robust manner so may just wait and see what happens - unless off course someone else comes along with a 'cure' just now. Cheers Phil

---

### Post by philferrar on 2008-02-21
Have just tried out suggestion made by spiderbatdad - unfortunately no change.

---

### Post by spiderbatdad on 2008-02-21
just looking at wpa-supplicant (in synaptic). I wonder if it would help.

---

