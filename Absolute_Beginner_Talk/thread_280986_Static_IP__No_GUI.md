---
title: "Static IP / No GUI"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by gustolove on 2006-10-20
Was wondering how I could set a static IP on one of my machines without going into the gui.

What I have is another box with ubuntu on it with no keyboard, mouse, or monitor hooked up. I admin the box through SSH. I know if I change the ip the SSH session will become disconnected but then I should just be able to reconnect at the new IP.

I see the /etc/network/interfaces file. I've opened it and it shows:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```

I believe I just need to change the eth0 address 'dchp' comment to 'static'
and then on the next few lines put the settings so it looks like this:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.1.xx
        netmask 255.255.255.0
        gateway 192.168.1.1

```

is that correct?

I was looking through the forums and had seen that other users were having issues when they changed it that way because the dhcp client would still try and renew them an address.

I just want to be sure before I change anything because its a hassle hooking up a monitor, keyboard, and mouse to the box.

Thanks a bunch!

---

### Post by Bachstelze on 2006-10-20
That is correct. Then save the file, exit your editor, run :

```
sudo ifdown eth0 && sudo ifup eth0
```

voilà :)

---

### Post by gustolove on 2006-10-20
Thanks, that worked perfectly... hopefully it will stay that way :-D

---

### Post by gustolove on 2006-10-21
well it turns out there was an issue with just doing it that way. there was a dhcp lease service that was still running and i had to kill it to make it stop switching my ip back nad forth

ps ax
kill 'PID'

that caused it to stop switching ips

---

