---
title: "Wireless not working"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by whiterabbit on 2006-09-23
Hi everybody,

I've been trying to get my Netgear WG11v2 card working and I'm having alot of trouble. I've made countless searches and despite being able to get it working a long while back when I first tried Ubuntu, I can't get it working now. 

I'm on my Thinkpad T20, running Xubuntu and I've managed to get the driver installed(using the win98 drivers).  

Both...

```
ndiswrapper -m
modprobe ndiswrapper
```

...do nothing.  Well "ndiswrapper - m" tells me that modprobe config already contains alias directive(no idea what that means to be honest).

ifup wlan0 gives me an error.  

Any ideas?  I'd really appreciate the help, thanks.

---

### Post by jd65pl on 2006-09-23
What is the output of
```

sudo ndiswrapper -l
```

Also what error message do you get .

Thanks

J

---

### Post by whiterabbit on 2006-09-24
Alrighty... I figured upgrading to Ubuntu 6.06 would do the trick but it still doesn't work.  

I'm able to install the driver with ndiswrapper.  

When I type...

```
sudo ndiswrapper -l
```

...I get "driver present, hardware present".

```
ndiswrapper -m
``` 

...gives me "modprobe config already contains alias directive".

When I type...

```
modprobe ndiswrapper
```

...I get nothing.

Then I type...

```
sudo ifup wlan0
```

...and this comes up: "ifup: interface wlan0 already configured".

This is probably because I went into Applications, System and Networking to set up the card a little while back.  Now, despite it saying that the wireless card is activated, I'm still unable to connect to the net.  I know this post is probably VERY confusing but I guess that because I'm a little confused myself.

---

### Post by jd65pl on 2006-09-24
You would only have to modprobe ndiswrapper the once. Have you tried using the guide for the whole set-up. I would highly recommend it.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

Thanks

J

---

### Post by xyz on 2006-09-24
Also by **nickm:**
[How to: Broadcom Wireless cards without Ndiswrapper for Dapper and Edgy]("http://www.ubuntuforums.org/showthread.php?t=185174&highlight=DMA")

---

### Post by whiterabbit on 2006-09-24
I finally got it working and I was only a step away when I posted my last post.  Thanks. :D

---

### Post by chrisfay on 2006-09-24
You may want to post your solution if it could benefit other members...just a thought.;)

---

### Post by whiterabbit on 2006-09-24
To be honest, I don't really know how I did it.  I just reconfigured the network settings, made sure everything matched and rebooted.  Worked fine. 

The only problem I'm having now is that I can't connect with the card in the slot.  If the card is inserted during boot and it reaches the network configs, the card activates and the laptop "freezes".  So I have to reboot, take out the card and insert it when the OS boots up.  Only then will it work.

---

### Post by jd65pl on 2006-09-24
Add

```
 alias wlan0 ndiswrapper
```


To:
/etc/modules.d/ndiswrapper

then reboot see if that works

J

---

### Post by jd65pl on 2006-09-24
See this post another person had this issue to.

[http://ubuntuforums.org/showthread.php?t=259445]("http://ubuntuforums.org/showthread.php?t=259445")

---

