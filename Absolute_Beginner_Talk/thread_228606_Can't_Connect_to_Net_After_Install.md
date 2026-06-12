---
title: "Can't Connect to Net After Install"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by pwn3d on 2006-08-03
Hullo.  I tried out the Live CD version of 6.06 on my XP machine, and was duly impressed with how it operated.  It should be noted that I had no problem connecting via Firefox/Gaim/whatever to the internet using the Live CD.  Networking to the two Macs on my LAN was no-go at the time, but not a big issue for the moment.

I installed 6.06 to a partition on my main drive, and while I had no trouble booting up, I no longer have net access.  Firefox, et al., time out when trying to connect.  Going to Sytem>Admin>Network and Networking show that the OS sees the ethernet card (and yes, it's selected), but pinging any address results in an "address not found" error.  One odd thing I noticed is that net access seems to work a few seconds after booting, long enough for the updater to alert me to the 145 updates I need to install :roll: .

This is all truly puzzling to me that the Live version of 6.06 works faultlessly, but an actual install chokes.

Anyone here have any suggestions on how to return connectivity?

My specs:
Dell Dimension 4400 (P4 1.7Ghz, 512MB, bog standard ethernet card)
nVidia 5200 64MB AGP GPU (3rd party)
Ubuntu 6.06


--
Chris

---

### Post by pwn3d on 2006-08-03
Oh, bugger, I forgot to mention I'm hiding behind a router on a cable connection.  It's a Belkin 4-port cable/DSL gateway router.  I haven't gotten around to exploring firewall options on Ubuntu yet, so those should still be set at default (whatever they are).


--
Chris

---

### Post by bensexson on 2006-08-03
Please post the output from these commands:
ifconfig -a
cat /etc/resolv.conf
route -n

---

### Post by eXisor on 2006-08-03
It could be your install is using both 'dfme' and 'tulip'. You can check this by typing 'lsmod' in a terminal and then seeing whether both are there. If so, you have the problem. The solution is simple.

```
sudo gedit /etc/modprobe.d/blacklist
```

and add 'tulip', without the quotes, to the bottom. Reboot and she should be good to go.

If lsmod does not show both, this is not the fix you are looking for.

---

### Post by pwn3d on 2006-08-03
> **eXisor said:**
> It could be your install is using both 'dfme' and 'tulip'. You can check this by typing 'lsmod' in a terminal and then seeing whether both are there. If so, you have the problem. The solution is simple.

```
sudo gedit /etc/modprobe.d/blacklist
```

and add 'tulip', without the quotes, to the bottom. Reboot and she should be good to go.

If lsmod does not show both, this is not the fix you are looking for.

Huh, both items showed up in the listing, alright.  I entered in the commands above, and that seems to have done the trick.  :-D Thanks!

Out of curiousity, what are dfme and tulip for, exactly?   Why turn off tulip and not dfme instead?


--
Chris

---

### Post by eXisor on 2006-08-03
They're both drivers for your network card. I tried turning dfme off for mine and tulip wouldn't work, but YMMV.

---

### Post by sebald on 2006-08-13
> **eXisor said:**
> They're both drivers for your network card. I tried turning dfme off for mine and tulip wouldn't work, but YMMV.

I had the exact same problem on one machine! (But not another, go figure...) My workaround was to install Xubuntu, and things worked fine. Now I'm adding the regular Ubuntu on top of that (the ubuntu-desktop package), and we'll see if the problem recurs. If so, I'll try this solution!

---

