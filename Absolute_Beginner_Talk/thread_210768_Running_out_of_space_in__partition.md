---
title: "Running out of space in / partition"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by ezebe on 2006-07-07
Hi,

I'm fairly new to Ubuntu, running from a 20 Gb HD as dual boot on my windows machine. I have three partitions on hdb: 
name,,,,,size,,,,,,,,free
/,,,,,,,,,,,,3.7 Gb,,,,,,100Mb
/home,,,,14.3 Gb,,,,,13ish Gb
/swap,,,,,,650ish Mb
     (or whatever the official swap title is)

I originally had breezy, and things were fine, but during the upgrade to dapper, I ran out of space on / and it all crashed, i think towards the end of the dpkg stage (everything had downloaded fine and was installing).  I had a Guru who helped me sort this out (i think he deleted some temp files and partially restarted the dpkg process, and it's been working ok since.  He's recently moved away, however, and I'm unsure what to do now.

I HAVE SO FAR DONE:
Having looked for advice online, I deleted *.deb from var/cache/archives which has given me 400Mb breathing space in total. but i wondered:

MY 3 QUESTIONS:
Is 3.3ish Gb really all needed for a Dapper install, or did i miss some kind of "breezy-removal" step due to my crash?

What else can I safely delete?

How can you move the partition? (I get the impression i have to do it remotely from another PC..)

Thanks for your advice,

Z

---

### Post by halfvolle melk on 2006-07-07
For cleaning up unwanted stuff you can refer to this thread:
[http://www.ubuntuforums.org/showthread.php?t=140920](http://www.ubuntuforums.org/showthread.php?t=140920)

Adjusting your partitions can be done with the live CD. It has Gparted on it.
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

---

