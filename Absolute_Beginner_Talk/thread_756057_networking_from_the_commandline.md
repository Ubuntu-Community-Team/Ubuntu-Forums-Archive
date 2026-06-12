---
title: "networking from the commandline"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by toddpedlar on 2008-04-15
Here's a sticky problem with which I am rather annoyed.

I was hoping to install nvidia-settings on my intel machine and when I did so, it uninstalled nvidia-glx - why, I don't know.

At any rate, when I rebooted after the install of nvidia-settings I had no operative xserver anymore.

So, I'm now stuck with a machine with no x11, and have to get nvidia-glx again ( I presume) to make the darn thing work again.  

Can anyone give me a quick lesson on connecting to my internet network from the command line so that I can get nvidia-glx from the repositories again?   I don't see any helpful information in the forums (but I've only looked for 10 minutes or so)

A second question - any reason that installing nvidia-settings should cause this problem?

Thanks,

Todd

---

### Post by blazercist on 2008-04-15
do you have a router or are you connected directly to the modem?  

either way if you have a router and it has dhcp or a modem with dhcp then you should just be able to do 

sudo dhclient eth0

and it should automagically setup your connection ... theoretically it should just work without doing anything.


if you dont have dhcp then you need your ip address (public or private depending on whether or not you have a router) your gateway address and the subnet mask address.  you can set this information by using sudo ifconfig
if you need more information on the ifconfig command you can check the man pages or just type ifconfig and itll give you a breakdown of the command options.

---

### Post by blazercist on 2008-04-15
actually stupid me, you probably dont even need the internet, the package itself shoudl still be in synaptics temp directory, so if you sudo apt-get install nvidia-glx it should just work anyway.

---

### Post by toddpedlar on 2008-04-16
I tried that first, which is why I then needed to ask about networking from the commandline - the claim was that it wasn't able to resolve http repositories.  It doesn't appear to have searched any synaptics temp directories though.  

still stuck...

---

### Post by OffAxis on 2008-04-16
what's 
```
ifconfig 
```
give you?

there's also 
```
sudo /etc/init.d/networking restart
```
which should yield a new ip as well.

---

### Post by prshah on 2008-04-16
> **toddpedlar said:**
> 
Can anyone give me a quick lesson on connecting to my internet network from the command line so Todd

Take a look at [http://ubuntuforums.org/showthread.php?t=756260](http://ubuntuforums.org/showthread.php?t=756260)

It specific to ndiswrapper but the commands (pure commandline) start to finish will act as a guide

---

### Post by toddpedlar on 2008-04-16
> **OffAxis said:**
> what's 
```
ifconfig 
```
give you?

there's also 
```
sudo /etc/init.d/networking restart
```
which should yield a new ip as well.

ifconfig shows my ethernet interfaces as expected.

I can do the restart, and have - the interface seems not to be connected, however, since
I can't telnet or ping - the issue isn't dns, but even telnetting to raw IP addresses gives me the "no route to host" thing.

Dead in the water....

---

### Post by northern lights on 2008-04-16
Can you simply post the outputs of ```
lshw -C network
```
and ```
route -n
``` and ```
cat /etc/network/interfaces
``` Thanks.

---

### Post by toddpedlar on 2008-04-16
> **northern lights said:**
> Can you simply post the outputs of ```
lshw -C network
```
and ```
route -n
``` and ```
cat /etc/network/interfaces
``` Thanks.

I could only do that by typing out 50 lines of text...

however interestingly enough /etc/network/interfaces only shows 

iface lo inet loopback
auto lo

for some reason - even though lshw -C network shows a lot, and route -n shows both wired and wireless interfaces with both showing "U"

Is there some specific info you want to see from those commands?  I really can't sit down and type out 50 lines of text

---

### Post by OffAxis on 2008-04-16
so dhcp is resolving properly?

the **route -n** command should show your default gateway; is that resolving properly?

try
w3m yahoo.com

why? because ping uses the ICMP ports and w3m uses port 80.

seems like you have more going on than just a blown xserver...

If the package is already on your system somewhere just go straight for the dpkg utility.

```
dpkg -l *nvidia*
```
will list all packages with nvidia in their name and package state. If it's partially installed you can run
```
sudo dpkg -C
```
to work something out.


If the .deb is still in the archives folder you can:

```
cd /var/cache/apt/archives
sudo dpkg -i nvidia-glx-new
```

you also have the option of downloading from another machine
```
sudo aptitude download nvidia-glx-new
```
which will download it to the present working directory
and then installing it with the
```
sudo dpkg -i nvidia-glx-new
```

You could check the liveCD to see if the package is on it (just cd into it from the terminal), or
boot the liveCD (which will hopefully get your GUI and network back temporarily) to do the downloading, and then reboot and install the package.

---

### Post by OffAxis on 2008-04-16
> however interestingly enough /etc/network/interfaces only shows

iface lo inet loopback
auto lo
The configuration file structure system-wide is being reconfigured. The main configuration file here, **/etc/network/interfaces**
is universal across the distributions, while system specific stuff (**configuration fragment files** I think is what they're officially called) is being doled out to sub-folders. If you go into the directory you'll see a number of sub-folders with .d extensions; for the networking stuff it's
```
ls /etc/network/

[COLOR="RoyalBlue"]if-down.d  if-post-down.d  if-pre-up.d  if-up.d[/COLOR]  interfaces
```

---

