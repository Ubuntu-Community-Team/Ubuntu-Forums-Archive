---
title: "Again bluetooth"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by Trance Gemini on 2007-10-04
Hi! I am posting my question again.

 have 2 PC. The first one runs windows XP (let's call it "main") and it is connected to the internet. The second one is laptop with no internet connection (let's call it "laptop"). Laptop has gutsy beta.

Recently I have bought a D-Link DBT-122 device (a bluetooth device, that is plugged via USB). I had an idea to plug this device to the main PC so that I could access internet on my laptop.

In the bluetooth explorer on main pc I can see my laptop. But when I try to connect them, it sais that the only bluetooth service avaliable on laptop is the audio device. So, no something like bluetooth network, or how should I name it.

If I load synaptic and search by "bluetooth" keyword, I can find, that some bluetooth related package descriptions contains phrase like "To make use of bluetooth functionality, install gnome-bluetooth".

So, I have two questions:
1. How to add something to my laptop, so that not only audio device, would be avaliable to use? Of course it means the network.
2. Do I need the gnome-bluetooth package to solve my problem? If so, how to install it if I do not have access to the internet on my laptop (because of question 1  )

By the way, maybe there's some sort of guide how to access to the internet via such devices?

Regards

---

### Post by pirxx on 2007-10-04
I am using a  USB Bluetooth dongle on an IBM ThinkPad T40, currently running Gutsy. 

I have not managed to get anything to work with Bluetooth in Gutsy or before in Feisty, beyond pairing devices. Since USB printing also only works on tuesdays after full-moon, I suspect this is the much bemoaned ubuntu USB issue and not a Bluetooth problem.

Apart from the broken PCMCIA support and the broken PPTP/OpenVPN issues, this is my biggest issue with ubuntu.:( 

You can't admit ubuntu into a production environment with these things not working.

---

### Post by Trance Gemini on 2007-10-04
You know, I have found some thoughts [here]("https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/138356").
As I've understood, the problem is in the gnome-vfs-obexftp package.
But, as I mentioned, I do not have a internet connection, so I cannot install it :(
But maybe this will give you the clue :)

---

### Post by FuturePilot on 2007-10-04
Try this
Gutsy i386 package.
Put it on a USB drive and take it to your laptop. Double click it to install.
[http://mirrors.kernel.org/ubuntu/pool/universe/g/gnome-vfs-obexftp/gnome-vfs-obexftp_0.4-1_i386.deb]("http://mirrors.kernel.org/ubuntu/pool/universe/g/gnome-vfs-obexftp/gnome-vfs-obexftp_0.4-1_i386.deb")

---

### Post by odzk on 2007-10-04
this is the same problem as mine...

for windows xp, there is a program feature from bluesoleil called LAN Access where u can share the connection for both pc and the laptop but ubuntu dont have this software.

:(

---

### Post by Trance Gemini on 2007-10-04
> for windows xp, there is a program feature from bluesoleil called LAN Access where u can share the connection for both pc and the laptop but ubuntu dont have this software
yeah, because I have a winXP also on my laptop, I have connected them with no problems.

I will try to install the package, but I am afraid it will ask for dependencies.

---

### Post by Trance Gemini on 2007-10-04
hmmm... well, I have installed vfs package. File transfer works great.
But what next? What to do with my problem regarding internet via bluetooth? :confused:

---

### Post by Trance Gemini on 2007-10-04
Problem solved. 
Everything works.

---

### Post by xarroyo on 2007-10-04
So, Finally what did you do to solve the problem?

---

### Post by Trance Gemini on 2007-10-04
First I installed the deb package gnome-vfs-obexftp.
Then I added a new network interface to the /etc/network/interfaces like this:

```
address 192.168.0.30
netmask	255.255.255.0
network	192.168.0.0
gateway	192.168.0.1
auto	bnep0
map	bnep0
```

Then I edited a pand startup script, so that pand starts automaticaly on boot, and then connected it to the main PC using pand :)
```
pand --connect mac_address_of_main_PC
```

---

