---
title: "Ubuntu on Vmware"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by cflint on 2006-04-04
Hi,

I'm having an issue once I install Ubuntu on VMware (running on Windows 2003).

I install ok, (server only, so no graphics) and then run the VMware tools install.

Once it's finished I am told to run a few commands which I can't remember at present (getting old) but goes something along the lines of:-

stop the network
unload pcnet32
unload vmxnet
scan
load vmxnet
start network.

This works a treat and the network starts responding to network traffic.

My problem is that when I restart Ubuntu, I ave no network again. According to the messages that fly off the screen during the boot, the machine is loading pcnet32 early on, and when vmware tools starts it's unable to connect the network (vmxnet) as pcnet32 already has control.

So,........ How do I stop the machine from loading pcnet32?

Cheers

Clive

---

### Post by izmaelis on 2006-04-04
To stop some module from loading on startup you should do
```
sudo nano /etc/modprobe.d/blacklist
```
and add such lines as
```
# modules to blacklist 
blacklist pcnet32
```
in your case.

---

### Post by cflint on 2006-04-07
Cheers for that, will try it when I get home.

Clive

---

### Post by cflint on 2006-04-07
Fantastic! It no longer loads the pcnet32 driver.

Bad news is I STILL have to run the commands to get the network to start.
/etc/init.d/networking stop
rmmod pcnet32
rmmod vmxnet
depmod -a
modprobe vmxnet
/etc/init.d/networking start 

No wonder people stay with MS! ](*,) 

What do I need to do now?

---

### Post by mat79 on 2006-04-07
same here... i'm just trying to get it to work...

btw: i have installed a newer kernel version (no idea if this is important or not)

after typing 
/etc/init.d/networking stop
rmmod pcnet32
rmmod vmxnet
depmod -a
modprobe vmxnet
/etc/init.d/networking start

everything works fine, but before this i dont even have a eth0... just lo

and writing 
# modules to blacklist 
blacklist pcnet32

into /etc/modprobe.d/blacklist (the file didnt exist, i created it) didnt stop pcnet32 from beeing loaded... 
rmmod pcnet32 works the first time and the second time it tells me that pcnet32 isnt loaded, so i guess pcnet32 is loaded on boot time

btw: i've installed Ubuntu in VMWare Server Beta 2 under WinXP SP2

---

### Post by mat79 on 2006-04-08
i think i found it:

just add 
```

auto eth0

```
to /etc/networking/interfaces
and it works (at least here)

---

### Post by cflint on 2006-04-10
Hey! It worked!!!!

Ah, the heady days of getting a problem solved. Think there are going to be a few more of those ahead.

---

