---
title: "Progress, but still tethered to router"
date: 2006-03-11
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2006-03-11
Again, I want to thank all of the people who put up with my frustration in getting started with ubuntu, and my wireless device not being found. I have begun compiling what I hope to be a good reference tool for nOObs to be referred to. I'm building the page slowly, as I still have no wireless access, so I have to do it in spits and spurts. (By the way, my fear of the terminal is not paralyzing anymore)
(How do I get the code box you guys always have in your posts?)

I went back through the posts in my previous thread, and followed the directions I could, but there is still something I'm missing. So far, this is what I think is right:
john@laptop:~$ sudo ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present

This is what I had trouble getting to.

Now, this is what I did, and I think I might have screwed something up in here, Please take a look..
Code:

sudo cp /etc/network/interfaces /etc/network/interfaces_bak sudo gedit /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map wlan0
	map eth0

# The primary network interface
iface wlan0 inet static
wireless_keymode open
wireless_mode managed
wireless_nick laptop
address 192.168.1.124
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid Rage
wireless-key open





iface eth0 inet static
address 192.168.1.123
netmask 255.255.255.0
gateway 192.168.1.1









auto eth0

---

### Post by LordCrank on 2006-03-11
are you on dapper?  if so

```
lsmod | less
```
should show you the modules that are loaded, look for one labeled "bcm43xx".  if that module is being loaded it will cause ndiswrapper problems, you can stop it from loading by blacklisting it, i.e. adding the line
```
blacklist bcm43xx
```
to /etc/modprobe.d/blacklist (must be edited with sudo)

as for getting the code box, use the word code in []'s

---

### Post by Papa-san on 2006-03-12
[QUOTE=LordCrank]are you on dapper?  if so

```
lsmod | less
```
should show you the modules that are loaded, look for one labeled "bcm43xx".  if that module is being loaded it will cause ndiswrapper problems, you can stop it from loading by blacklisting it, i.e. adding the line
```
blacklist bcm43xx
```
to /etc/modprobe.d/blacklist (must be edited with sudo)

as for getting the code box, use the word code in []'s[/QUOTE]

I am not sure if it is dapper or not... how to check?
Also, when I ran that command, there was no bcm43xx in the list.

---

### Post by kaamos on 2006-03-12
[QUOTE=Papa-san]I am not sure if it is dapper or not... how to check?[/QUOTE]
You most likely are not. You can use "cat /etc/issue" to check. Breezy is the current release and dapper is in developement.

[QUOTE=Papa-san](How do I get the code box you guys always have in your posts?)[/QUOTE]
Type [_code]blaablaa[/code] without the underscore(_)

---

### Post by Papa-san on 2006-03-12
```
yadayada
```
Cool!, that worked!
I have Breezy.

---

### Post by Papa-san on 2006-03-12
How does something like this happen?
Is it telling me two different things?:
john@laptop:~$ sudo ndiswrapper -i /home/johnstone/drivers/bcmwl5.inf
bcmwl5 is already installed. Use -e to remove it
john@laptop:~$ sudo modprobe -r bcmwl5
FATAL: Module bcmwl5 not found

---

### Post by kaamos on 2006-03-12
Ndiswrapper is telling you that you have installed the bcmwl5 windows driver for *ndiswrapper*. Modprobe -r means "unload this kernel module", so it is looking for a different thing because ndiswrapper uses the module "ndiswrapper".

So you should not worry about the second error, it just tells you that there is no point in removing something that is not there. The first error tells that you already have the driver that you are trying to install. If you are trying to install a newer version, you should do
```
sudo ndiswrapper -e bcmwl5
```
and the try the install ("-i") again.

---

### Post by Papa-san on 2006-03-12
Nope, that is the most current driver. I'm just pretty convinced I have screwed something up elsewhere.
tried this too:```
john@laptop:~$ for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
> sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
> done
bash: /etc/ndiswrapper/bcmwl5/14E4:4318:1028:0005.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4318:1028:0006.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4318.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4319:1028:0005.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4319:1028:0006.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4319.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:1028:0001.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:1028:0002.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:1028:0003.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320:1028:0004.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4320.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:1028:0001.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:1028:0002.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:1028:0003.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324:1028:0004.5.conf: Permission denied
bash: /etc/ndiswrapper/bcmwl5/14E4:4324.5.conf: Permission denied
```

---

