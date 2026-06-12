---
title: "Wi-Fi lost on MacBook Pro/Ubuntu 18.04"
date: 2020-04-15
forum: Apple Hardware Users
---

### Post by Ken53 on 2020-04-15
Recently I installed Ubuntu 18.04 on my MacBook Pro (mfd ~2012) and almost everything worked fine, including Wi-Fi. But suddenly I lost my connection.

Settings > Wi-Fi says "No Wi-Fi Adapter Found ..." 

lspci returns
  ...
  02:00.0 Network controller: Broadcom Inc. and subsidiaries BCM4331 802.11a/b/g/n (rev 02)
  ...

iwconfig  returns
  lo        no wireless extensions.
  enp1s0f0  no wireless extensions.

ifconfig shows only enp1s0f0 and lo -- no wlan0

It looks to me like my wi-fi adapter is dead and needs replaced. Am I right? Or might there be another diagnosis?

Assuming I am right, I have seen instructions on replacing the adapter, but does anyone have any particular recommendations on where to get a replacement and how to install it?

(NB: I am not a sophisticated Linux user and am new to the Forums.)

---

### Post by wildmanne39 on 2020-04-15
Hello, please post the results of the wireless script in my signature so we can take a look and see what is going on.

---

### Post by Ken53 on 2020-04-16
Sorry, but I don't see your signature, much less a script.

---

### Post by jeremy31 on 2020-04-16
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
Link to the script

---

### Post by Ken53 on 2020-04-16
Thanks, Jeremy31, and now I see your signature links, wildmanne39. I ran the apts and my wi-fi adapter seems to be back, but I won't know for sure until I'm within wi-fi range -- probably tomorrow morning.

---

### Post by Ken53 on 2020-04-16
Embarrassingly, the Wi-Fi adapter is found and wi-fi working (right now) after
```

sudo apt update
sudo apt dist-upgrade

```
Thanks to you both!

(The reason I had not updated is that I have become reluctant to do so after many instances of updates breaking work-critical software. I guess that I need to relax on that a bit.)

---

