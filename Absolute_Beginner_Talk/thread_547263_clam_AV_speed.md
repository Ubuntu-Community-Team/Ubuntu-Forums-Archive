---
title: "clam AV speed"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by frrobert on 2007-09-09
I installed Clam on my laptop running Ubuntu 7.04.  If I run clam to scan 1 small text file with just 1 line as a test, it takes almost 5 minutes to run the scan and my CPU pegs at 100% for the duration of the scan.  Something has to be wrong.  Any ideas?


Thanks

---

### Post by oilchangeguy on 2007-09-09
> **frrobert said:**
> I installed Clam on my laptop running Ubuntu 7.04.  If I run clam to scan 1 small text file with just 1 line as a test, it takes almost 5 minutes to run the scan and my CPU pegs at 100% for the duration of the scan.  Something has to be wrong.  Any ideas?


Thanks

read this:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
and this:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by SOULRiDER on 2007-09-09
I did some searching and I couldnt find anything to help you. I feel however, I must ponit out having an AV software in Linux is pretty much pointless unless youre using it in a PC that acts as a firewall and is protecting Windows PCs

---

### Post by gn2 on 2007-09-09
> **frrobert said:**
> Something has to be wrong.  Any ideas?



Yes, what's wrong is you're using anti-virus in an operating system that has no requirement for it whatsoever.

---

### Post by frrobert on 2007-09-09
Thanks for the quick answers but I'm not looking use clam to secure my system.  

I do interact with Windows users and if I get sent a MS office document with a macro virus, I want to be able to scan the file to make sure it is clean before I pass the file on.


Thanks,


Fr. Robert

---

### Post by HermanAB on 2007-09-09
Well, you are correct in that something is wrong with your setup, but you are not providing any information.

Have a look at eh log files in /var/log.  there should be a directory for clamav.  Put a tail on those then run the scan and see what pops up.

Cheers,

Herman

---

### Post by gn2 on 2007-09-10
> **frrobert said:**
> 
I do interact with Windows users and if I get sent a MS office document with a macro virus, I want to be able to scan the file to make sure it is clean before I pass the file on.



That's a responsible attitude, however it's up to Windows users to make sure they're protected.

Viruses are their problem, not yours.

---

