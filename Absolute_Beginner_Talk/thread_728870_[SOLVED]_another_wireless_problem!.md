---
title: "[SOLVED] another wireless problem!"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by kamitsukai on 2008-03-19
ive installed my wireless driver with ndiswrapper but i cant configue it because it's not an option see thumnail below

---

### Post by chucky chuckaluck on 2008-03-19
check - [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,troubleshooting/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,troubleshooting/)

it looks like you should run *ndiswrapper -l* in the terminal to make sure the windows driver is properly installed.

---

### Post by kamitsukai on 2008-03-19
Hmmm followed part of that troubleshooting site but it appears to be installed properly maybe ubuntu wireless isnt enabled? as there is no option to select it? anyway this is my output:
```
carl@carl-desktop:~$ sudo ndiswrapper -l
netmw225 : driver installed
        device (1286:1FAB) present
carl@carl-desktop:~$ ndiswrapper -l dmesg | grep ndiswrapper
install/manage Windows drivers for ndiswrapper
usage: ndiswrapper OPTION
carl@carl-desktop:~$ 
```

---

### Post by alan34 on 2008-03-19
Has ndiswrapper been loaded to the kernal ? Go in a terminal

lsmod

and look for ndiswrapper

edit /etc/modules and at the end on a line on its own add

ndiswrapper

save and restart the pc

---

### Post by kamitsukai on 2008-03-19
> **alan34 said:**
> Has ndiswrapper been loaded to the kernal ? Go in a terminal

lsmod

and look for ndiswrapper

edit /etc/modules and at the end on a line on its own add

ndiswrapper

save and restart the pc

i cant find ndiswrapper in that list it brings up?

***edit***
oh i see i need to edit a file called modules in the folder etc? so how do i do that? (Me=Noob)

---

### Post by alan34 on 2008-03-19
You need after installing ndiswrapper have to done the following commands in a terminal

sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m

See ndiswrapper when you do?

lsmod

to edit the file

sudo gedit /etc/modules

Think it is kate not gedit in kubuntu

---

### Post by kamitsukai on 2008-03-19
yep i can see ndiswrapper! lol now what? :P

---

### Post by kamitsukai on 2008-03-19
it works!!!!! thankyou soooooo much your a godsend :P

---

