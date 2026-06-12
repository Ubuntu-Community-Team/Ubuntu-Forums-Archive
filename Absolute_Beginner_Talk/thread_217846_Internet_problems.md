---
title: "Internet problems"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by alpine_sc on 2006-07-17
I installed Ubuntu about a week ago on my laptop and everything worked perfectly.  Then, I tried installing 3d acceleration, but I must have configured it wrong because I could not get into the GUI.  I tried reinstalling and reconfiguring, but I failed a few times until I decided to just reinstall Ubuntu.  After reinstalling, I got problems with my internet connection.  It goes extremely slow, and it usually times out before a website can open. When downloading packages, updates, and package information, it usually fails the first time, but the second time it usually downloads at 150+ KB/s, which is normal speed.  I use a Qwest DSL modem and use the USB port.  Another computer is connected via the ethernet port.  I tried connecting the laptop to the modem via the ethernet port, but there was the same problem.  I read on another forum that there could be a problem with ipv6 (whatever that is) and the modem.  So I went to /etc/modprobe.d and opened up aliases and inserted the lines

alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ivp6 off

in place of

alias net-pf-10 ipv6

It doesn't work (that's what I guessed because the problem wasn't  just with Firefox.
Any suggestions?

---

### Post by Thenotsowyzewun on 2006-07-17
This usually happens with routers but not modems - the DHCP table is probably corrupt (I think that's what people blame it on...).
Anyway try resetting your modem :).

---

### Post by alpine_sc on 2006-07-18
Well I pushed the reset button on my modem, but that didn't work, and I tried unplugging it overnight, but that didn't work either.

Why would the internet work the first installation and not the second or third?  Should I try boot and nuke to completely erase my disk and then try reinstalling it?

---

### Post by alpine_sc on 2006-07-19
YES!!!! FINALLY after much hassle I ended up right back at the beginning.  I had to disable ipv6 but I just wasn't doing it right.  From the same forum that I learned about ipv6 there was a post that said to type about:config in firefox address bar.  In filter, I typed ipv6 and toggled network.dns.disableIPv6 to true.  Internet is working great.

---

### Post by alpine_sc on 2006-07-19
Oh, btw, does ne1 know why the internet worked for me during the first installation without disabling ivp6?

---

