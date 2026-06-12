---
title: "Ubuntu 6.06.1 is from August 2006 - 140MB of updates now - Time for 6.06.2!!!"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by emarkay on 2007-01-23
Since this is a "LTS", what is the release schedule for incremental updates.  

Every install I do now takes a over an hour to get all the updates!
[B][I]
When will a "up-to-date- ISO image be made of 6.06 Dapper that has all the security and program updates be made available?[/I][/B]

---

### Post by emarkay on 2007-01-23
Anyone???

---

### Post by Happy_Man on 2007-01-23
Well, as far as I can tell, the updates are sent out when they're made, there's no "patch Tuesday" like with Windows. Are you using a LiveCD from August, or are you burning new ones every time? I think the Ubuntu guys periodically update the LiveCDs, but then, updates do come fast and thick. Ah well...

---

### Post by oilchangeguy on 2007-01-23
if you're using dial-up you may want to consider a highspeed connection. because no matter what os you use, dial-up is going to be slow doing any type of download.

---

### Post by Tux Aubrey on 2007-01-23
I agree with the OP.

AFAIK there have been no builds since August 06.

The update from the current Dapper Live CD (6.6.1) to a full install is way too large and an impediment for those wanting to introduce Ubuntu to new users.

Might be worthy of a "bug report" on launchpad.

EDIT: Done! see Bug #81208:

---

### Post by emarkay on 2007-01-23
OCG - I do have broadband - I get anywhere from 25kbps to 44kbps download - but some of the (both US and International) Ubuntu repositories slow that down to 9kbps or less at times!

HM - The updates are sent out as needed, but that doesn't help me if I need to do a few PC's with 6.06 and have to wait a few hours to download it all....  The only ISO there is is the one from August...

TA - Thanks I just signed up for a Launchpad account, but didn't think it's a bug - but I thank you for alerting them!!! - IMHO there NEEDS to be a "PORTAL" ***HERE***, where us forum folks can alert the Cannonical folks on sincere questions and comments - I feel [and fear] that a LOT of valuable comments and suggestions HERE are being wasted, because no Ubuntu developers seem to EVER appear here...

Oh well time to waste more bandwidth on a fresh install....

---

### Post by _duncan_ on 2007-01-24
if you have a fully-updated installation, you can copy the contents of /var/cache/apt/archives to a blank CD, then copy these into the exact same folder on the new installation.

go through the motion of updating the new install. Synaptic (or whatever you use to update) will *see* the .deb files and no longer download from the ubuntu repositories.

---

### Post by AlanRogers on 2007-01-24
> **_duncan_ said:**
> if you have a fully-updated installation, you can copy the contents of /var/cache/apt/archives to a blank CD, then copy these into the exact same folder on the new installationThat's a very useful tip, thank you. I think it's equally relevant to those folk with multiple machines and a capped download connection.

Following that line of thought further, is it possible to share that directory across the network and configure it as a preferred repository for other machines?

---

### Post by david_kt on 2007-01-24
> **AlanRogers said:**
> That's a very useful tip, thank you. I think it's equally relevant to those folk with multiple machines and a capped download connection.

Following that line of thought further, is it possible to share that directory across the network and configure it as a preferred repository for other machines?

If you want to share across network for many computers, it is better to install apt-cacher. Basically it is similar to setting up local mirror in your network. One computer as a server/mirror, and other computers will download from that server (locally). Below is the instructions:

[http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher](http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher)
[http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher-p2](http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher-p2)

I have not tried it yet though. But I will try it either this week or next week.

Regards,
DK

---

### Post by emarkay on 2007-01-24
> **_duncan_ said:**
> if you have a fully-updated installation, you can copy the contents of /var/cache/apt/archives to a blank CD, then copy these into the exact same folder on the new installation.
go through the motion of updating the new install. Synaptic (or whatever you use to update) will *see* the .deb files and no longer download from the ubuntu repositories.

***Someone ought to double check this and than STICKY this!!!!***

---

### Post by lamego on 2007-01-24
You can also try apt on CD:
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by _duncan_ on 2007-01-24
> **AlanRogers said:**
> That's a very useful tip, thank you. I think it's equally relevant to those folk with multiple machines and a capped download connection.

Following that line of thought further, is it possible to share that directory across the network and configure it as a preferred repository for other machines?

It's technically possible especially at the corporate / enterprise level, but may not be practical for a network of only a few computers.

What you have on the /var/cache/apt/archives folder is just a collection of all .deb files installed / updated into the system. It lacks other info that a *true* repository has. So the ubuntu package managers will not be able to *talk* to it directly. You will have to use a utility such as those mentioned in other posts to convert it into a pseudo local repository, then alter the /etc/apt/sources.list file to point to it.

A compromise will be to just share the .deb files across the network, then copy said files into individual /var/cache/apt/archives folders as necessary.

---

