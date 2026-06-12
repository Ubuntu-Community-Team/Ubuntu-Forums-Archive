---
title: "how do I run this script"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by the_tiger on 2006-05-06
I have this script
```
#!/bin/bash
interface=wlan0 # fill in whatever your interface is here it should typically be eth1
# Turning off other network devices"
sudo ifconfig eth0 down # assumes you have a wired NIC remove if you don't have one
sudo modprobe bcm43xx
# setting wireless device parameters
sudo ifconfig $interface up # This step is very very important!
sudo iwconfig $interface essid your_essid_here
sudo iwconfig $interface mode managed 
# sudo iwconfig $interface mode auto # another suggested mode
#sudo iwconfig $interface key off # see man iwconfig for wireless encrpytion
"Setting up dhcp"
sudo dhclient $interface

```

how do I run it?

Secondly how do I get it to run at startup?

---

### Post by ds[de] on 2006-05-06
To run it, just open a terminal, and type (after chmod'ing it -> (sudo) chmod +x file)
./filename

e.g. if the file is script.sh, type
./script.sh

I don't know about the autostart though.

//edit: Or you could just double-click it and when asked whether to view or execute the file, choose execute.

---

### Post by dermotti on 2006-05-06
or **sh script.sh**

---

### Post by aysiu on 2006-05-06
Go to a terminal and copy and paste these commands: ```
gksudo gedit /usr/local/bin/wlanscript
``` in Gnome or ```
kdesu kwrite /usr/local/bin/wlanscript
``` in KDE. In the newly opened text editor window, paste in the code you posted here. Then save and exit the text editor. ```
sudo chmod +x /usr/local/bin/wlanscript
``` Then go to startup programs. I believe this lives in System > Preferences > Sessions in Gnome. I'm going to have to poke around in KDE to find where that is. Just add the command ```
wlanscript
``` to the list of startup programs.

**Edit**: actually, I just realized your script invokes *sudo* in the terminal, so adding it to the startup programs probably won't work.

These threads may help, though:
[http://www.ubuntuforums.org/showthread.php?t=170111](http://www.ubuntuforums.org/showthread.php?t=170111)
[http://www.ubuntuforums.org/showthread.php?t=13229](http://www.ubuntuforums.org/showthread.php?t=13229)
[http://www.ubuntuforums.org/archive/index.php/t-33615.html](http://www.ubuntuforums.org/archive/index.php/t-33615.html)

---

