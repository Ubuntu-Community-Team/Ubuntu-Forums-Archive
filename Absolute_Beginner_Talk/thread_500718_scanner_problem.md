---
title: "scanner problem"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by nichanson on 2007-07-14
Hi
Can anyone make a suggestion what I should do, xsane says I haven't a scanner when it clearly says I have in the device list!!!:

hanson@hanson-desktop:~$ lsusb
**Bus 003 Device 011: ID 04a9:2210 Canon, Inc. CanoScan 9900F**
Bus 003 Device 010: ID 0789:0140 Logitec Corp. 
Bus 003 Device 008: ID 04b4:0101 Cypress Semiconductor Corp. 
Bus 003 Device 004: ID 0461:4d03 Primax Electronics, Ltd Kensington Mouse-in-a-box
Bus 003 Device 006: ID 05e3:070e Genesys Logic, Inc. 
Bus 003 Device 003: ID 05e3:0606 Genesys Logic, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 03eb:3301 Atmel Corp. at43301 4-port Hub
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
hanson@hanson-desktop:~$ scanbuttond -r 1000000
hanson@hanson-desktop:~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
hanson@hanson-desktop:~$ scanimage -T -d
scanimage: no SANE devices found
hanson@hanson-desktop:~$ xsane

---

### Post by the.phantom on 2007-07-14
is your scanner on this list?
[http://www.sane-project.org/sane-supported-devices.html](http://www.sane-project.org/sane-supported-devices.html)

---

