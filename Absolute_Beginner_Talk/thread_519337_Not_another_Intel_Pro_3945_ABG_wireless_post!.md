---
title: "Not another Intel Pro 3945 ABG wireless post?!"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by Anjruu on 2007-08-06
Yes, it is. I have tried to read the other posts, but I can't understand most of what is going on.

I am running Edgy on a Vaio 9500 series laptop with the ipw 3945 driver installed and, since the problem did not go away when I tried using ndiswrapper, I think working, though of course I might be wrong. 

Under System>Administration>Networking, a "wireless connection" is found, with a check mark next to it. I have entered my Essid and marked for DHCP. However, when I open firefox, the server cannot be found. I am dual-booting with Windows XP, and I can access the internet using that. 

iwconfig gives:
[FONT="Times New Roman"]
lo                                      no wireless extensions

eth0                                 no wireless extensions
 
eth1                                 IEEE 802.11g                     ESSID:"*my essid*"
                                        mode: managed                  frequency: 2.437 GHz    Access Point 00:14:6c:92:9c:66
                                        bit rate: 54 mb/s                Tx-power 15 dBm
                                        retry limit: 15                     RTS thr:ff                         fragment thr: off
                                        power management: off
                                        link quality=95/100           signal level=-33 dBm        noise level=-44 dBm
                                        Rx invalid nwid:0              Rx invalid:1                       Rx invalid frag:0
                                        Tx excessive retries:0      Invalid misc:720               missed beacon:0

sit0                                  no wireless extensions[/FONT]


Is there any other information I should include? 

Thanks!

---

### Post by Inxsible on 2007-08-06
this might not be very helpful, but have you considered upgrading to Feisty?

My Intel 3945 ABG, worked out of the box in Feisty.

---

### Post by Anjruu on 2007-08-08
Hmmmm...Thanks, I'll give it a try. Now to figure out how to upgrade...

---

### Post by Anjruu on 2007-08-08
I feel really stupid, but I can't figure out how to upgrade to Feisty. I got a blank CD, downloaded the file from "Get Ubuntu" on the main site, burned it, and put it into my laptop. However, the CD does not automatically run, and the command found on the upgrading help website does not seem to work. I can open the CD, but it is read only, and I cannot find a file to run to get the upgrade started. What do I do? Did I do something wrong?

---

### Post by Inxsible on 2007-08-08
how did you burn the cd....as a data cd or iso image ?

burn speed should be 4x or less. also have you considered a fresh install instead of upgrading ?

if you are only upgrading, i dont think you need the CD, you can simply upgrade via synaptic or the terminal.

---

### Post by Anjruu on 2007-08-10
Ok, so I upgraded to Feisty, and its still not working. Under the network manager, however, there is now an option for eth1, which has never occurred before, but it claims it is not configured properly. Any ideas what the next step is?

---

