---
title: "How to load old Xorg.log ?"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by gingin on 2007-03-19
[COLOR="Black"][/COLOR]

Just today have installed Ubuntu in to mine laptop and already  have managed to crash mine monitor.You know usual problems installing Ati Redeon drivers.

How to get back default  values ? 
Seams as original default file know is /var/log/Xorg.0.log 

Thanks for help

---

### Post by annda on 2007-03-19
this is just a log file (configuration is in /etc/X11/xorg.conf). did you do a back up? if not, reconfigure X from the terminal:
sudo dpkg-reconfigure xserver-xorg

---

### Post by chili555 on 2007-03-19
This file is a log of the steps that have been taken to load your Xserver, not a backup copy of your old file. You can inspect it by opening a terminal and issuing the command: ```
less /var/log/Xorg.0.log
```The command less allows you to scroll back and forth through the file and look for EE indicating an error occurred.

You might also issue the command:```
 sudo dpkg-reconfigure -phigh xserver-xorg
```That's a bit risky, but may be better than no X-server and no other options. It will allow you to change parameters and write the changes to a new xorg.conf file and, hopefully, restart.

You can back up any configuration file by:```
sudo cp /etc/file_you_want_to_back_up /etc/file_you_want_to_back_up.bak
```Then, if disaster strikes, you just reverse the command and you are back in business.

---

### Post by gingin on 2007-03-20
Thanks guys I´m going to do that. We wil see about result.
How to restore that * bac file after I have back it up?

---

### Post by chili555 on 2007-03-20
Just reverse the process:```
sudo mv /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```If you want to go messing about with any configuration file, and you are the least bit unsure about the outcome, it makes sense to first back up the known working file. For example,```
sudo cp /etc/modules /etc/modules.bak
```Then if you make a mistake, you can always move (mv) the bak in replacement of the file that got modified incorrectly.

---

### Post by gingin on 2007-03-20
Thanks a lot Chili, all advises have worked like  with butter.

Using sudo dpkg-reconfigure -phigh xserver-xorg wast risky at all worked really god.

---

### Post by chili555 on 2007-03-21
Glad it worked well for you. Have fun with Ubuntu!

---

