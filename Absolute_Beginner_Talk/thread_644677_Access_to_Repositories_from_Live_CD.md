---
title: "Access to Repositories from Live CD"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by dutch_boy on 2007-12-19
Hi,
I'm trying to install 7.10 as a dual boot with Vista on a machine with "fake-raid" 0.

Booting from the Live CD, the first step is to refresh the repositories and install dmraid so I can create partitions and filesystems.  I've had to disable ipv6 in Firefox to get internet access, but apt etc.  still can't access the internet...hence, I can't follow the usual route to get dmraid running and can't access any disks.

I've seen some of the posts here about disabling ipv6 entirely (which I think is where I need to be going) but they all require a reboot after editing some of the modprobe.d files.  Obviously, if I reboot at this stage, before running the install - I'm just back to the Live CD configuration.

Has anyone got any ideas for getting the config. right while running the Live CD ?

I'm fairly confident that there is no seperate issue with DNS, ip addresses, router config etc. They all look OK and I've got a laptop running 6.06 on the same network and that works like a dream.

Really hope someone here can help me..I'm tearing out what little hair I've got left.

---

### Post by hyper_ch on 2007-12-19
in FF enter:

about:config

There you should be able to disable IPv6

---

### Post by RomeReactor on 2007-12-19
Hi. As you said, you could try blacklisting ipv6 in /etc/modprobe.d/aliases:
```
gksudo gedit /etc/modprobe.d/aliases
```
comment out:
```
alias net-pf-10 ipv6
```
and add this line just below that one:
```
alias net-pf-10 off
```
then, instead of rebooting, you could try:
```
sudo /etc/init.d/networking restart
```
or
```
sudo dhclient
```

Hope this helps.

---

### Post by dutch_boy on 2007-12-19
RomeReactor,
thanks for that - I've stepped through your suggestions & also added a couple of changes I found at [http://www.simonscullion.com/2007/11/20/ipv6-issues-with-ubuntu-710/](http://www.simonscullion.com/2007/11/20/ipv6-issues-with-ubuntu-710/).  Following a networking restart - still no joy.

I guess it's safe to assume I've disabled ipv6 - so I assume I've been barking up the wrong tree.

What has helped..... I've changed server and protocol in the Software Sources applet (a UK mirror via ftp) and this seems to have cracked the problem.  I've got dmraid installed and can see the raid disks.  Thanks a lot for your prompt help....no doubt I'll be back as the install progresses !!

---

