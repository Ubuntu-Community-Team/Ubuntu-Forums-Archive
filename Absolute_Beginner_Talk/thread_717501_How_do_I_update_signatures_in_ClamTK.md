---
title: "How do I update signatures in ClamTK?"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by bwallum on 2008-03-07
Hi

Just in case i thought I would familiarise myself with a Linux antivirus programme and found ClamTK. It appears to be ok but I cannot see how to update signatures. Does it use a repository? Does it require a PGP key?

If anybody has experience with this could they pass it on please.

Regards
Bob

---

### Post by etusha on 2008-03-07
try 
sudo clamtk
go to help and go to Update

---

### Post by JK21 on 2008-03-07
> **bwallum said:**
> Just in case i thought I would familiarise myself with a Linux antivirus programme and found ClamTK. It appears to be ok but I cannot see how to update signatures. Does it use a repository? Does it require a PGP key?


You don't need pgp. Use 'sudo freshclam' in a terminal to update signatures.

If you get a warning that your programversion is outdated just follow the instruction how to update. There's a repository in the link you need to go to...

---

### Post by hyper_ch on 2008-03-07
you know, all that AV on linux does is scan for windows viruses?

---

### Post by bwallum on 2008-03-07
I did that with an interesting response:-

bob@bob-desktop:~$ sudo freshclam
[sudo] password for bob:
ClamAV update process started at Fri Mar  7 12:59:20 2008
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.91.2 Recommended version: 0.92.1
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
main.inc is up to date (version: 45, sigs: 169676, f-level: 21, builder: sven)
daily.inc is up to date (version: 6161, sigs: 56165, f-level: 26, builder: ccordes)
bob@bob-desktop:~$ 

Thanks!

However when I went to the website and ran the debian install (sudo apt-get install clamav) I was told I already had the latest version!

---

### Post by bwallum on 2008-03-07
Thanks etusha. It appears to just updated!

---

### Post by bwallum on 2008-03-07
Is that right, I didn't know that. So I can use ClamTK to scan a possibly infected Windows drive? Thats very useful when repairing other machines.

---

### Post by hyper_ch on 2008-03-07
yes, AV on linux is used for two things:

(1) clean viruses from fileservers / email servers

(2) clean viruses from windows computers / partitions

btw, there are about 40 known viruses for linux - none of them is running in the wild and about 60'000 known viruses for windows.

---

