---
title: "Trouble instaling Skype in amd64"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by abbrew on 2006-09-02
I am having trouble installing Skype on my Dapper 64-bit computer.  I tried the force architecture command, but that sent back some error messages. Something about dependency problems and leaving unconfigured.  I'm not sure what to do about that. Here is the terminal:

alex@alex-desktop:~$ sudo dpkg -i --force-architecture skype_1.2.0.18-2_i386.debdpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 77687 files and directories currently installed.)
Preparing to replace skype 1.2.0.18-2 (using skype_1.2.0.18-2_i386.deb) ...
Unpacking replacement skype ...
dpkg: dependency problems prevent configuration of skype:
 skype depends on libstdc++5 (>= 1:3.3.4-1); however:
  Package libstdc++5 is not installed.
dpkg: error processing skype (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 skype
alex@alex-desktop:~$

---

### Post by macdo on 2006-09-02
You could maybe try installing from the bz archive: [http://www.skype.com/go/getskype-linux-dynamic](http://www.skype.com/go/getskype-linux-dynamic)

HTH, at let us know - i have an AMD 64 too, and I need to install Skype on it soon...

---

