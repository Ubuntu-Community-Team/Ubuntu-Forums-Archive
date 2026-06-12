---
title: "[SOLVED] reboot"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by maryjanua on 2007-09-24
hi iv been using ubuntu for about 10 days and i occasionally get this message when i have switch on/reboot the pc
/dev/hda2 has been mounted 31 times without being checked - force check
after checking it says 1.4% non-contiguous
is this normal?
also i have installed the free avg for linux and it wont update but then again it doesnt find any problems either
am i being over cautious with these things? does it matter?
:)

---

### Post by hyper_ch on 2007-09-24
[http://lists.debian.org/debian-user/2001/07/msg02685.html](http://lists.debian.org/debian-user/2001/07/msg02685.html)
> 
This isn't an error so much as an observation.  It's roughly the same
as noting that 50% of the sentences in this paragraph aren't on single 
lines; it suggests non-optimal performance but there's nothing wrong
per se.  On my system, partitions tend to have 4-6% non-contiguous
files.  0.6% is very good.

So I guess it's nothing to worry about.

Why do you run an AV on linux?

---

### Post by PartisanEntity on 2007-09-24
At this point, you will only need an anti-virus application installed in Ubuntu if you are worried about passing on windows viruses to windows users (through emails or files you receive perhaps).

---

### Post by maryjanua on 2007-09-24
thanks
i wasnt really sure if i needed an av on ubuntu
thought id b better off safe than sorry as iv only used windows before and even with an av iv gotten viruses( not often but occasionally)
also i take it theres no need for anti spyware (spybot etc.)
so would i be as well getting rid of the av?

---

### Post by maryjanua on 2007-09-24
also when i do update manager i get this error:
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
how do i fix this pls?

---

### Post by mali2297 on 2007-09-24
> **maryjanua said:**
> thanks
i wasnt really sure if i needed an av on ubuntu
thought id b better off safe than sorry as iv only used windows before and even with an av iv gotten viruses( not often but occasionally)
also i take it theres no need for anti spyware (spybot etc.)
so would i be as well getting rid of the av?

There is no point to use AV or anti-spyware to protect your Linux system. The only reason to have those is, like PartisanEntity said, if you want to scan files for Windows virus before sending them to Windows users.

---

### Post by PartisanEntity on 2007-09-24
> **maryjanua said:**
> 
so would i be as well getting rid of the av?

I think one of the hardest things to adapt to when switching to Ubuntu from Windows is av software. Like you, when I was new to Ubuntu, I installed AVG. A few months later I removed it and haven't used any since.

It depends on how much you email and what kinds of files you email.

---

### Post by hyper_ch on 2007-09-24
you don't need av or anti-spyware on linux... there are about 40 known viruses for linux - most of them proof-of-concept, meanint they exist to show that it is possible to have viruses on linux.

Due to the total different architecture of linux compared to windoze they cannot wreck as much havoc on a linux as on windows... most likely yu would have to expressivly grant permissions to wreck havoc ;)

And the AV is normally used to filter viruses from emails or from a file server to protect windoze users from them. Although I'm of the opinion that it's the job of the windoze users to protect them themselves...

---

### Post by maryjanua on 2007-09-24
thanks folks i think i'll uninstall it
whats this mean when i go in terminal and do : sudo apt-get update

W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems
billym@billym-desktop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

---

### Post by hyper_ch on 2007-09-24
You did not install the GPG keys for that repository. That GPG key should be published on the tuxfamily homepage.
The reason behind it is that you can verify that you are downloading from the correct site.

And apt-get update must be used with "sudo"

---

### Post by maryjanua on 2007-09-24
i did use sudo .........i said that but i dont understand what im sposed to do with that tux thingy

---

