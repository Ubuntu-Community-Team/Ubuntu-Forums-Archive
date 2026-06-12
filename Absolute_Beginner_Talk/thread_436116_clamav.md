---
title: "clamav"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by phil66 on 2007-05-07
Ubuntu Dapper Drake

Downloaded the following files from synpatic

clamav
libclamav-1
clamav-base
clamav-freshclam
arj
unzoo
clamav-daemon
clamtk

All files show to be installed 
Cannot open clamav from terminal or alt F2 getting file not found

Followed instructions at money blog with no success.

Clamtk will open from terminal and scan files

How do I open clamav so I can configure for scanning e-mail

Thanks 
Ray

---

### Post by Skrynesaver on 2007-05-07
Hi Ray,

ClamAV is a large and complex package.  This link should provide all the documentation you will need [http://www.clamav.net/doc/latest/html/node1.html](http://www.clamav.net/doc/latest/html/node1.html)

---

### Post by phil66 on 2007-05-07
Thanks for the reply and link

I have everything download from the repositories

I can change directories 

I can change permissions

But I cannot open clamav???

What do I need to type in the terminal to open clamav

Ray

---

### Post by BadSquishy on 2007-05-15
clamav is a command line virus scanner.  To scan something interactively from the command line use the clamscan command, for more info on clamscan check out the man page.  

For example I've installed the clamav-testfiles package so I have files to scan that will give me a positive result.  To have clamav scan the directory where the test files are installed I ran the following command, here is my output:
```
dave@linserver1:~$ clamscan /usr/share/clamav-testfiles/
LibClamAV Warning: ********************************************************
LibClamAV Warning: ***  This version of the ClamAV engine is outdated.  ***
LibClamAV Warning: *** DON'T PANIC! Read http://www.clamav.net/faq.html ***
LibClamAV Warning: ********************************************************
LibClamAV Warning: ********************************************************
LibClamAV Warning: ***  This version of the ClamAV engine is outdated.  ***
LibClamAV Warning: *** DON'T PANIC! Read http://www.clamav.net/faq.html ***
LibClamAV Warning: ********************************************************
/usr/share/clamav-testfiles/clam-error.rar: RAR module failure
/usr/share/clamav-testfiles/debugm.c: OK
/usr/share/clamav-testfiles/clam.cab: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam.exe.bz2: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam.exe: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam.rar: ClamAV-Test-File FOUND
/usr/share/clamav-testfiles/clam.zip: ClamAV-Test-File FOUND

----------- SCAN SUMMARY -----------
Known viruses: 93233
Engine version: 0.88.4
Scanned directories: 1
Scanned files: 7
Infected files: 5
Data scanned: 0.00 MB
Time: 2.910 sec (0 m 2 s)
```

The warnings at the beginning are because the package available in Dapper Universe is version 0.88.4, the current stable version available from [www.clamav.net](www.clamav.net) is 0.90.2.  

There is also a way to have clamav run as a daemon (clamd) but I haven't figured this out yet.  

Hope this helps, 

Regards,

---

