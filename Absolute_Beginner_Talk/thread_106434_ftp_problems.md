---
title: "ftp problems"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by PilotEd on 2005-12-20
Hello...I'm running ubuntu 5.10 with proftpd.  I've downloaded an iso file on the ubuntu box and am trying to ftp the file to an XP box where my burner is.  I'm using cmd on the XP to ftp into the ubuntu box.  I'm able to login (using a non-root user) but when I use the ls or dir ftp command, the ftp connect quits.  The following message is what I get:  ftp:  get: Connection reset by peer.

I've googled this problem to no avail.  I'm not sure if the problem is on the XP end or the ubuntu end.

Is anyone else having this problem or does anyone have a sample proftp.conf file I could use?  I'm trying to ftp between 2 boxes that are inside my firewall.  I don't have any intention to put anything beyond my firewall so hopefully this simplifies the configuration process.

Thanks in advance....

---

### Post by aysiu on 2005-12-20
Maybe [this](http://ubuntuforums.org/showthread.php?t=76647) might help?

---

### Post by PilotEd on 2005-12-23
Thanks for the response.  Samba might be a future option but a simple solution is what was needed.  I was able to get ftp operable by googling and installing netkit-inetd, configuring the inetd.conf file, and configuring the proftpd.conf file.

I'm still not able to use the Windows command-line ftp client to connect but am using a gui client, ftpwanderer, to connect.

Thanks again for the help!

---

