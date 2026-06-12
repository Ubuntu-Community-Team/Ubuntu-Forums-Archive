---
title: "Ubuntu an OS X"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by Armman on 2007-07-19
So I want to access my Ubuntu files from my iMac. So I used the network tool in Ubuntu to share the computer using samba and turned on windows file sharing on my iMac. After that my Ubuntu computer showed up in finder on my iMac. But when I tired to connect and error message came up. Is there any way that I can access my Ubuntu files from iMac over the network?

---

### Post by koganinja89 on 2007-07-19
> **Armman said:**
> So I want to access my Ubuntu files from my iMac. So I used the network tool in Ubuntu to share the computer using samba and turned on windows file sharing on my iMac. After that my Ubuntu computer showed up in finder on my iMac. But when I tired to connect and error message came up. Is there any way that I can access my Ubuntu files from iMac over the network?

It is completely theoretically possible As long as you use Samba or the mac filesharing protocol

if none of those work try setting up and ftp or something along those lines it is much easier than trouble shooting you setup for samba.

---

### Post by aysiu on 2007-07-19
For some strange reason, you also have to edit the /etc/samba/smb.conf file and change it so that browseable = yes

There's a video that explains how to do it:
[http://video.google.com/url?docid=134399432610065619&esrc=sr1&ev=v&q=ubuntu%2Bsamba&srcurl=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DAd17kma8rNM&vidurl=%2Fvideoplay%3Fdocid%3D134399432610065619%26q%3Dubuntu%2Bsamba%26total%3D6%26start%3D0%26num%3D100%26so%3D0%26type%3Dsearch%26plindex%3D0&usg=AL29H21AJ1dGWwbNNDMcZU8cAMMAJ1Yf-g](http://video.google.com/url?docid=134399432610065619&esrc=sr1&ev=v&q=ubuntu%2Bsamba&srcurl=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DAd17kma8rNM&vidurl=%2Fvideoplay%3Fdocid%3D134399432610065619%26q%3Dubuntu%2Bsamba%26total%3D6%26start%3D0%26num%3D100%26so%3D0%26type%3Dsearch%26plindex%3D0&usg=AL29H21AJ1dGWwbNNDMcZU8cAMMAJ1Yf-g)

---

### Post by annda on 2007-07-21
there is one thing left to do: allow samba connections in iptables (linux in-built firewall). i forgot that and was awfully frustrated for a while.

here is a quick introduction to installing and using firestarter (GUI for the firewall) on ubuntu:
[http://www.ubuntugeek.com/firestarter-firewall-for-your-ubuntu-desktop.html](http://www.ubuntugeek.com/firestarter-firewall-for-your-ubuntu-desktop.html)

you need to create a new rule for incoming traffic. go to the policy tab, select 'inbound traffic policy' and click the 'add rule' button. select 'samba' as the service name and the relevant ports will be filled in automatically. the easiest way is to leave the option 'anyone' to make sure all computers can access the shared files.

---

