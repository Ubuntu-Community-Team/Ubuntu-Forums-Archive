---
title: "Installing CIsco VPN Client"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by Pete89 on 2007-02-19
Hello,

I am having trouble installing the VPN client for Cisco. I downloaded the following file:

vpnclient-linux-4.7.00.0640-k9.tar.gz

I unpacked it to /home/pete

I ran:

```
pete@pete-laptop:~/vpnclient$ ./vpn_install
Sorry, you need super user access to run this script.
pete@pete-laptop:~/vpnclient$ sudo ./vpn_install
Cisco Systems VPN Client Version 4.7.00 (0640) Linux Installer
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms.


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]y

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.15-28-386/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.15-28-386/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.15-28-386/build" will be used to build the module.

Is the above correct [y]y

Making module
make -C /lib/modules/2.6.15-28-386/build SUBDIRS=/home/pete/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-28-386'
  CC [M]  /home/pete/vpnclient/linuxcniapi.o
/home/pete/vpnclient/linuxcniapi.c: In function ‘CniInjectReceive’:
/home/pete/vpnclient/linuxcniapi.c:292: error: ‘struct sk_buff’ has no member named ‘stamp’
/home/pete/vpnclient/linuxcniapi.c: In function ‘CniInjectSend’:
/home/pete/vpnclient/linuxcniapi.c:432: error: ‘struct sk_buff’ has no member named ‘stamp’
make[2]: *** [/home/pete/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/pete/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-28-386'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

```

Now I am scratching my head a lot.

Thanks Pete

---

### Post by ieee488 on 2007-02-19
sudo  ./vpn_install

---

### Post by lreyes6 on 2007-02-19
try installing the **build-essential** package... and try again

---

### Post by Pete89 on 2007-02-19
The scratching is worse now...

```
pete@pete-laptop:~/vpnclient$ sudo ./vpn_install
Cisco Systems VPN Client Version 4.7.00 (0640) Linux Installer
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms.


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]y

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.15-28-386/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.15-28-386/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.15-28-386/build" will be used to build the module.

Is the above correct [y]y

Making module
make -C /lib/modules/2.6.15-28-386/build SUBDIRS=/home/pete/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-28-386'
  CC [M]  /home/pete/vpnclient/linuxcniapi.o
/home/pete/vpnclient/linuxcniapi.c: In function ‘CniInjectReceive’:
/home/pete/vpnclient/linuxcniapi.c:292: error: ‘struct sk_buff’ has no member named ‘stamp’
/home/pete/vpnclient/linuxcniapi.c: In function ‘CniInjectSend’:
/home/pete/vpnclient/linuxcniapi.c:432: error: ‘struct sk_buff’ has no member named ‘stamp’
make[2]: *** [/home/pete/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/pete/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-28-386'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
pete@pete-laptop:~/vpnclient$
```

Thanks for your help!

---

### Post by meng on 2007-02-19
vpnc is an excellent substitute for Cisco VPN client for many (perhaps most!) users.
Install by:
sudo apt-get install vpnc

Then you can google to find out how to modify the example.conf file to a default.conf file for connecting.

---

### Post by Pete89 on 2007-02-19
I have already install build-essentails. Is it necessary to reinstall?

---

### Post by Pete89 on 2007-02-19
"vpnc is an excellent substitute for Cisco VPN client for many (perhaps most!) users.
Install by:
sudo apt-get install vpnc"

OK. Do you use it and it works?

---

### Post by getaboat on 2007-02-19
I use cisco vpn on my XP latop and vpnc on my dapper desktop. Installing cisco vpn on ubuntu looked a bit tricky - vpnc did the job out of the box so I didn't biother with cisco.

No probs from the command line - but can't get the gui to work - must revisit that some time.

Used for RDP to work MS network.

---

### Post by Pete89 on 2007-02-19
OK but would you use it if you had to log in about 10 sites a day? Thats my situation. If I have to touch up some conf. file every time I connect I might go bonkers.

Thanks,

Pete

---

### Post by getaboat on 2007-02-19
I agree that the command line is not an ideal interface - however with vnpc you can save the configurations in files and when you run it point it an the configuration you want.

---

### Post by Pete89 on 2007-02-19
OK I will give it a try and report back.

---

### Post by meng on 2007-02-19
> **Pete89 said:**
> OK I will give it a try and report back.
I can confirm that it works for me.
If you have to connect to different places, then your options are:
- to not use a conf file at all, but type in the particulars every time you use vpnc (yeah that's going to get old fast), or
- have a separate conf file for each place, and specify that conf file at runtime as the one to look at for settings

---

### Post by Pete89 on 2007-02-19
" have a separate conf file for each place, and specify that conf file at runtime as the one to look at for settings"

Cool. How would that look like on the command line?

Thanks again

---

### Post by meng on 2007-02-19
sudo vpnc first.conf

or

sudo vpnc second.conf

---

### Post by Pete89 on 2007-02-19
OK it seems to connect alright but how can I gracefully end the session and begin a new one?

---

### Post by meng on 2007-02-19
sudo vpnc-disconnect

---

### Post by Pete89 on 2007-02-19
Hey that was pretty sweet. Talk about solving a problem quickly. I am getting hooked on Ubuntu FAST because with this kind of help, I can actaully get work done and finally OWN my system.

Happy Noob

---

### Post by meng on 2007-02-19
own, or pwn?
:D
The nice think about vpnc is that (unlike Cisco) it won't break across kernel upgrades.

---

### Post by Pete89 on 2007-02-19
Thanks for you help. I really appreciate it. Once I am connected though when I connect via Terminal Server all I get is a black screen. Its a windows box.

Any idea what the heck this could be?

Maybe I shoul start a new thread or start doing a search on this forum.

---

### Post by meng on 2007-02-19
Hang on a minute, what exactly are you trying to do here? VPN is generally used for connecting to the work or school/university intranet. Are you trying to connect to an individual machine (whether running Windows or Linux)? If so, would you be better off using remote desktop software, i.e. VNC (not VPN)? Or even SSH?

Perhaps if you explain in a little more detail what you are trying to do and why you think VPN is the answer. I admit you may have a legitimate purpose for VPN that I am just ignorant of.

---

### Post by NeonShadow on 2007-02-19
ok, not sure if you did this, but you need to get kernel headers and also run "make" command to compile the source.

I see that you are using 4.7 version, any chance you can get 4.8? If not you need a patch.

Try this link for basic how-to
[http://www.blog.arun-prabha.com/2006/11/16/installing-cisco-vpn-and-vpnc-in-ubuntu/](http://www.blog.arun-prabha.com/2006/11/16/installing-cisco-vpn-and-vpnc-in-ubuntu/)

now, there are some notes to running the VPN. The command in this article did not work for, but instead I used ```
 sudo vpnclient connect <pcf filename>
```

and disconnecting I used Ctrl+C

I'm absolutely amazed that the setup was much less painful then I expected AND I was able to connect to my WindowsXP Pro box at work using Gnome-RDP without much of configuring and was able to run all my apps.

---

### Post by Pete89 on 2007-02-20
For Meng:
Here is what I do. I VPN to the remote LAN and then once I am connected I open up a Terminal Server session to one of the W2k servers on the remote LAN. I do my work and bye-bye. Thats it.

Thanks NeonSHadow. If I could get the CIsco Client to work all the beter since I will then know how to support a LINUX version of it in the hopefull event that one of my clients wants to make the switch to LINUX. I will try and get the 4.8 client but when I went to Cisco´s site I pretty sure I grabbed the latest they had.

Thanks again,

Pete

---

### Post by getaboat on 2007-02-20
It's not the firewall blocking you is it? In which case I installed Firestarter and switched it off. I haven't found a way yet to configure it to allow RDP through.

---

### Post by Pete89 on 2007-02-20
Hi,

Its not a firewall thing because when I vpn into the remote LAN using the Windows CISco client and then use remote desktop to the server it works fine. I can open up the desktop without a problem. It would seem the RDP client for Ubuntu might have issues with W2k terminal services but I am not sure what.

---

### Post by getaboat on 2007-02-20
It was the firewall at th Ubuntu end I was referirng to.

I've just VPNd onto a W2K server using the Ubuntu Terminal Services Client having started up vpnc from terminal. Also onto a W2K3 server. I connect using IP address rather than name. Also I choose the RDPv5 protocol in TSC for both W2K and W2K3 connections.

However, if I try to use TSC with the Ubuntu firewall running - nothing. Turn the firewall off (using Firestarter - which isn't installed by default on dapper) and I get through OK. There may those smarter than I that can say what needs to set in the firewall to allow RDP/TSC through. I can't recall if I had these problems before I installed Firestarter.

---

### Post by Pete89 on 2007-02-20
OK. I will give that a try tonight after work. The thing was I connected but the screen was black. I could ping the server, even do nslookups off it which gets me all the way to the application layer. But whatever, I will give it a go this evening.

Thanks for the tip. Also I have the 4.8 version of the Cisco Client that I will try to install and report back how it goes.

Thanks to everyone,

Pete

---

