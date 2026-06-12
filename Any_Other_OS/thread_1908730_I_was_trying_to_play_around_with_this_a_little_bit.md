---
title: "I was trying to play around with this a little bit....."
date: 2012-01-14
forum: Any Other OS
---

### Post by imachavel on 2012-01-14
on my linux mint partition:

 [http://www.howtoforge.com/ubuntu_pxe_install_server](http://www.howtoforge.com/ubuntu_pxe_install_server)


here we are:

________________________________________
( "You have been without answer too long )
( now. Unfortunately I don't know the    )
( answer, but I believe the short answer )
( is NO"                                 )
(                                        )
( Husse Jun 8 2007                       )
 ----------------------------------------
   o
    o
        .--.
       |o_o |
       |:_/ |
      //   \ \
     (|     | )
    /'\_   _/`\
    \___)=(___/

danel@danel-Dimension-4700 ~ $ sudo <snip>
[sudo] password for danel: 
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
danel@danel-Dimension-4700 ~ $ su
Password: 
danel-Dimension-4700 danel # apt-get update
E: Malformed line 12 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
danel-Dimension-4700 danel # apt-get update
E: Malformed line 12 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
danel-Dimension-4700 danel # sudo apt-get update
E: Malformed line 12 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
danel-Dimension-4700 danel # apt-get update
E: Malformed line 12 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
danel-Dimension-4700 danel # sudo apt-get install update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package update
danel-Dimension-4700 danel # sudo apt-get install netkit-inetd tftpd-hpa dhcp3-server lftp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package netkit-inetd is a virtual package provided by:
  inetutils-inetd 2:1.8-3
  openbsd-inetd 0.20080125-6ubuntu1
You should explicitly select one to install.

E: Package 'netkit-inetd' has no installation candidate


got kind of bored with it. Idk:

sudo netstat -uap
[sudo] password for danel: 
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
udp        0      0 *:bootpc                *:*                                 1016/dhclient   
udp        0      0 *:mdns                  *:*                                 870/avahi-daemon: r
udp        0      0 *:48142                 *:*                                 870/avahi-daemon: r
udp6       0      0 [::]:mdns               [::]:*                              870/avahi-daemon: r
udp6       0      0 [::]:42972              [::]:*                              870/avahi-daemon: r
danel@danel-Dimension-4700 ~ $ sudo /etc/inetd.conf
sudo: /etc/inetd.conf: command not found
danel@danel-Dimension-4700 ~ $ cd /etc/inetd.conf
bash: cd: /etc/inetd.conf: No such file or directory
danel@danel-Dimension-4700 ~ $ cd /etc
danel@danel-Dimension-4700 /etc $ inetd.conf
inetd.conf: command not found



I guess I didn't get around to setting up dhcp, default gateway, subnet mask etc. Anyone else set this up so that you can allow any computer to install the OS if they boot to the network drive? btw, anyone heard that motherboards using intel v pro chip set can install through the network to any computer no matter what hard ware differences? previously what actually prevented people from doing so? Also I remember setting up a windows deployment on a computer one time, and about 15 other computers booted to it and installed 3 partitions. I don't remember it being as hard as this vi dhcpd-3 server stuff. But then, windows is kind of made idiot proof huh? LOL, until it breaks, then you wish you were using linux.

Anyone think they could contribute to this thread? If not no big deal I just wanted to discuss a bit :popcorn:

---

### Post by sffvba[e0rt on 2012-01-14
Thread moved to Other OS.


404

---

### Post by hhh on 2012-01-14
That tutorial is from 2006! Edgy Eft was 9 releases ago.

---

