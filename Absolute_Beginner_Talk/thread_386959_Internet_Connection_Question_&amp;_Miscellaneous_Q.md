---
title: "Internet Connection Question &amp; Miscellaneous Question"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by patrick1314 on 2007-03-17
Hello!

I have a couple questions. I'm new to Ubuntu so I'm not too used to it yet. I have searched around before asking these questions but unfortunately I can't seem to get the exact answer I need.

Oh, I'm running on a Dell Inspiron 9400/e1706 and Ubuntu 6.10 with GNOME, in case that makes a difference.

Question 1: On Windows XP Pro, I had to disconnect and connect the LAN for Internet access each time I started up and shut down. I liked this set up, as I can't stand the idea of an internet connection that I can't connect/disconnect at will. With Ubuntu, the default setup is an 'always on' connection. Is there any way I can set it up like I had it in Windows?

Question 2: Is there a CCleaner equivalent for Linux/Ubuntu? I don't mean a registry cleaner, as I know this is unnecessary, but I did so love the internet browser and application cache-cleaning ability it provided - especially its secure deletion ability. Is there anything that will securely delete my temporary files and browser cache like this?

Thanks!

---

### Post by rccharles on 2007-03-17
> **patrick1314 said:**
> Hello!

I have a couple questions. I'm new to Ubuntu so I'm not too used to it yet. I have searched around before asking these questions but unfortunately I can't seem to get the exact answer I need.

Oh, I'm running on a Dell Inspiron 9400/e1706 and Ubuntu 6.10 with GNOME, in case that makes a difference.

Question 1: On Windows XP Pro, I had to disconnect and connect the LAN for Internet access each time I started up and shut down. I liked this set up, as I can't stand the idea of an internet connection that I can't connect/disconnect at will. With Ubuntu, the default setup is an 'always on' connection. Is there any way I can set it up like I had it in Windows?

Question 2: Is there a CCleaner equivalent for Linux/Ubuntu? I don't mean a registry cleaner, as I know this is unnecessary, but I did so love the internet browser and application cache-cleaning ability it provided - especially its secure deletion ability. Is there anything that will securely delete my temporary files and browser cache like this?

Thanks!
It is possible to do what you want.

There is applications > accessories > terminal
see the commands ifup, ifdown, and ifconfig.

man ifconfig

will provide some terse info on ifconfig


You could go into /etc/network/interfaces and not configure the eth0 port or start eth0.  You could use ifconfig to dynamically configure eth0.

man interfaces

be sure to make a copy of /etc/network/interfaces before messing with it.
cd  /etc/network
sudo cp interfaces interfaces.works
cd ~

I not sure of the details, but this will give you the idea where to look further.

Linux is a lot more secure than Windows.  You need to worry less.  

I'd look into firestarter to set up a firewall. I'd monitor outbound traffic to verify that no unknown application is starting a strange connection.

I'd get a hardware firewall.  Most routers have a firewall.

Question 2:
  Firefox provides for clearing data.  Do: 
    Tools > Clear private data

Look under: 
  Preferences > Privacy 
  See the settings button.

Of course, the data is still on the harddrive.  It is hard to find since the file system pointers to it have been erased/replaced.

Robert

---

### Post by rccharles on 2007-03-18
> **rccharles said:**
> 

I not sure of the details, but this will give you the idea where to look further.



You should leave out the auto stanza in /etc/network/interfaces for eth0. You should leave in auto lo.  When the system boot, it will invoke ifup -a which causes all the auto interfaces to be activated. Thus, only lo will be brought up.

See:
man interfaces for details.

Robert

---

