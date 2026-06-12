---
title: "installing vpn client"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by dagarshali on 2008-04-19
Hi,
I am very very new to linux world. I installed ubuntu 7.10-gutsy version. I order to access some of the softwares from off campus, we need to install the vpn client provided by our school. The link of the website is [http://www.it.iastate.edu/pub/lng335/lng_335.html](http://www.it.iastate.edu/pub/lng335/lng_335.html)

It says to type in terminal
rpm -q kernel-source, and when i do that...I get 

> root@dagarshali-desktop:/usr/src# rpm -q kernel-source
package kernel-source is not installed
root@dagarshali-desktop:/usr/src# 

the document then asks to install the kernel-source. I also did > uname -r at the terminal and got 2.6.22.14-generic as output

When I go to the folder

/usr/src/ I find folders name linux-headers-2.6.22.14, linux-headers-2.6.22.14-generic and another folder called rpm.

when installing the vpn client it asks for the path for the kernel source. when i give /usr/src/linux-headers-2.6.22.14-generic, it gives

> Making module
make -C /usr/src/linux-headers-2.6.22-14-generic SUBDIRS=/home/dagarshali/Desktop/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/dagarshali/Desktop/vpnclient/linuxcniapi.o
/home/dagarshali/Desktop/vpnclient/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory
/home/dagarshali/Desktop/vpnclient/linuxcniapi.c: In function ‘CniInjectReceive’:
/home/dagarshali/Desktop/vpnclient/linuxcniapi.c:315: error: ‘struct sk_buff’ has no member named ‘stamp’
/home/dagarshali/Desktop/vpnclient/linuxcniapi.c:347: error: ‘struct sk_buff’ has no member named ‘nh’
/home/dagarshali/Desktop/vpnclient/linuxcniapi.c:348: error: ‘struct sk_buff’ has no member named ‘mac’
/home/dagarshali/Desktop/vpnclient/linuxcniapi.c: In function ‘CniInjectSend’:
/home/dagarshali/Desktop/vpnclient/linuxcniapi.c:452: error: ‘struct sk_buff’ has no member named ‘stamp’
/home/dagarshali/Desktop/vpnclient/linuxcniapi.c:456: error: ‘struct sk_buff’ has no member named ‘mac’
/home/dagarshali/Desktop/vpnclient/linuxcniapi.c:457: error: ‘struct sk_buff’ has no member named ‘nh’
/home/dagarshali/Desktop/vpnclient/linuxcniapi.c:460: error: ‘struct sk_buff’ has no member named ‘h’
/home/dagarshali/Desktop/vpnclient/linuxcniapi.c:460: error: ‘struct sk_buff’ has no member named ‘nh’
make[2]: *** [/home/dagarshali/Desktop/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/dagarshali/Desktop/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

Please help

Regards,
vishwa

---

### Post by quirks on 2008-04-19
I found a post where someone had the exact same problem. The thread also points out a solution: you need to download a patch for your VPN client.

Link: [http://ubuntuforums.org/showthread.php?p=2511814](http://ubuntuforums.org/showthread.php?p=2511814)

Besides: Ubuntu doesn't use RPM packages. It is Debian based and uses DEB packages, therefore. So running rpm -q something is pointless. The according tool is dpkg.

---

### Post by crashcoredump on 2008-04-19
Is it the Cisco Client?

If so just use VPNC, you need to supply some parameters but I use to connect to the ASA's at work and it works Awesome.

Its in the package list for apt-get........

---

### Post by Washer on 2008-04-19
Run your own vpn client. I use KVpnc from add/remove programs with openvpn or vpnc (i forget which) in synaptic

Get the group password & decrypt it - many [sites]("http://www.google.com/search?q=vpn+group+password+decrypt&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a") will do it. I used [this]("http://www.thecampusgeeks.com/tools/cisco-VPN-decrypt/cisco-decrypt.php"). The rest of the setup is fairly straightforward, import the settings file, put in the passwords & connnect. I had to turn off advanced settings under (preferences->profile->general->advanced).

---

