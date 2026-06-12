---
title: "Virus Related Question."
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by wcks48 on 2006-04-05
Well, i'm just quite confused bout the virus problem for linux, Kubuntu particularly.

So, unlike MS Windows, as i heard and looked these days, linux are free from the attack of virus such as trojan horse. but why still lots of anti-virus built on linux platform? and as i noticed and not sure bout the auto-protect mode is available for linux, but only for scanning. is it linux just being the immortal from direct virus attack? and only possibility is accidentally stored the virus inside the folder and not a big effect for the linux OS?

so could someone tell me about this in more detail?
thanks.

---

### Post by NeghVar on 2006-04-05
Linux does have viruses, last time I seen it was around 40 or so. If any of these ever did get into your system and you were only a regular user they could only nuke your files, unlike windows where you are 'root' always. This may seem bad but hey your computer is still alive.

Most people run Anti-Virus for Linux for two main reasons:

1) To protect a Windows partition, and other less fortunates out there who run Windows. Its not much but we should do all we can to help protect the less fortunate as much as we can.

2) My personal favorite and the reason I run 3 seperate AV aps, extreme paranoia...

---

### Post by Sef on 2006-04-05
If you had an email client, a windows virus would not infect you, but it could be sent to your friends who most likely use windows.

---

### Post by wcks48 on 2006-04-05
how bout virus of linux? is it only hide inside my user own folder and won't be going anywhere else inside the root? 
then once i log in as root, would it spread out?

then no need auto-protect for linux, am i right?

---

### Post by htinn on 2006-04-05
The main advantage to Linux is that most software provided to you is open source, so there is nowhere for an exploit or backdoor to hide. Vulnerabilities still exist, but they can be quickly dealt with.

Of course hackers are not partial, and you still see lots of people try to infect Linux systems, so you still need protection.

---

### Post by ubuntu27 on 2006-04-06
Check this out: [http://www.linux-magazine.com/issue/62](http://www.linux-magazine.com/issue/62)

Linux Magazine issue 62 talking about Virus stuff. You can read some of them online.

---

### Post by dcstar on 2006-04-06
[QUOTE=NeghVar]
.......
Most people run Anti-Virus for Linux for two main reasons:

1) To protect a Windows partition, and other less fortunates out there who run Windows. Its not much but we should do all we can to help protect the less fortunate as much as we can.

2) My personal favorite and the reason I run 3 seperate AV aps, extreme paranoia...[/QUOTE]
I only run ClamAV to scan my incoming e-mail in Evolution and let me know what crap is out there threatening most other platforms (that means Windows, not Linux.....).

The only advantage to my Linux system is that it identifies the "Phishing" e-mails with the supposedly hidden/munged links in the e-mails (but they go to my Junk directory anyway via Spamassassin, so even then it's only academic information).

---

### Post by Kurt` on 2006-04-06
[QUOTE=wcks48]how bout virus of linux? is it only hide inside my user own folder and won't be going anywhere else inside the root? 
then once i log in as root, would it spread out?

then no need auto-protect for linux, am i right?[/QUOTE]
Any program you run as a user has THAT user's rights...

If you ran a virus as your normal user, it could only modify files/folders where you have write access (/home/youruser, /tmp, etc.). It wouldn't be able to, say, replace binaries in /bin or /usr/bin with corrupt versions or something like that

If you run it as root, the virus has write permissions to the ENTIRE drive, and all betsd are off

Just be careful what you run as root. :)

---

### Post by TrendyDark on 2006-04-06
What's a good anti-virus program that won't be annoying like Norton?

---

### Post by meborc on 2006-04-06
linux world likes to use clam-av (in repositories) ... but there are also linux ports to avg and f-prot... there are some how-to's in tips and trics forum


avg how-to [http://www.ubuntuforums.org/showthread.php?t=136064&highlight=avg](http://www.ubuntuforums.org/showthread.php?t=136064&highlight=avg)
f-prot how-to [http://www.ubuntuforums.org/showthread.php?t=88357&highlight=f-prot](http://www.ubuntuforums.org/showthread.php?t=88357&highlight=f-prot)

made by AI

---

### Post by Gracye on 2006-04-06
Quick question about dual booting and viruses. I've disabled the internet on Windows whenever I log out of it wiill this protect me somewhat against viruses when I switch over to Linux?

---

### Post by meborc on 2006-04-06
if you are dual-booting and sharing files between linux/windows, it doesn't matter where the infected file comes from... weather from linux or from windows (when internet is enabled), when you have a partition shared both by win and linux, the virus will eventually find a way to your win box and infect it...

so use av soft ;)

---

### Post by Gracye on 2006-04-06
okie dokie. thanks for your help :)

Which av software is the best for Linux?  I have Norton for Windows but I don't like it.  It didn't stop a Trojan from hacking in before so I don't trust it.

---

### Post by meborc on 2006-04-06
read my post about av soft in the end of the previous page ;)

---

### Post by Gracye on 2006-04-06
ahh didn't see that post XD thanks again!

---

