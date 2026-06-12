---
title: "Not booting"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by Bliss_ on 2007-04-08
Hey guys,

I just installed Ubuntu today, and while I was installing some software updates I accidentally tripped over my power cord and that caused my computer to restart. Once I booted it up again, I got to the point where I enter my username and password, but after I log in, it's just a blank screen (regular brown bg) with a cursor. I'm afraid I might have damaged some system files (I probably have) and I wanted to know if theres a solution to this? Thanks.

---

### Post by heimo on 2007-04-08
I think your post is in a wrong forum.

I'd change to virtual console by hitting ctrl+alt+F1, log in, create a new user:
```
sudo adduser [new username]
```

change back to X (hit ctrl+alt+F7) and try to login with the new user. Does it work? If yes, problem is probably in your user specific configuration files.

---

### Post by calraith on 2007-04-08
When you get to the login dialog, hit Ctrl-Alt-F1 to go to a TTY console.  Log in, and:

```
sudo apt-get update
sudo apt-get upgrade -y
```

That should complete installation of whatever failed to upgrade last time.  After the installation of everything completes, if any kernel or module packages were upgraded you should reboot.  Otherwise, just alt-F7 to return to X.  (It's probably safest to just reboot in any case.)

If that doesn't work, you might have some conf file in your profile corrupt.  You might have to do the following:

```
cd /home
sudo mv $(whoami) $(whoami).bak
sudo mkdir $(whoami)
sudo chown $(whoami):$(whoami) $(whoami)
sudo reboot
```

Good luck!

---

### Post by Bliss_ on 2007-04-08
Ok, thanks guys. I just did the update and I managed to get back on. But now I have no internet connection. :s

I'm connecting thorough a Linksys router using an ethernet DSL broadband modem. I've checked the network settings, and eth0 is active, using DHCP. eth0 is set to the default gateway as well. Any ideas?

---

### Post by calraith on 2007-04-08
If you do ifconfig in a terminal window, does eth0 have an IP address?  If not, try:

```
sudo dhclient eth0
```

It's also possible that in all the excitement, your router has locked up and refuses to serve DHCP.  Try unplugging the router's power, leave it unplugged for 10 seconds, then plug it back in and try to renew your IP address.  Any success?

---

### Post by Bliss_ on 2007-04-08
Wel I tried ifconfig, and it doesn't show an IP. Then I did dhclient, and it still didn't do anything. I restarted my router, but still nothing. I'm pretty sure it has nothing to do with my router because I have a laptop (running on XP) connected to the internet.

---

### Post by calraith on 2007-04-08
Try the following:

```
cat /etc/network/interfaces | grep eth0
```

You should have the following two lines:
[INDENT]iface eth0 inet dhcp
auto eth0[/INDENT]

If not, sudo nano -w /etc/network/interfaces and add them.  Then sudo ifdown eth0 and sudo ifup eth0.

If that doesn't help, then try the following:

```
ifconfig -a
```

Does your machine list other entries, not just eth0 and lo?  Is it possible your machine has more than one physical network interface, and you're plugged into what it's configured as eth1 instead of eth0?

---

