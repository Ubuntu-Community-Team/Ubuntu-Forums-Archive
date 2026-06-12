---
title: "Launching Terminal reboots machine"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by ChristopherS on 2008-01-17
I'm a complete newbie to Linux, but eager to learn. I picked up a cheap older computer to play with - it's a Dell Dimension L667r, PIII 866 MHz, 320 MB RAM, 7.5G hd. Not great specs, but from reading the forums, it seemed like it should be enough to run Xubuntu. It booted fine off the Xubuntu 7.10 live CD, so I went ahead and did the install. I just accepted all the defaults, let it handle partitions, etc. The only error message I got in the installation process was that it couldn't connect to the internet to get the security updates. 

After install, it boots fine, various programs, games, etc. launch just fine. No internet, so I go into the Network control panel and set it to DHCP. I'm trying to connect through a DSL modem and ethernet cable which I know are good. So (from my reading) it seems like the next step is to go into the Terminal and try to figure out if it's seeing the NIC and what's going on. But when I try to launch Terminal, everything disappears and I'm at the login screen. This happens every time - I can't start the terminal. It's not a total reboot, I guess, just a logout. 

I've only set up one account, which I assume has admin rights - I didn't do anything special with that.

What's next? I'd be happy to reinstall, but this was a clean install, and there weren't really a lot of options, so I'm not sure what I would do differently. Should I try the Ubuntu CD instead, and is it easy to migrate from that to Xubuntu if the performance is bogged down?

Unfortunately, I kind of have to do all of this from memory, because the only computer I have at home that does have an internet connection is an old Mac that can only handle an old browser that crashes when I try to post here. I can read any responses, and will be very thankful for them, but probably can't reply with any details about the system until tomorrow.

---

### Post by maybeway36 on 2008-01-17
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/91849](https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/91849) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Add to /etc/X11/xorg.conf at the end:
```
Section "Extensions"
        Option "Composite" "Disable"
EndSection
```

---

### Post by ChristopherS on 2008-01-17
Cool - thanks.

---

### Post by flasherrr on 2008-01-23
How can you change the file. I can't acces the terminal....

---

