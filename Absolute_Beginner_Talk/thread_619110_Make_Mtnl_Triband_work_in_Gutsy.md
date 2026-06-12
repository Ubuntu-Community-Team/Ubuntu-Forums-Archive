---
title: "Make Mtnl Triband work in Gutsy"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by Krishnan on 2007-11-21
Can anyone tell me the procedure to configure MTNL Broadband in Gutsy. I receive the pings though iam not able to browse websites. I did see this [http://db.glug-bom.org/wiki/index.php/MTNL_Triband](http://db.glug-bom.org/wiki/index.php/MTNL_Triband). But the problem remains the same.

---

### Post by kleo skywalker on 2007-11-22
I don't know about the guide you mention, but here's what I did to get my MTNL Broadband working:

Go to System-->Administration-->Network. Click on the "Properties" button next to "Wired Connection". Uncheck the "enable roaming mode" box, set Configuration to "Static IP", and set the rest as follows:
IP address: 192.168.1.5
Subnet mask: 255.255.255.0
Gateway Address: 192.168.1.1
Back in the "Network Settings" menu, set DNS servers as:
Primary: 59.179.243.70
Secondary: 203.94.243.70

In the Terminal (Applications-->Accessories-->Terminal), run this command ```
sudo pppoeconf
```Once done, reboot.

Open Firefox, in the address bar enter > [http://192.168.1.1/](http://192.168.1.1/)Enter username and password when prompted (by default, both are *admin*). You should now be connected to the internet.

Every once in a while, you'll be able to ping to 59.179.243.70 but not open any webpages. I have no idea why that happens.

You can check all the numbers given above by calling your local MTNL Junior Engineer (JE).

Do post back whatever happens. Good luck.

---

