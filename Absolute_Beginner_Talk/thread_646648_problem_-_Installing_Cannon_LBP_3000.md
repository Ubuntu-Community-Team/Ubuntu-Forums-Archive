---
title: "problem - Installing Cannon LBP 3000"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by taekr on 2007-12-21
For 2 days I have tried to make it work..  just can not..  

I went to [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900)
and tried the way..

also 

[http://ubuntuforums.org/showthread.php?t=134937&page=2](http://ubuntuforums.org/showthread.php?t=134937&page=2)

as well. 

when captstatusui -P LBP3000, 

I get this error message.. 

check the Device Path of /etc/ccpd.conf


what is the problem?  What can I do?   I reinstalled ubuntu 2 times becasue of this.. T T;;

Can't stand it anyrmoe..

---

### Post by dstew on 2007-12-21
What is the output of ccpdadmin?

---

### Post by taekr on 2007-12-21
Usage: 
  ccpdadmin [-p Printer-name -o Printer-dev-path]
  ccpdadmin [-x Remove-Printer-name]


 CUPS_ConfigPath = /etc/cups/
 LOG Path        = None
 UI Port         = 59787

 Entry Num  : Spooler   : Backend       : FIFO path             : Device Path  : Status 
 ----------------------------------------------------------------------------
     [0]    : LBP3000   : ccp           : /var/ccpd/fifo0       : /dev/usblp0  :

---

### Post by dstew on 2007-12-22
That seems right. The problem is that the ccpd program doesn't seem to be able to access its configuration file. The default location /etc/ccpd.conf either is not accessible (permissions are not correct) or the file is somewhere else (different path). Find the file using** locate ccpd.conf**Then look at the directory and file permissions.

---

### Post by citral on 2008-04-08
Also check that the name of your printer in the ccpd.conf matches the name of your printer in the CUPS configuration (printers.conf)

---

