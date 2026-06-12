---
title: "internet + KDE"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by reallybign00b on 2007-01-15
hi, 

i installed ubuntu dapper a few months ago, and i havent used it since, but i want to start using KDE.  my friend showed me how to do this, but he said that i need internet connection to access the synaptic package manager.  the problem is, that when i change my internet connection, it still says 'lo'.  and it still doesnt work.  can someone please help me with my internet connection.

---

### Post by inCursorated on 2007-01-16
lo is the loopback interface which you don't connect to the internet through. perhaps your adapter is not enabled? try running the command 'sudo ifconfig -a' and see if there is another interface (eth0). if there is, try opening a console a doing:

```

sudo ifconfig eth0 up
sudo dhclient eth0

```

this is assuming your using DHCP. how are you changing your internet connection? what type of connection do you have (dsl, cable, etc.)?

you could also just grab a [kubuntu]("http://kubuntu.org/") iso image (the kde version of ubuntu) and start from scratch...

---

