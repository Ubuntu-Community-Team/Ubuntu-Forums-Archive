---
title: "ARGH! ndiswrapper problems."
date: 2006-01-31
forum: Absolute Beginner Talk
---

### Post by LinuX Nova on 2006-01-31
Hey all.

I have been following the guide [[COLOR="Red"]here[/COLOR]]("https://wiki.ubuntu.com/SetupNdiswrapperHowto?highlight=%28ndiswrapper%29") to install my NETGEAR WG111 usb wireless connector onto my Breezy-installed computer, but seem to have struck some kind of a dent.

I have followed every step to the letter except where it says ```
ndiswrapper-1.1.tar.gz
``` i have typed ndiswrapper-1.8.tar.gz, because that is the version i have used.

I have encountered this problem.

Here it is.

I type this

```
cd /usr/src/ndiswrapper-1.1/
make deb

```

And the prompt says it can't do it. :'(


So, does anyone know what's wrong or how i can fix it?

---

### Post by LinuX Nova on 2006-01-31
Okay, I tried with [[COLOR="Red"]this[/COLOR]]("https://wiki.ubuntu.com/WifiDocs/NetgearWG111?highlight=%28WifiDocs%29%7C%28ManufacturerModel%29%7C%28AND%29") tutorial, and a problem occurs right at the modprobe thing, except this time it does not say anything.

---

### Post by LinuX Nova on 2006-01-31
So sorry to post thrice in the same topic, but i have almost finished setting up the thing except for this

> Specify the details of the connection. Assuming your wireless network runs in managed mode and you need only an ESSID (no WPA or WEP), add the the following to /etc/network/interfaces
[B]
auto wlan0
iface wlan0 inet dhcp
        hostname <hostname>
        wireless_mode managed
        wireless-essid <essid>[/B]

adjusting wlan0 as appropriate, and specifying your hostname and the ESSID of your wireless access point. 


How do I go around finding the bits in bold?

Thanks very much in advance.

Paul.

---

### Post by carlosqueso on 2006-01-31
Before you do that, I'd try opening up a terminal and typing ```
sudo ifup wlan0
``` as you may not need to specify any of that stuff (I didn't have to when I set up my card)

---

### Post by LinuX Nova on 2006-01-31
when i do that it says "ignoring unknown interface wlan0=wlan0"

??

---

