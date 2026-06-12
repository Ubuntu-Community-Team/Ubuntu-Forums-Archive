---
title: "Internet problems"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by bobalicious on 2007-03-30
Hey, 

I have recently upgraded from a 512 connection to 1.5 megabit connection. With XP i have no problem with the connection, however with ubuntu i am waiting 1min+ for google to load.

I recently had problems with actually connecting to internet, i was told to disable ipv6 protocol throughout the OS which allowed me to connect to internet.

Any help would be greatly appreciated

---

### Post by openix on 2007-03-30
Try this, from a terminal type,

gksudo gedit /etc/modprobe.d/blacklist-ipv6

then enter password. Copy the following two lines into the new text file,

# Disable IPv6 because it's not needed
blacklist ipv6

Save this file and reboot. Once your machine reboots, login and open a terminal up then type the following,

lsmod | grep ipv6

hit enter, other than the terminal prompt you should see nothing on the next line. This mean the IPV6 module has not loaded - which is what you want :)

You can also do the following if you wish, go Systems > Administration > Networking, click on host tab under Network Settings and remove all references to IP6 in the IP Address/Aliases list.

Also firefox is known to go faster with IPV6 disabled - see [http://www.hackaday.com/2004/12/26/speed-up-firefox/]("http://www.hackaday.com/2004/12/26/speed-up-firefox/") for more details.

---

