---
title: "setting up internet connection"
date: 2006-02-02
forum: Absolute Beginner Talk
---

### Post by Sbarton on 2006-02-02
Hi all! I have now installed a Router/Ethernet connection to my Dual boot PC. It is up and running in windows but I need help to setup in Ubuntu, Is there anyone patient enough to walk me through the setup? Oh! one other thing as well Firefox does'nt load up for some reason. The little white circle appears with dots moving inside (searching I imagine) but nothing actually loads. I realise this is 2 items I can make a separate post if necessary.
Many thanks

---

### Post by davmac on 2006-02-02
I'll be happy to try to help. When you start up Ubuntu do you see the network icon on the taskbar? Probably with a small yellow exclamation mark, to show that it is not working?

If you double click this (and type in your password) you'll get the network settings dialog. You can also access this from the "Systems" menu, but I can't remember the exact sequence (and I'm on a Windows box at work at the moment).

Click on your connection (probably eth0) and then choose properties. From this point in it depends on your setup. If you boot up windows and check the network properties you should be able to find all of the information you need. If this gets an IP address automatically assigned then it is easier but if not, make a note of the IP address, subnetmask, gateway address and DNS addresses.

Back to the network properties in Ubuntu and you should be able to spot the relevant fields to key this information into (but shout up if not). If luck is with you, everything will be working now. If not let us know what is happening and what messages, if any, you're getting.

Hope this helps,

Dave Mac

---

### Post by Sbarton on 2006-02-02
Hi! davmak, Glad you have to know you may have the answer. Sorry to say this but patience is required as I have to switch PC's at the moment. I do not have the exlamation mark so I am going to switch and find some details. AS ARNIE says 'I will be back' Thanks for your reply

---

### Post by br4inwash3r on 2006-02-15
oh yes, me too no find any exclamation mark. btw, does this method also work for the live cd version? okay then, me check first...rebooting now....i'll be back if sumthin's wrong. thx

---

### Post by br4inwash3r on 2006-02-15
aah, it's turns out to be very easy. i just set the eth0 and eth1 to DHCP and it automagically detects my connection. ow btw, setting the IP, gateway bla, bla stuff didn't work.....

but thx again!! and so this is officially my second post to any web forum using linux and ubuntu for that matter...

---

