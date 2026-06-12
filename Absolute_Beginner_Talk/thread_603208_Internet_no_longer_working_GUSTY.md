---
title: "Internet no longer working GUSTY"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by homerj742 on 2007-11-04
I had a few issues after the Gusty upgrade. 

1) Samba - still working on this

and all of a sudden, no more interent! I can ping my gateway, I can get to the internet via other PC's (and my Windows Partition). 

I had installed Firestarter yesterday to see if it would help my Samba issue. I had stopped the firewall to open up all ports. I then noticed that the internet had stopped all together. I uninstalled firestarter, rebooted -> Nothing! so I went ahead and reinstalled firestarter -> again nothing. I'm at wits end, this upgrade is a nightmare. 

Ready to give up! Please help! (posting from XP!)

---

### Post by ubuntology on 2007-11-04
If you can ping your gateway, can you ping anything beyond it?
try pinging 64.13.232.103
then try pinging ubuntology.com
Those are the same machine. If pinging the IP works but not the name, it's DNS.

---

### Post by homerj742 on 2007-11-05
Doh, I didn't even try that. I couldn't ping google, but I will try it by IP (when I get home). thank you

---

### Post by homerj742 on 2007-11-05
Pinged by IP, got nothing, can only contact the gateway. 

Tried pinging the ubuntu machine from my Windows PC, nothing. 

Weird problem.

---

### Post by ubuntology on 2007-11-05
so, you can only ping the gateway, nothing beyond it. what about on the same side as you, can you ping your windows machines? If you can ping things on your side of the network, but nothing on the other side, are the packets getting to the router? what's the output of "sudo route"
while you're at it, whats the output of sudo ifconfig -a 
can you ping 127.0.0.1 from the linux machine? what about "ping localhost"

---

### Post by homerj742 on 2007-11-05
Thank you for all of your help. I actually figured it out, first in the network settings it was set to "roaming mode", I unchecked that box, and selected "Automatic Configuration DHCP" from the drop down.

I was able to ping out to the internet. However couldn't browse. 

NEXT, I disabled the firewall via firestarter. Now I"m back in business. 

However, I'm still having Samba issues (the Windows machines can only access it via IP and not via network places).

---

### Post by ubuntology on 2007-11-05
Glad you got it sorted. :-)
I would start another thread for the Samba problem.

---

### Post by homerj742 on 2007-11-05
Weird thing is I don't know how things got changed like that! 

Weirder yet, I had to reboot the PC to get the settings to work again (shades of windows whewww!) 

Thank you again for all your help.

---

