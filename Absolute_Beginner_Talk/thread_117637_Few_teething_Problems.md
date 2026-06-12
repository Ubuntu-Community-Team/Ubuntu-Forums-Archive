---
title: "Few teething Problems"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by completelinuxnoob on 2006-01-15
Hi all I'm a complete noob to any form of linux,but an advanced windows user.First let me just say Ubuntu=wow!!!I won't be going back to that clunky overpriced os if i can get a handle on this.

Ok points-I've installed ubuntu on a self built amd athlon 64 2800+ system with an asus mboard.So far all hardware recognised except my broadband ethernet modem(yikes)

I've tried downloading cedega via this pc running windows but i have no idea how to install on ubuntu.I open the file and it asks me to run,run in console or view.Ive tried all and the best i can get is a 10 sec window that i then close.

Can someone tell me in VERY VERY simple linux how to do one of the 3 following-

connect my modem to my ubuntu pc
or
Network my ubuntu pc to my windows xp pc and browse the internet that way
or
download linux programs on my windows pc,transfer to the hard drive on my ubuntu pc(transferring itself not a prob) and install that way

I know there's probably a way to do it automatically but im still in os transfer shock,its like starting computing all over again :)

Thanks a million in advance

---

### Post by cwaldbieser on 2006-01-15
[QUOTE=completelinuxnoob]Hi all I'm a complete noob to any form of linux,but an advanced windows user.First let me just say Ubuntu=wow!!!I won't be going back to that clunky overpriced os if i can get a handle on this.

Ok points-I've installed ubuntu on a self built amd athlon 64 2800+ system with an asus mboard.So far all hardware recognised except my broadband ethernet modem(yikes)

I've tried downloading cedega via this pc running windows but i have no idea how to install on ubuntu.I open the file and it asks me to run,run in console or view.Ive tried all and the best i can get is a 10 sec window that i then close.

Can someone tell me in VERY VERY simple linux how to do one of the 3 following-

connect my modem to my ubuntu pc
or
Network my ubuntu pc to my windows xp pc and browse the internet that way
or
download linux programs on my windows pc,transfer to the hard drive on my ubuntu pc(transferring itself not a prob) and install that way

I know there's probably a way to do it automatically but im still in os transfer shock,its like starting computing all over again :)

Thanks a million in advance[/QUOTE]

The last option is the simplest to describe, but it can be a annoying to do--  you basically download the Ubuntu .deb files for the packages you want, copy them to Ubuntu, and then issue this command:
```

$ sudo dpkg -i <deb file name>

```
If you are missing dependencies, you have to download those debs first, and repeat the process until all the dependencies are installed.

If you can get one of the first two options working, I highly reccomend it.  First, you should check if your ethernet card is recognized.

Try using this troubleshooter, and let us know how far you get:
[http://ubuntuforums.org/showthread.php?t=87643]("http://ubuntuforums.org/showthread.php?t=87643")

---

### Post by completelinuxnoob on 2006-01-15
I've gotten to ifconfig and i've gotten a readout but i don't have an ip address,how do i assign one?

---

### Post by cwaldbieser on 2006-01-15
[QUOTE=completelinuxnoob]I've gotten to ifconfig and i've gotten a readout but i don't have an ip address,how do i assign one?[/QUOTE]
```

$ sudo ifconfig eth0 192.168.0.2

```
Assigns IP address 192.168.0.2 to your eth0 device.  This is a static IP address.

```

$ sudo dhclient eth0

```
Causes your eth0 device to request a dynamic IP address via DHCP. 

If you want to share the Internet from XP, you probably want to just assign a static IP address to your Ubuntu PC, since it will be on your local network.  If you connect it directly to your Internet modem, you probably want to request a dynamic IP address.

---

