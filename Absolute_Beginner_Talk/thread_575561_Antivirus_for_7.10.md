---
title: "Antivirus for 7.10"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by Strevethick on 2007-10-14
Is there an antivirus available for Ubuntu 7.10 release  Tried installing the AVAST antivirus but unable to get the application to run.

---

### Post by mindtrick on 2007-10-14
[http://free.grisoft.com/doc/5390/us/frt/0?prd=afl](http://free.grisoft.com/doc/5390/us/frt/0?prd=afl)

---

### Post by PmDematagoda on 2007-10-14
Why do you need an AV for an OS which has virtually no viruses?

---

### Post by por100pre1 on 2007-10-14
Welcome to the forums! Did you try to install the .deb installer? BTW, read [this]("http://www.psychocats.net/ubuntu/security").

---

### Post by n3tfury on 2007-10-14
you don't really need one for linux unless you need it to scan windows partitions.

---

### Post by Capricori on 2007-10-14
Half of Ubuntu users reckon you don't need an Anti-Virus, because there is little or no threat to Linux from viruses, for various reasons. The other half reckon its better to have a virus program installed just in case. ClamAV seems to be recommended a lot. "sudo apt-get install clamav" in a terminal. Read the stickies in the 'Security and Servers' forums, should help you make your own mind up :)

---

### Post by Strevethick on 2007-10-14
Thanks.  Will give it a try,

---

### Post by marco123 on 2007-10-14
You would be much better off installing rkhunter ( sudo apt-get install rkhunter ) for a Linux box.  You only need AV if there's windows boxes on your network.  IIRC they only scan for windows viruses anyway.

---

### Post by Malibu Illusion on 2007-10-14
> **marco123 said:**
> You would be much better off installing rkhunter ( sudo apt-get install rkhunter ) for a Linux box.  You only need AV if there's windows boxes on your network.  IIRC they only scan for windows viruses anyway.

+1

There's not much point in using an AV package for Linux unless you're interacting with Windows boxes.  Another application you may wish to check out is: chkrootkit.

---

### Post by Capricori on 2007-10-14
Have a read through [this thread.]("http://ubuntuforums.org/showthread.php?t=510812")
It covers anti-virus, rootkits, and a few more things.

---

### Post by FredB on 2007-10-14
Well, even if an antivirus is nearly useless, why not clamav ?!

Linux AV are only useful to stop virus spreading from windows zombies using mail.

---

### Post by Strevethick on 2007-10-16
Thanks for all you help and comments  been very useful

Steve

---

### Post by bodhi.zazen on 2007-10-16
> **FredB said:**
> Well, even if an antivirus is nearly useless, why not clamav ?!

:lolflag:

> **Strevethick said:**
> Thanks for all you help and comments  been very useful

Steve

Steve: Welcome to Ubuntu. Since you have the answer you need I am going to close this thread (read on, antivirus discussions tend to recur and can get out of hand) with my usual :


Anti-Virus scanning on Linux is of limited utility as there are no know linux viruses "in the wild" so there is essentially nothing to scan for.

In addition Antivirus is reactive, not proactive meaning it can not protect you from the next Linux virus until AFTER it is released, not before.

A potential use of linux antivirus is to "protect" windows or if you are running a mail server, and even then, IMO, Windows antivirus is better then Linux antivirus.

In the end, the choice is yours to make, but I would be willing to bet that the more experience one has with Linux (Ubuntu) the less one feels the need for scanning / for 

viruses.

If you would like to learn a little about Ubuntu  security, see this link :

[[color=black]Ubuntu Security[/color]](http://ubuntuforums.org/showthread.php?t=510812)

If you would like to discuss antivirus on linux, see this forum:

[ Recurring Discussions](http://ubuntuforums.org/forumdisplay.php?f=302)

---

