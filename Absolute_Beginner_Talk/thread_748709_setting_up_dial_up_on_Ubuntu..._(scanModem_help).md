---
title: "setting up dial up on Ubuntu... (scanModem help)"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by GhostbustThat on 2008-04-07
after I went to [http://linmodems.org]("http://linmodems.org") and downloaded the scanModem tool, I followed the steps here ([http://132.68.73.235/linmodems/first.html]("http://132.68.73.235/linmodems/first.html")).

after I ran the commands in a terminal an error i didn't quite understand showed up... here is all the text I entered in the terminal, I hope someone can help...
--------------------------------------------------------------
shawn@GhostbustThat:~$ cd Documents
shawn@GhostbustThat:~/Documents$ gunzip scanModem.gz
shawn@GhostbustThat:~/Documents$ chmod +x scanModem
shawn@GhostbustThat:~/Documents$ sudo ./scanModem
[sudo] password for shawn:
Sorry, try again.
[sudo] password for shawn:
UPDATE=2008_04_06
 Continuing as this update is a only 0 weeks old,
 but the current Update is always at: [http://linmodems.technion.ac.il](http://linmodems.technion.ac.il)


Identifying PCI bus slots with candidate modems.
Running PCIbus cases
Analysing card in PCI bus 00:02.6, writing to scanout.00:02.6

 Please load the candidate driver snd-intel8x0m, with Admin/root command:
        sudo modprobe snd-intel8x0m
 Then rerun 
        ./scanModem

---

### Post by mgranet on 2008-04-07
[http://linmodems.technion.ac.il/Read.scanModem/YourSystem.txt](http://linmodems.technion.ac.il/Read.scanModem/YourSystem.txt)

This might be a good start.

---

