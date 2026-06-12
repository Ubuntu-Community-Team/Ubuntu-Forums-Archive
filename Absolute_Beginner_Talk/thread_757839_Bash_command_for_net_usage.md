---
title: "Bash command for net usage"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by ahvargas on 2008-04-17
I am wondering if there is a command that tell me the net usage of an interface.
Like vmstat is for memory

---

### Post by aktiwers on 2008-04-17
I use this applet for Gnome:
[http://www.gnome.org/projects/netspeed/](http://www.gnome.org/projects/netspeed/)

Very nice.
But not commandline.
Take a look at netstat:
[http://www.faqs.org/docs/linux_network/x-087-2-iface.netstat.html](http://www.faqs.org/docs/linux_network/x-087-2-iface.netstat.html)

---

### Post by Sukarn on 2008-04-17
Thanks for the links to those applications.

Would you happen to know of any application that would tell how much bandwidth an application is currently using?

---

### Post by wawadave on 2008-04-17
system monitor will tell you what all apps are useing.
system/administer/system monitor

But being a linux newby there is most likely something that can monitor 1 program.

found a few things here
[http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html)

---

### Post by unutbu on 2008-04-17
Perhaps ipaudit can do what you want. See:
[http://ask.slashdot.org/article.pl?sid=00/10/02/0059242&mode=thread](http://ask.slashdot.org/article.pl?sid=00/10/02/0059242&mode=thread)
[http://ipaudit.sourceforge.net/](http://ipaudit.sourceforge.net/)

---

### Post by aktiwers on 2008-04-17
There are lots of network commandline tools. Check out this list:
[http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html)

You can install them all with ```
sudo apt-get install <appname>
```
Remember that many of them need to be run with sudo.

Maybe something like iftop or pktstat will do? Sorry I have not used this apps much myself yet :)

---

### Post by Sukarn on 2008-04-17
Sorry to the OP for hijacking the thread.

Thanks for the help guys, but all the applications I tried (and saw at that big list) could only list bandwidth usage by ip address, host name or network interface. So far I have not been able to find any application that shows network usage by a particular application or by multiple applications like iftop does. Unfortunately, even iftop lists by host names and not by application names.
Its the same with pktname.

Maybe I happened to overlook some application in that big list, but none of them seemed to do this. Maybe this is just not possible with linux. I remember using some software on windows about 2 years ago that did this, but windows is out of the question now.

Again, thanks for the help guys.

---

### Post by ghostdog74 on 2008-04-17
```

# netstat --statistics
# man netstat
# info netstat

```

---

### Post by ahvargas on 2008-04-22
thanks to all . netstat worked for me.

---

