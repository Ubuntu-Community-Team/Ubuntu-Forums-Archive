---
title: "ntpd not behaving"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by mohnkern on 2007-09-26
I'm having a heck of a time with ntpd right now.  I've got several boxes and one of them keeps giving me a "no association id's returned" error mesage when running ntpq -p.  Here's the contents of the /etc/ntp.conf file:


 restrict default ignore
restrict 127.0.0.1
restrict {IP address of my network}  mask 255.255.255.0 nomodify notrap
restrict { ip address of another network} mask 255.255.255.0 nomodify notrap

# Above sets a default deny policy, then opens all access to the 
# localhost so it can manage it's ntpd daemon, and finally allows
# only OHD hosts as time sources, appropriate for a broadcast client

broadcastclient
driftfile /var/lib/ntp/drift
disable auth
authenticate no

---

