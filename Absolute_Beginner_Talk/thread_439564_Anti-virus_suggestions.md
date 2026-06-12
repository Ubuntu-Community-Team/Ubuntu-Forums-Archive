---
title: "Anti-virus suggestions"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by Belliinator on 2007-05-10
I am unaware if this has been spoken about before, but what kind of anti-virus, anti-ad or firewall etc are available for linux and what do you reccommend?

---

### Post by nickburns on 2007-05-10
You don't need any...

---

### Post by Belliinator on 2007-05-10
but I do believe ther are linux viruses out there.

---

### Post by PhatStreet on 2007-05-10
I believe the most popular one is ClamAV, but I could be wrong. But honestly, you're only going to need it if you're paranoid about things.

---

### Post by aktiwers on 2007-05-10
You wont need it..  I havent had a Virus or any adware yet, and I used Linux for about 2 years in total now, on 2 PC's.

---

### Post by Belliinator on 2007-05-10
Ok, well coumt me as paraniod. I'll try ClamAv. Thankyou.

---

### Post by Slim Backwater on 2007-05-10
Antivirus - I've heard that the scale of Linux viruses in on the order of 10s, if that many, but nothing to back that up right now.

Anti-Ad - Firefox has many blockers built-in, others are available as extensions, and Adware is written for Windows (the executable kind) which won't run on Linux.

Firewall - One aspect of a firewall is to protect your open ports (TCP/UDP) and by default, Ubuntu doesn't have any open ports (type netstat -an | grep LISTEN to see)  The other aspect is to control which programs you run should have internet access, which is usually a concern if your computer is 'owned', by a virus or adware, so without those, that aspect of the firewall is not a concern.

ClamAV is good, and I've used it to scan hard drives from Windows computers for Windows viruses, but I don't run it continuously.

HTH

---

### Post by aktiwers on 2007-05-10
I actually once found some Virus on my HD when scanning it for fun..  
Well it turned out it was some exe files I didnt know I had from an old old Windows backup.. but thats all I have found.
Good Luck

---

### Post by Wiebelhaus on 2007-05-10
[http://www.gnu.org/fun/jokes/evilmalware.html](http://www.gnu.org/fun/jokes/evilmalware.html)



> evilmalware 0.6 (beta)

Copyright 2000, 2001, 2003, 2005
E\/17 |-|4><0|2z Software Foundation, Inc.

This is free software; see the source for copying conditions.  There is
NO warranty; not even for MERCHANTABILITY, COMPLETE DESTRUCTION OF IMPORTANT 
DATA or FITNESS FOR A PARTICULAR PURPOSE (eg. sending thousands of Viagra 
spams to people accross the world).

Basic Installation
==================

Before attempting to compile this virus make sure you have the correct
version of glibc installed, and that your firewall rules are set to `allow 
everything'.

1. Put the attachment into the appropriate directory eg. /usr/src

2. Type `tar xvzf evilmalware.tar.gz' to extract the source files for 
   this virus.

3. `cd' to the directory containing the virus's source code and type
   `./configure' to configure the virus for your system.  If you're
   using `csh' on an old version of System V, you might need to type
   `sh ./configure' instead to prevent `csh' from trying to execute
   `configure' itself.

4. Type `make' to compile the package. You may need to be logged in as 
   root to do this.

5. Optionally, type `make check_payable' to run any self-tests that come 
   with the virus, and send a large donation to an unnumbered Swiss bank 
   account.

6. Type `make install' to install the virus and any spyware, trojans
   pornography, penis enlargement adverts and DDoS attacks that 
   come with it.
  
7. You may now configure your preferred malware behaviour in 
   /etc/evilmalware.conf .

SEE ALSO
   evilmalware(1), evilmalware.conf(5), please_delete_all_my_files(1) 

---

### Post by aktiwers on 2007-05-10
> **sx66gns said:**
> [http://www.gnu.org/fun/jokes/evilmalware.html](http://www.gnu.org/fun/jokes/evilmalware.html)

:lolflag:

---

### Post by fakie_flip on 2007-05-10
chkrootkit is all i use, and ive still never had a problem with viruses, spyware, or other ms infestations. ive been using linux for over 2 years, not just ubuntu. the only malicious code that ran on my linux box is one that i tested on my computer called the fork bomb.

---

### Post by Celegorm on 2007-05-10
You might also try rkhunter, and I've heard firestarter is nice for managing the built in firewall called iptables. Really, the most important thing is not to install software from untrustworthy sources.

---

