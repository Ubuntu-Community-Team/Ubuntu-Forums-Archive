---
title: "Extremely urgent: smartctfl commands not working in Terminal?"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by Lucifiel on 2007-04-15
Okay, for the past hour or so, I've been trying to execute the following commands: 

sudo smartctl -t short /dev/sda or sudo /usr/sbin/smartctl -t short /dev/sda

and even sudo smartctl -t long /dev/sda

However, everytime it states that the test has begun, I'll get kicked back to lucifiel@lucifiel:~$ 

I've been trying various variants of the commands but no use. They still don't work. 

Does anyone know? Please, I'm trying to confirm a certain SMART issue. Asking for help in #ubuntu+1 didn't get any answers, neither did trying to conduct several searches through Google and so on. Man, I wish I didn't have to keep asking but I'm still rather new to Linux commands. :/

---

### Post by bobplano on 2007-04-15
try adding a -v(verbosity) so it will output what it is doing

---

### Post by Lucifiel on 2007-04-15
> **bobplano said:**
> try adding a -v(verbosity) so it will output what it is doing

Thank you. Do you mean something like this? 

sudo smartctl -t short /dev/sda -v

Hmmm... no, that didn't quite work. Nor does sudo smartctl -t short /dev/sda -v 200 or sudo smartctl -t short /dev/sda -v --200 . Nope, not even sudo smartctl -t short /dev/sda -v writeerrorcount 

Oh boy, I really am clueless about this.

---

### Post by confused57 on 2007-04-15
I've never used smartctl, but found this with a Google search:
[http://gentoo-wiki.com/HOWTO_Monitor_your_hard_disk(s)_with_smartmontools](http://gentoo-wiki.com/HOWTO_Monitor_your_hard_disk(s)_with_smartmontools)

It's for Gentoo, but should work the same...did you determine if your bios supports smartctl?

---

### Post by Stunt Double on 2007-04-15
"sudo smartctl -s on /dev/sda"
Then     "sudo smartctl -t long (or short) /dev/sda"
Then     "sudo smartctl -a /dev/sda"
 The top line turns it on and must be repeated every new terminal.

---

### Post by Lucifiel on 2007-04-19
Hmmm it seems that this command worked "sudo smartctl -d ata -a /dev/sda" while every other command like "sudo smartctl -s on /dev/sda" resulted in failure possibly because my SATA hdd is dying. 

However,  "sudo smartctl -t long (or short) /dev/sda" worked.  While "sudo smartctl -a /dev/sda" didn't because somehow, S.M.A.R.T failed. 

Anyways, I've since managed to succeed by running "sudo smartctl -d ata -a /dev/sda" which I found from this thread: [http://ubuntuforums.org/showthread.php?t=343313&page=2&highlight=smartctl](http://ubuntuforums.org/showthread.php?t=343313&page=2&highlight=smartctl)

Hope this helps anyone who's this issue, too. :)

---

