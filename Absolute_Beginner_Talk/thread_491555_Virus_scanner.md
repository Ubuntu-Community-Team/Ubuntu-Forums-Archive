---
title: "Virus scanner?"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by czepluch on 2007-07-03
Is there a virus scanner in ubuntu ?

---

### Post by KIAaze on 2007-07-03
You can install ClamAV from the repositories.

---

### Post by Nekiruhs on 2007-07-03
You really don't need one for Linux.

---

### Post by KIAaze on 2007-07-03
Here are some others:
-AVG Antivirus
-Avast Home for Linux
-Vexira antivirus

There is also a GUI available for ClamAV. But it has a pretty old look.

> You really don't need one for Linux.
It's always good to be safe. There have been GNU/Linux viruses and [there might be more in the future]("http://computerworld.com/securitytopics/security/virus/story/0,10801,110330,00.html").
And antiviruses like ClamAV can also scan mail sent to Windows users as well as the Windows partitions for viruses.

---

### Post by czepluch on 2007-07-03
But is it necessary or not?

---

### Post by Nekiruhs on 2007-07-03
> **czepluch said:**
> But is it necessary or not?
Not unless your woorried about passing on windows viruses.

---

### Post by cogadh on 2007-07-03
There have only been 14 viruses for Linux since 1991. All of the holes that those viruses exploited are closed and there are no new viruses currently in the wild. As long as you are reasonably security aware (i.e. don't open e-mail attrachments, only download from trusted sources, etc.) you really don't need an antivirus application to protect your Linux system.

That being said, the only reason to run an antivirus application in Linux is to protect any Windows users you may interact with through your machine. You still have the ability to send Windows-virus infected files to Windows users.

---

### Post by Jimmyfj on 2007-07-03
I use AVG antivirus on my system, simply because I like the Ubuntu Code of Conduct and the thoughts that made it real - Be considered, is one of the aspects in CoC and to be considered, to me, also mean that you think before act, and send anything to none-secure systems like Windows. This way I fell I'm promoting Linux in the best manner.

---

### Post by hyper_ch on 2007-07-04
Well, if the windows machines get infected constantly maybe that makes people change to linux :) I'm one who doesn't use av anymore.

---

### Post by dptxp on 2007-07-04
A very important reason for running Linux is because I do not want my system to run slow running antivirus.

---

### Post by skymera on 2007-07-04
well if loads of people change to linux, it will become a target for virus creating retards.
in my opinion, make the most of virus free

---

### Post by moredhel on 2007-07-04
But linux is inherently harder to make viruses for ;)

---

### Post by hyper_ch on 2007-07-04
virii on windows are very dangerous because of two things:

(1) Most people assume admin rights all the time to actually be able to work with their computer
(2) The monolithic design of windows

Linux has another approach and even if a virus could annoy a user it will very unlikely be as devastating as a windows virus

then the number of computers doesn't have any significance to being a target. Apache2 is the most common web server however IIS is the moste beloved target ^^

---

### Post by lbelloq on 2007-07-04
How do you install AVG in Ubuntu?

---

### Post by Wiebelhaus on 2007-07-04
> **skymera said:**
> well if loads of people change to linux, it will become a target for virus creating retards.
in my opinion, make the most of virus free


evilmalware 0.6 (beta)

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

### Post by tribaal on 2007-07-04
> **sx66gns said:**
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

3 letters: L O L 

- trib'

---

