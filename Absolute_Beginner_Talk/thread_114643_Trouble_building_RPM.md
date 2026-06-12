---
title: "Trouble building RPM"
date: 2006-01-09
forum: Absolute Beginner Talk
---

### Post by lindejos on 2006-01-09
I'm having trouble building the rpm tool so I can install the jre.  I did an apt-get install rpm and then I tried to use rpm to unbundle the file I got from sun.

root@homebrew:/home/lindejos/AdobeReader# rpm -i  lindejos/Desktop/jre-1_5_0_01-linux-i586-rpm.bin

/home/lindejos/Desktop/jre-1_5_0_01-linux-i586-rpm.bin: read manifest failed: Success

Any ideas out there?

---

### Post by aysiu on 2006-01-09
[Why do you need to install an RPM?](https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249)

---

### Post by lindejos on 2006-01-09
Never mind I figured it out

RPM is for redhat, i just went and got the .bin file and ran it at the command line.

Still new, trying not to be too stupid.

Thanks for quick response.

---

