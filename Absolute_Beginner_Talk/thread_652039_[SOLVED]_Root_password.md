---
title: "[SOLVED] Root password"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by cfs633 on 2007-12-28
Apologies in advance for the daft questions. I have just loaded 10.7 on my PS3 after 10.4. I had no problems with the earlier release but did a fresh full install rather than an upgrade.I now  have the following problems:

1, If I attempt to be super user ie type su it requests a password. I use the one I logon with (the only user account) and it fails authentication. Is there a default as part of the install? I find that hard to believe but can't think of anything else.

2, No network connectivity. I am using a wired ethernet connection. In network manager I get a choice of wired or modem. The wired is set to remote but there is no connection if I attempt to access a webpage via firefox. The router is wireless but it does not seem to have been detected.

Any help would be greatly appreciated.

---

### Post by taurus on 2007-12-28
1.  Use sudo/gksudo instead.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by KentS on 2007-12-28
1. Have you activated your root account? It's deactivated by default. Use
```
sudo
``` 
instead.

2. Do you get an IP address? Do
```
ifconfig
```
to check.
If you don't get an IP, try 
```
sudo dhclient
```
If you get an ip address, check your nameservers.
For wireless, you might have to install drivers first.

---

### Post by PPAAUULL on 2007-12-28
Typing sudo can sometimes be a pain if you have to do a lot of commands in a row and I sometimes will you the sudo -s command to get to a root terminal for a while. I do not recomend using it for your everyday commands, I ONLY use it when I have a lot to type in and I don't want to be typing sudo and my pass every 5 min.

Hope that helps.

---

### Post by Tyke91 on 2007-12-28
if you want to use superuser powers, get in the habit of using sudo and gksudo every time. There's just too much risk that you could accidentally leave yourself in a root shell and screw yourself over later, i remember that I did that once, compiled/installed a game from source only to find that I made it owned by root... had to delete the entire thing and start over :(

not only that, but you could accidentally delete important files, or let a rare piece of linux malware have full control of your system.


here's a how-to on ndiswrapper for a dell laptop, dunno if it will work the same for the PS3, but you could try
[http://ubhttp://ubuntuforums.org/showthread.php?t=297092](http://ubhttp://ubuntuforums.org/showthread.php?t=297092)

---

### Post by bindatype on 2007-12-28
About issue 2, no connectivity, check the output of ifconfig--if the IP address starts with 169.254 then you aren't getting a dhcp server response but you probably already know that. 

However, the output will/should contain a line that says something line eth0 or ath0 or maybe even wlan0. If you are using wires then you want eth0 or eth1 or whatever the case may be.

At this point you may want to try setting the configuration by hand by editing /etc/network/interfaces

open that file and add these lines to try static assignment:


```
auto eth0
iface eth0 inet static
        address 192.168.1.100 # your values may be different
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        dns-nameservers nnn.nnn.nnn.nnn # the n are numbers provided by your ISP
        dns-search yoursearch.domain.com # this line is optional
```
 
 
to try dhcp add these lines

```
auto eth0
iface eth0 inet dhcp
```

Save and close the file and type this
 
```
sudo ifup eth0
```


Remember that if your value is eth1 then use that instead. See what that gets you. You may also need to add your nameservers to the /etc/resolv.conf file. The format is 

```

nameserver nnn.nnn.nnn.nnn

```
where the nnn.nnn.nnn.nnn is the same number you put in the interface file if you chose static.


Post your output if you have problems or are unsure.

---

### Post by cfs633 on 2007-12-28
Thanks for all the advice. As soon as I can stop my Son using it as a Games console I'll try them out!

---

### Post by cfs633 on 2007-12-30
Thanks guys, I just typed in "sudo dhclient"  and the wired connection connected! Thanks again.

---

