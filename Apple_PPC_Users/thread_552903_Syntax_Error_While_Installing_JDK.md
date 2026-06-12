---
title: "Syntax Error While Installing JDK"
date: 2007-09-17
forum: Apple PPC Users
---

### Post by Monster Eats the Baby on 2007-09-17
I recently installed Ubuntu 7.04 on a PowerBook G4. I'm trying to install JDK6 so I can begin programming on my computer. I downloaded the .bin from java.sun.com and tried to install it following the instructions [here]("http://java.sun.com/j2se/1.5.0/install-linux.html"). (Yeah, it's for 5.0, not 6, but the instructions seem like they should be the same. Also, I've tried 5 and gotten the same results.) When I enter ```
sudo ./jdk-1_5_0_12-linux-i586-rpm.bin
``` I get a license agreement and then
```
Unpacking...
Checksumming...
Extracting...
./install.sfx.17957: 1: Syntax error: "(" unexpected
Failed to extract the files.  Please refer to the Troubleshooting section of
the Installation Instructions on the download page for more information.

```
The number after "install.sfx." bounces around, but the error message remains the same. Installing with the .rpm gets me the same message. Can anyone here help out?

---

### Post by bodek on 2007-09-17
I think Sun's java is only for intel processors.
If you want java for PPC you better go with IBM. The [ubuntu wiki]("https://help.ubuntu.com/community/Java") shows in few steps how to get it and install.
Hope it will work for you.

---

