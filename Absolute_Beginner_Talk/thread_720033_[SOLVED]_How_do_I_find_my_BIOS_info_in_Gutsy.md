---
title: "[SOLVED] How do I find my BIOS info in Gutsy"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by iansane on 2008-03-09
Hi, I am trying to find out my BIOS make and version so I can upgrade. Actually I want a backup copy of the rom  and any thing that goes with it. I have tried hwinfo, hardinfo, sysinfo, and system monitor. None of them show info about the BIOS. I haven't tried going into BIOS. It might tell me their, but is there a program for Gutsy that will display this info?

Also I am having a hard time getting any download from Pheonix technologies. They redirect me to esupport, who scans my computer and tells me they have an update but wants me to talk to a sales person/tech support and they want me to pay for updates. I though BIOS updates were usually free to download. Can anyone help me to get a copy of my BIOS update?

Thank you

---

### Post by hhhhhx on 2008-03-09
this might help

[http://www.cyberciti.biz/tips/querying-dumping-bios-from-linux-command-prompt.html](http://www.cyberciti.biz/tips/querying-dumping-bios-from-linux-command-prompt.html)

---

### Post by iansane on 2008-03-09
Cool thanks Xhhux. That got me the info. Now if I can just find a free download I'll be set.

---

### Post by iansane on 2008-03-09
Can anyone tell me how to extract my current bios image in Ubuntu or Windows. I can do either one. Will winflash do this? Not from a downloaded file but actually extract a copy from my ROM. I'm researching but any suggestions are appreciated.

---

### Post by iansane on 2008-03-09
Ah I think I found all the info I need and how to make a back up.

Here's something I found in case anyone else wants to check it out.

[http://freepctech.com/troubleshooting/tsb017.shtml](http://freepctech.com/troubleshooting/tsb017.shtml)

---

### Post by handy on 2008-03-09
If you know the make & model of your motherboard, you find it on the manufacturers site where you will be able to access the most recent BIOS & the software used to upgrade the on-board BIOS.  In this process you are given the option to make a backup of your existing BIOS, sometimes you are not even given the option, it is done automatically.

The software is windows centric, so you can use a floppy, though most modern motherboards now make it possible over the internet.

---

### Post by dcstar on 2008-03-10
> **iansane said:**
> Hi, I am trying to find out my BIOS make and version so I can upgrade. ........

System-Preferences-Hardware Information-Computer-Advanced has my BIOS info.

It is the hal-device-manager package.

---

### Post by iansane on 2008-03-11
Thanks you guys. I found the BIOS where you said in system>prefrenvced>hardware info>advanced. I'll reboot in windows and use c-puz for the mother board info. c-puz for linux would be awsome. :-)

---

### Post by Cannaregio on 2008-04-06
dmidecode is a great command, but  I prefer to port all lshw results to html instead.
Issue the command
```
sudo lshw -html >MyGNULinuxBox.html
```
and then use your browser.

---

### Post by scrime on 2008-04-06
Problem is if the flash goes wrong, you've got the bios image saved but your computer may not start.  This can be a mission.  Luckily most new motherboards have a bios backup facility, the have 2 bios chips and you can revert to the original if you have too.

---

