---
title: "Should I migrate from CentOs?"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by jimwillsher on 2005-12-20
Hi all,

I must confess, I know nothing about Ubuntu....

I currently have a stable CentOs 4.2 installation. It's a server-only install, running Apache, MySql and PHP. I also have the Slim Devices Slimserver software, serving my MP3 collection.

The hardware is bog-standard home-built i386 with a P4 and 2Gb memory, the only complexity being the 3Ware 8006 RAID card.

I'm a bit frustrated with CentOs as its often slow to release new versions of software, as they only release whatever RedHat releases. For example, PHP is still 4.3; SpamAssassin is still 3.0.4.

Would I benefit from reinstalling and using Ubuntu? My main criteria are:

[LIST]
[*]Native support for my 3Ware RAID card and my Realtek RTL-8169 GigaBit ethenet card
[*]Easy installation - I'm not a Linux guru by any means!
[*]Installation of RPMs without having to recompile.
[*]Server only, no GUI required.
[/LIST]

Any comments? Particularly from people with RHEL or CentOs 4.2 backgrounds.

Many thanks!


Jim

---

### Post by Rinzwind on 2005-12-20
1. The raid controller should not be a problem. A quick google search on it shows good support for Linux. BUT if it works under Redhat I suppose it works under Ubuntu (haven't got 1 myself so...). You might be able to check this with the LIVE cd.

2. I started begin december and came from Windows XP but I use Redhat alot at work. Ubuntu's been very nice to me and I only had problems that I found CHALLENGING to solve and not hindering me at my experience with Ubuntu. 

3. Well RPM's itself often need to be re-packed. But from what I've seen it's a 2 line coding (something with the command 'alien'. Search for it on these forums :) )

4. Not a problem: use 'server' during bootinstall and it's a 'server' install.

Thing is. Ubuntu has a 6 months cycle. 6 months after Breezy Dapper should be released and fixed. A lot can happen in 6 months but Redhat is alot slower ;) 


So Ubuntu might be your thing, it might not be. Only trying a live cd will ;)

---

### Post by jimwillsher on 2005-12-20
Excellent, thank you. I will try a LIVE CD and see what happens. I'll take a screen up to the attic where the server lives and give it a whirl!

Cheers,


Jim

---

### Post by Rinzwind on 2005-12-20
:D

Hey, the other people on these forums are a bit shy but with time they also comment ;) 

Live cd's are great. 
Just don't forget to use 'live' as a bootparameter. I think 'server live' works too.
Oh and don't download the wrong live cd cuz you might get hooked on gnome ;)

---

### Post by jimwillsher on 2006-01-20
Just a quick update. My webserver is now up and running on breezy!


I'm using:

Postfix
procmail
apache2
php5
mysql 4.1
amavisd
dovecot
spamassassin
squirrelmail
clamav


and all seems to be performing beautifully. I'd delighted!

(oh, and I got my slimserver music software to work, using alien as was suggested)

Happy boy :-)



Jim

---

