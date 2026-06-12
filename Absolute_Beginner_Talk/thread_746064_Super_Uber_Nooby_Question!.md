---
title: "Super Uber Nooby Question!"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by Stabilityonitsown on 2008-04-05
What's MoBlock-nfq? And whats the difference between MoBlock and Moblock-nfq? And do they both have the same blocklist(Do they both block the same thing?)???  Also why does Moblock not work with me and Moblock-nfq does? Pleeeassee answer! Thanks will be awarded!

---

### Post by SaddleTramp on 2008-04-05
> **Stabilityonitsown said:**
> What's MoBlock-nfq? And whats the difference between MoBlock and Moblock-nfq? And do they both have the same blocklist(Do they both block the same thing?)???  Also why does Moblock not work with me and Moblock-nfq does? Pleeeassee answer! Thanks will be awarded!

Try here: [http://moblock.berlios.de/](http://moblock.berlios.de/)

& here:  [http://www.debiantutorials.org/talkitup/index.php?topic=1808.msg3479](http://www.debiantutorials.org/talkitup/index.php?topic=1808.msg3479)

hope this helps

S'Tramp

---

### Post by jre on 2008-04-05
> **Stabilityonitsown said:**
> What's MoBlock-nfq? And whats the difference between MoBlock and Moblock-nfq?
The differences only relate to the packages on moblock-deb.sourceforge.net: There are two packages for MoBlock 0.8: moblock-nfq uses the kernel module NFQUEUE and moblock-ipq uses the deprecated kernel module ip_queue.
MoBlock 0.9 is only available in the nfq version, therefore only the package name "moblock".

> **Stabilityonitsown said:**
> And do they both have the same blocklist(Do they both block the same thing?)???
Have a look at /etc/moblock/blocklists.list to see what lists are used.

In moblock-nfq 0.8 the nipfilter.dat from bluetack.co.uk was used. This is a compilation of many other lists.
moblock 0.9 (which fixes a bug related to the blocklists) uses these other lists plus some more.
Make sure that you use the nipfilter.dat only with the setting BLOCKLIST_FORMAT="d" in moblock.conf and the other lists only with the setting BLOCKLIST_FORMAT="p". You can't use them at the same time because they are in different formats.

> **Stabilityonitsown said:**
> Also why does Moblock not work with me and Moblock-nfq does?
What does not work?
Have a look at the logfiles /var/log/moblock-control.log and /var/log/moblock.log and the man page
"man moblock-control".
Make sure that you use the right configuration. You may run into problems if you run one version with the configuration of the other, see above.

---

