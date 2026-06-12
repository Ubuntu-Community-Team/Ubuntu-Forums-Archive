---
title: "What Does This Fax Error Mean?"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by LearningPerson on 2008-01-03
Hello, I am trying to run Efax-gtk with GutsyGibbon and received the following error:

warning: ignoring zlib error: incorrect data check
efax-0.9a: 13:31:16 opened /dev/ttyS1
efax-0.9a: 13:31:16 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 13:31:16 failed page /home/sharon/instruct.ps.001
efax-0.9a: 13:31:17 Error: fax device write: Input/output error
efax-0.9a: 13:31:19 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 13:31:21 Error: fax device write: Input/output error
efax-0.9a: 13:31:23 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 13:31:23 sync: dropping DTR
efax-0.9a: 13:31:23 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 13:31:23 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 13:31:25 Error: fax device write: Input/output error
efax-0.9a: 13:31:27 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 13:31:27 Error: fax device write: Input/output error
efax-0.9a: 13:31:27 Error: fax device write: Input/output error
efax-0.9a: 13:31:27 sync: sending escapes
efax-0.9a: 13:31:27 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 13:31:27 Error: fax device write: Input/output error
efax-0.9a: 13:31:27 Error: fax device write: Input/output error
efax-0.9a: 13:31:29 Error: fax device write: Input/output error
efax-0.9a: 13:31:31 Error: fax device write: Input/output error
efax-0.9a: 13:31:33 Error: sync: modem not responding
efax-0.9a: 13:31:33 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 13:31:33 finished - unrecoverable error

Typing "lspci" in the terminal gives me an HSP Micromodem 56 v.2 and my purchase papers list: HSP56 Wdm.  I have tried a few sites but am hoping for one I can understand.  Thanks.

---

### Post by LearningPerson on 2008-01-04
Here's what I've done so far:

#1 Went to:  [http://132.68.73.235/linmodems/index.html#scanModem](http://132.68.73.235/linmodems/index.html#scanModem)
and downloaded scanModem to the Desktop

#2 Went to: [https://help.ubuntu.com/community/DialupModemHowto/ScanModem](https://help.ubuntu.com/community/DialupModemHowto/ScanModem)
It is not necessary to type a $; there IS a space after cd
$ cd ~/Desktop
 $ gunzip scanModem.gz
 $ chmod +x scanModem
 $ ./scanModem
Read what comes up then:
cd ~/Desktop
ls Modem/
less Modem/1stRead.txt

Whole bunch of files same as above came up again.  I read then typed:

cd ~/Desktop
less Modem/ModemData.txt
I read this and at the colon   :   HAD TO KEEP PRESSING RETURN to go way down and find my modem. DO NOT STOP UNTIL YOU SEE Completed candidate modem analyses.

I found this info: 
 For candidate modem in PCI bus:  01:0a.0

   Class 0703: 134d:7897 Modem: PCTel Inc HSP MicroModem 56

      Primary PCI_id  134d:7897

 Support type needed or chipset:        PCTEL

 
----------------end Softmodem section --------------

    At [http://linmodems.technion.ac.il/pctel-linux](http://linmodems.technion.ac.il/pctel-linux)

 Get the pctel-0.9.7-9-rht-8.tar.gz

 Unpack under Linux with:

    tar zxf pctel*.tar.gz

 and read instuctions therein.

  Read Pctel.txt and Modem/YourSystem.txt for follow through guidance.


 Writing Pctel.txt


 Completed candidate modem analyses.

---

### Post by YCW on 2008-01-23
Hi there Learning Person
I too am facing your same problem. Just like to asked if your fax is working already? If yes, do you mind to help me. PLS

Many thanks in advance:popcorn:

---

### Post by YCW on 2008-01-23
Oops...Sorry, i forgot to mentioned i did the same steps you mentioned from linmodems.org but it is still not working for me yet.

---

### Post by caravel on 2008-01-23
You're using an internal winmodem?  You'd be way better off with an external serial modem if you can get one for cheap.

---

### Post by rosegarden78 on 2008-02-07
Hey I have WinModem same errors and just used whole partition for Ubuntu!  I wonder if I can use my VirtualBox XP instead?  That was a nice feature having the fax/modem work though.

---

