---
title: "AVG 7.5 Scan problem"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by The-Falconer on 2007-06-30
Hi,
    I am new to Ubuntu, but I like it. I set it up with few problems in a triple boot with XP and Vista. I want to use AVG 7.5 and have installed it, and fixed the update problem, but when I do a full scan from / it stops at  /dev.
I can run a complete scan if I uncheck  /dev with oly 2 errors as follows:
    /lib/   Cannot open; not checked! Permission denied
   /proc/ Cannot open; not checked! Invalid argument

If I try to scan all from / it stops after 108 files and this is the error I get:
/     Cannot open; not checked! No such device

If I try to scan just /dev it stops after 2 files and i get this:
/dev/     Cannot open; not checked! No such device

I have tried directories below /dev/ with mixed results from simply stop the scan to locking up AVG all together.

Any help would be appreciated.

Wish my vendors would right in Linux. 
Thank you,
Pete

---

### Post by oilchangeguy on 2007-06-30
you really don't need anti-virus software in linux. if you send a document to your windows partitions, just make sure to scan them before you open them.
and what do you mean by this statement - Wish my vendors would right in Linux. ? do you mean write, and not right? if so, the statement makes sense.

---

### Post by overdrank on 2007-06-30
> **The-Falconer said:**
> Hi,
    I am new to Ubuntu, but I like it. I set it up with few problems in a triple boot with XP and Vista. I want to use AVG 7.5 and have installed it, and fixed the update problem, but when I do a full scan from / it stops at  /dev.
I can run a complete scan if I uncheck  /dev with oly 2 errors as follows:
    /lib/   Cannot open; not checked! Permission denied
   /proc/ Cannot open; not checked! Invalid argument

If I try to scan all from / it stops after 108 files and this is the error I get:
/     Cannot open; not checked! No such device

If I try to scan just /dev it stops after 2 files and i get this:
/dev/     Cannot open; not checked! No such device

I have tried directories below /dev/ with mixed results from simply stop the scan to locking up AVG all together.

Any help would be appreciated.

Wish my vendors would right in Linux. 
Thank you,
Pete

Hi and welcome, it is my understanding that is why linux has no viruses. Just like your scan and probably half the threads about permission.  The scan does not have permission to scan the file like the virus cant. ;)

---

### Post by RomeReactor on 2007-06-30
Hi. This topic crops up here quite frequently; the usual response is "you don't need antivirus software **for** Linux, as there are no known viruses in the wild (or very, very few)". The only reason to have an antivirus in Ubuntu is to scan files before sending them to windows machines (like your other partitions, or to windows-using people). If so, then I suggest you instead use **clamav** (found in "Add/Remove" or Synaptic), or [F-prot]("http://www.f-prot.com/download/trial_forms/linux-ws-deb.html"); both are command line scanners, very simple and efficient, in my opinion. You can get a graphical interface for clamav in the form of **clamtk** (more Gnome-like) or **klamav** (for KDE), Both found through Add/Remove or Synaptic.

And welcome! :D

---

### Post by The-Falconer on 2007-06-30
I know A virus may be rare in linux systems, but it only takes one to do damage or steal information, and the only system that would be 100% virus free would be one that loaded from a read only media. Ubuntu Live CD is 100% virus free at boot, but even it could be infected if you goto a malicious website, but reboot and Virus is eliminated.  AVG is a good anti-virus and that is why I trust it. If you run your OS from a hard drive you must have anti-virus.






Yes, I did mean write in my statement at the bottom.

Thank you,
The-Falconer

---

### Post by oilchangeguy on 2007-06-30
i agree avg is a good free anti-virus program. i use it on my windows boxes. but it can and does miss some viruses/trojans, etc. (i've never had a problem) no program is perfect. however on my linux boxes i run no anti-virus software. it's not needed, pure and simple. 
the main reason it's not needed, is because user accounts are not set up as root/admin. whereas in xp the default user account setup is admin. and not limited. if xp users would run as a limited user, virus problems would greatly decrease.

---

### Post by RomeReactor on 2007-06-30
If you're really determined to use an antivirus, I suggest you take a look at the ones I posted; they're very good, and I've come across threads where people seem to have trouble setting up AVG (in that regard I can't help, sorry; I used to have AVG when I used windows, but the only AV scanners I've used in Linux are clamav and f-prot). Oh, and there's also Aegis (search for **virus** on Add/Remove, or for aegis on Synaptic).

---

### Post by The-Falconer on 2007-06-30
I do agree about admin rights, as i am the IT department for a small sheriff's office and the first thing i did when i took over was take all admin rights away, and the second was put in a   url filter to block some web sites (myspace, porn sites and game sites). Things seem to be under control now. I ask my vendor this week if they considered the Linux OS, but they said they were a Microsoft Gold partner. If anyone knows of good Records Management System, Computer Aided Dispatch and Jail Management system For Linux let me know. 

I will try the other anti-virus programs.

Thank You,
The Falconer

---

