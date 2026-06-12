---
title: "My internet connection solution  -XP"
date: 2006-03-08
forum: Absolute Beginner Talk
---

### Post by noswal on 2006-03-08
I'm just over a week into using ubuntu, my first post a week ago was about a problem I had, as it was I went this way to get connected.

I could always connect to the internet with my XP laptop which was linked to my desktop (which now has ubuntu) with a crossover network cable.

As I had previously had a static IP address with my desktop when it ran windose I thought that was the way to go, I managed to get a direct connection between the two computers with the laptop having ip 196.168.0.1 and the desktop 196.168.0.2 and activating samba I got shared files between the two, even downloaded a linux file on xp and transfered it across - worked, but limited.

With the internet connected to the laptop the desktop could not get the internet even with ICS on XP. I tried it with the LAN setting in XP being shared and then the modem being shared - neither worked.

Switching to automatic IP address on the laptop that became 192.168.0.1 - now I had previously set in the host file of XP and in host tab of the networkworking program in the system/admin menu that ip address above of 196.168.0.1 was also as the gateway - it worked on a fixed connection but when I changed it to DHCP it didnt. I had made host addresses of the laptop and desktop in there. Removing these helped the connection become established.  I confused myself with the fact that a static ip address begins with 196 and an assigned IP begins with 192

In General tab, Hostname is same as my windose workgroup

Searching the forums for help, I found these "cat" commands to check the content of file configurations, which meant that some had to be edited.
: ~$ cat /etc/hosts
(shows the same as in Hosts tab in network settings)

: ~$ cat /etc/resolv.conf
which for me shows 
 search mshome.net
nameserver 192.168.0.1
(this also shows in the DNS tab)

: ~$ cat /etc/network/interfaces
in this file where is says # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers (added the dns numbers which I got in winxp by typing ipconfig /all)


: ~$ ifconfig -a
(shows your ethenet card status)
: ~$ route -n
(shows your gateway status)
: ~$
: ~$
Also, contained in the set up files is an html file, went through 1 - 6 in doing above
file:///usr/share/doc/samba/diagnosis.html

A BIG also, is that Zonealarm in XP I set to medium with the IP addresses entered and my ISP DNS addresses.

Posts with more detailed help which helped me
[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)
[http://ubuntuforums.org/showthread.php?t=128339](http://ubuntuforums.org/showthread.php?t=128339) 

Hope this helps someone.

---

