---
title: "Ubuntu Server 7.10 Wireless Connections"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by mohaakilla51 on 2008-03-12
OK, so, I am, although note completely new at Linux, I have never dealt with the shell before. So, in order to broaden my horizons, I decided to give Ubuntu 7.10 Server Edition a shot. I installed it on a semi-old machine that I bought for $40 at a garage sale, and now am trying to connect to my home's wireless network. The wireless card works, because I tested it on a Ubuntu 6.X Live CD I had, and it connected fine. I tried to find out the command to connect it via the shell, and came up with "iwconfig", so the problem would be, when I type iwconfig, it doesn't seem to find my router. I get the following: 

```

administrator@server-test:~$ iwconfig
lo                    no wireless extensions

eth0                  no wireless extensions

wmaster0              no wireless extensions

wlan0                 IEEE 802.11g  ESSID:""
                      Mode:Managed   Channel: 0   Access Point: Not-Associated
                      Retry min limit:7   RTS thr: off   Fragment thr=2346 B
                      Link Quality: 0    Signal level: 0    Noise level: 0
                      Rx invalid nwid:0   Rx invalid crypt:0   Rx invalid frag:0
                      Tx excessive retries:0   Invalid misc:0   Missed beacon: 0
administrator@server-test:~$

```

Now, I assumed my network was the wlan0 one, so I then tried to connect to it, and still no luck... assuming that I was not trying to connect to my network, I went and unplugged the router, and had no change on the screen, leading me to believe that this is just something that is always there...

I have also seen people refer to eth1 as a device, yet, whenever I type:
```

iwconfig eth1

```
I get told that that isn't a valid device... So, is there some configuration file I have to change before I can connect? Or, how can I get it to connect. I KNOW the network is not at fault, because I am sitting here on my laptop, running the aforementioned Live disc, and am having no problems connecting...

Any suggestions?

~ Cody Haines

---

### Post by handydan918 on 2008-03-12
RE: eth1. 
You don't have one. It appears that your wireless is on wlan0. So try ```
sudo dhclient wlan0
```
and see if that gets you an IP address. 
If it doesn't, you may find ```
sudo iwlist scanning
``` useful.

edit: Just to keep your sanity, turn off encryption at the router. You can turn it back on after all else is well.

---

### Post by mohaakilla51 on 2008-03-12
OK, tried both of those things... not sure which IP you were talking about on the first one, but the last line I get is
No working leases in persistent database - sleeping

However, I do get an access point, which is accurate according to my router, but no IP...

On the iwlist scanning, I get told that no scan results were found. However, isn't that just supposed to give you an Access Point? If so, then I already have that data, but even manually setting it:
```

sudo iwconfig wlan0 ap xx:xx:xx:xx:xx:xx

```
I don't get any results...

maybe I am not finishing the setup, what command do I use to actually connect to it?

---

### Post by handydan918 on 2008-03-12
> **mohaakilla51 said:**
> OK, tried both of those things... not sure which IP you were talking about on the first one, but the last line I get is
No working leases in persistent database - sleeping

However, I do get an access point, which is accurate according to my router, but no IP...

On the iwlist scanning, I get told that no scan results were found. However, isn't that just supposed to give you an Access Point? If so, then I already have that data, but even manually setting it:
```

sudo iwconfig wlan0 ap xx:xx:xx:xx:xx:xx

```
I don't get any results...

maybe I am not finishing the setup, what command do I use to actually connect to it?

Is the router set up to do dhcp?

---

### Post by mohaakilla51 on 2008-03-12
yes. here is a question I posted elsewhere, as a kindof addendum to this thread, but, is there a way to get the network config files from the live disc, after I got it working, IE, while the live disc is running, onto my server install?

---

### Post by handydan918 on 2008-03-12
Knowledge meter maxed out. Let's see if a real wireless guru shows up...

---

### Post by mohaakilla51 on 2008-03-13
lol, not a big worry, as I said, it is really only to learn anyway, so internet connection isn't vital, untill I actually want to run it as a full fledged web server, but that will be a while down the road

---

