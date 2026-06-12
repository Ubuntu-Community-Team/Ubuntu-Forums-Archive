---
title: "gpilot-install-file with multiple devices"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by jim1964 on 2007-12-26
I have two palm devices, a Treo 700p and a TX. I have set up profiles and activated the backup and file install conduits for both. Both devices sync fine. But I can only install files to one of the devices with gpilot-install-file. I even disabled the backup and file install conduits for the first device. But still no luck with the second. How can I tell gpilot-install-file which device to install files to? It must be hard coded in some file but I can't find it. Thanks in advance for your help.

---

### Post by himikeb on 2008-02-02
Hah!  I think I got it..  Broke out hex edit and looked through the gpilot-install-file binary.
It's a shame they don't document this in the Man file.
First, use gpilot-install-file --help   - The answer IS there..

gpilot-install-file --now --pilot=MyZire *.prc
where MyZire is the NAME of your PDA.  Seems to always frickin' default to the first PDA you registered.
I assume --later would work, too..

Then Sync, sit back, and enjoy your newly-installed software!!

---

