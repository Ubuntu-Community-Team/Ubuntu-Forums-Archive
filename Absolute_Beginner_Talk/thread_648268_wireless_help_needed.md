---
title: "wireless help needed"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by darkeale on 2007-12-23
hey all, i used this guide to setup my wireless

[http://ubuntuforums.org/showthread.php?t=644899&highlight=wireless+amilo](http://ubuntuforums.org/showthread.php?t=644899&highlight=wireless+amilo)

what now? what program do i use to search or connect to a wireless network?

cheers

alex

---

### Post by Josdell on 2007-12-23
Should be working now. There SHould be a computer icon in the top right corner click it.

---

### Post by bwhite82 on 2007-12-23
Network manager applet

---

### Post by darkeale on 2007-12-23
hmmm i dont have an icon in the top right. maybe it didnt setup properly. is there anywhere to check if its properly set up?

---

### Post by bwhite82 on 2007-12-23
> **darkeale said:**
> hmmm i dont have an icon in the top right. maybe it didnt setup properly. is there anywhere to check if its properly set up?

ifconfig

It should show you eth0 and eth1

---

### Post by darkeale on 2007-12-23
> **Soldierboy said:**
> ifconfig

It should show you eth0 and eth1

i get eth0 and lo. so its not properly configured then?

---

### Post by bwhite82 on 2007-12-23
You should see both eth1 and eth0 if you have both a Wired and Wireless NIC in your computer (properly configured). If you do indeed have both, then most likely only your Wired NIC is configured.

The command: lsmod will tell you which kernel modules are currently loaded, you should see your wireless module there (acerhk), if not, then you need to modprobe it: modprobe acerhk

 What exactly did you do to configure your wireless?

---

### Post by darkeale on 2007-12-23
> **Soldierboy said:**
> You should see both eth1 and eth0 if you have both a Wired and Wireless NIC in your computer (properly configured). If you do indeed have both, then most likely only your Wired NIC is configured.

The command: lsmod will tell you which kernel modules are currently loaded, you should see your wireless module there, if not, then you need to modprobe it. What exactly did you do to configure your wireless?

i followed this guide cause i also have an amilo 1718


[http://ubuntuforums.org/showthread.p...wireless+amilo](http://ubuntuforums.org/showthread.p...wireless+amilo)

the wireless button on the key pad works now but apparently thats all that guide did. 

so where do i go from here?

---

### Post by darkeale on 2007-12-23
i just tried this guide too and still nothing,  

[http://ubuntuforums.org/showthread.php?t=546451&highlight=amilo+1718+wireless](http://ubuntuforums.org/showthread.php?t=546451&highlight=amilo+1718+wireless)

the light on the laptop comes on indicating that the wireless is on when the wireless key is pressed but ifconfig still doesnt show it

any more suggestions?

also when i run lsmod, acerhk is there

---

### Post by darkeale on 2007-12-23
it wouldnt matter that im using ubuntu studio does it? cause whenever adding something to the modules section ie lib/modules/2.6.22-14-generic i have to change it to lib/modules/2.6.22-14-rt because of the different kernal i think. would this effect the setup?

---

### Post by bwhite82 on 2007-12-23
> **darkeale said:**
> it wouldnt matter that im using ubuntu studio does it? cause whenever adding something to the modules section ie lib/modules/2.6.22-14-generic i have to change it to lib/modules/2.6.22-14-rt because of the different kernal i think. would this effect the setup?

You definitely want your modules to match your kernel. Its odd that you say you see the module loaded but its not working.....

I remember spending hours trying to get my wireless working, when it was working the whole time, it was simply disabled by dell's hotkeys. Did you try that? Is there a button on your computer to enable wireless? Try hitting it.

---

### Post by darkeale on 2007-12-23
yeah i hit the key and the light on the laptop comes on, but thats all that happens. as far as i can see ubuntu doesnt realise its on

---

### Post by xc3RnbFO8P on 2007-12-23
> **darkeale said:**
> yeah i hit the key and the light on the laptop comes on, but thats all that happens. as far as i can see ubuntu doesnt realise its on

You could  try this:


sudo depmod -a
password: 

sudo modprobe -r acerhk
sudo modprobe acerhk poll=1 autowlan=1

then, Fn + wireless button.

---

### Post by darkeale on 2007-12-25
the buttons works fine, i just made a partition to see if itll work on a generic kernel instead of ubuntu studios real time one and the wireless works fine in the normal 7.10 so i think it might be a ubuntu studio problem

oh and merry christmas to all!

---

### Post by darkeale on 2007-12-25
ok got it working in ubuntu studio, only thing is i have to run the command 

sudo modprobe ndiswrapper

everytime i boot up otherwise the wireless device isnt recognised. anyway to make the effect of this comment permanent? 

thanks
alex

---

