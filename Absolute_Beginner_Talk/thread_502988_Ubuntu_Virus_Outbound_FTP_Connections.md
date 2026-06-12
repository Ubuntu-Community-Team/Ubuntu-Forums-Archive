---
title: "Ubuntu Virus? Outbound FTP Connections"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by nickburns on 2007-07-17
I have installed 6.10 and put nagios on is at my work.  It has ran great for several months.  I looking at our hardware firewall logs, the machine as recently started making outbound FTP connections to the outside world.  Not just a couple, but hundreds of connections to servers that seem to be random.

I have ran chkrootkit and it has found no infections, so I am lead to believe that perhaps there is a malicious program running on the system.

I do not have sftp or any other ftp software installed, at least that I am aware of. 

A little help???

I thought all ports are closed by default on Ubuntu....

---

### Post by rickycodie on 2007-07-17
install clam av and se if that finds anything.

sudo apt-get install clamav

---

