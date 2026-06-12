---
title: "Need Help with update manger and synaptic connection"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by Clintonostra on 2008-01-16
Had Tor and Privoxy with Opera but removed them. Email & internet connections work except for FTP, I believe. The port 8118 has to be changed but haven't been able to find a method.
Help would be greatly appreciated.

Receive this message whenever I try update:
[http://im.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:](http://im.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:) Could not connect to 127.0.0.1:8118 (127.0.0.1). - connect (111 Connection refused)
[http://im.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2:](http://im.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2:) Could not connect to 127.0.0.1:8118 (127.0.0.1). - connect (111 Connection refused)
[http://im.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2:](http://im.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2:) Could not connect to 127.0.0.1:8118 (127.0.0.1). - connect (111 Connection refused)

---

### Post by mattismyname on 2008-01-18
Sounds like tor or privoxy added some firewall rules to your system.  You can get a list of rules currently in place by doing "sudo iptables -L".  What do you see there?

---

