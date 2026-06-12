---
title: "[SOLVED] Printing on a Canon LBP2900 printer shared by Windows"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by martinr on 2008-04-02
HOWTO configure Ubuntu Dapper to print to a Canon LBP2900 printer shared by Windows:

I've been struggling with this for a while and now that I've solved it, I wanted to share it with you (with the 1.30 drivers it didn't work yet).

1)
Download the linux drivers from Canon support:
CAPTDRV160.tar.gz
Canon CAPT Printer Driver for Linux (1.60) (with the 1.30 drivers it didn't work yet)
[http://software.canon-europe.com/products/0010177.asp](http://software.canon-europe.com/products/0010177.asp)

2)
Unpack it:
```
tar -xvzf CAPTDRV160.tar.gz
```

3) 
Install the two .deb packages cndrvcups-common_1.60-1_i386.deb and cndrvcups-capt_1.60-1_i386.deb as root:

```
root@avalon:/var/tmp/ToInstall/LBP2900-CUPS-Linux/Versie160/CAPTDRV160/driver/debian# dpkg -i cndrvcups-common_1.60-1_i386.deb 
Selecting previously deselected package cndrvcups-common.
(Reading database ... 96396 files and directories currently installed.)
Unpacking cndrvcups-common (from cndrvcups-common_1.60-1_i386.deb) ...
Setting up cndrvcups-common (1.60-1) ...

root@avalon:/var/tmp/ToInstall/LBP2900-CUPS-Linux/Versie160/CAPTDRV160/driver/debian# dpkg -i cndrvcups-capt_1.60-1_i386.deb 
Selecting previously deselected package cndrvcups-capt.
(Reading database ... 96445 files and directories currently installed.)
Unpacking cndrvcups-capt (from cndrvcups-capt_1.60-1_i386.deb) ...
Setting up cndrvcups-capt (1.60-1) ...
```

4)
Restart CUPS:
```
root@avalon:/var/tmp/ToInstall/LBP2900-CUPS-Linux/Versie160/CAPTDRV160/driver/debian# /etc/init.d/cupsys restart
 * Restarting Common Unix Printing System: cupsd                         [ ok ] 
```

For network printing purposes the driver works now, no additional steps required. (However the install manual goes on! to setup for spooler for direct connection of the printer to a laptop, but that is not necessary in our case.)

5)
Now you can configure a Windows shared network printer from the Gnome Desktop:
```
System -> Administration -> Printing
```  
In the dialog select New Printer -> network printer (Windows Printer smb) ->
select host and the shared printer on that host and you're done.

Happy printing!

Note:
(This might also work for other drivers contained in the same package, but this is not tested:
  i-SENSYS LBP2900  
  i-SENSYS LBP3000  
  Laser Shot LBP-1120  
  Laser Shot LBP-1210  
  Laser Shot LBP2900  
  Laser Shot LBP3000  
  Laser Shot LBP3300  
  LBP-3200  
  LBP5000  
  LBP5100  
  LBP5300  
)

Warning!
DPKG can mess up your system. 
If your dpkg fails, the package can be unpacked but not configured. That really can bugger your computer up.
apt-get -f install
pulls in all unsatisfied dependancies or removes the offending package(s)

---

