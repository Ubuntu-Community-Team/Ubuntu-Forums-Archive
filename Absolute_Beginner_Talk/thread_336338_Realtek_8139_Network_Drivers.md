---
title: "Realtek 8139 Network Drivers"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by darkcyber on 2007-01-11
Ok, I'm trying to access the internet after my installation of ubuntu.  I've enter my static lan ip address under the network settings and still can't access the internet, nor can I ping my router.  How can I tell if ubuntu actually installed a driver for my onboard Realtek 8139 nic?

Also, if it didn't, where can I find a linux driver for this?  Been looking with not success.

Thanks!

---

### Post by chippy99 on 2007-01-11
The 8139 is a really common nic and ubuntu should have no problem finding it. Try typing 
*sudo lsmod* and you should see 8139cp and / or 8139too modules listed. 
If not listed try typing *sudo modprobe 8139cp*. Also what do you see if you type *sudo ifconfig*, there should be some info on eth0 displayed.

Hope this helps

---

### Post by darkcyber on 2007-01-12
Finally got it fixed.

Here's what I did I disconnected my 2 ide hd's and only had my SATA hd connected. I then installed the 32 bit version of ubuntu. This time when I installed it the little ubuntu splash screen was in color. When I used the 64 bit version it was always black and white. Also, when I finished the installation and it exited off the desktop it went back to that splash screen which was in color again and it opened the cd tray and said to remove the cd and press enter. This time when I pressed enter the computer did reboot.

So, I don't know if it was the 64 bit version or the ide hd's. I did try the 32 bit version with the 2 ide hd's connected and it didn't work. So, could have been a combination.

All my network stuff was detected and all I did was click on FireFox and it accessed the net right off...very sweet.

---

