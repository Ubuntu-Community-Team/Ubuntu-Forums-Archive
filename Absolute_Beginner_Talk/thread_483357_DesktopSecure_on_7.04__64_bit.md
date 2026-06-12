---
title: "DesktopSecure on 7.04  64 bit"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by roystondh on 2007-06-24
I have used Panda sofware's Anti Virus & firewall s/w for three years on my XP / 64 bit XP machines for three years and wanted to check out the DesktopSecure product, to keep things simple.

No mention is made on the Panda website about Feisty Fawn support, so I could simply be pushing my luck, but at least it's free for the first 90 days.

On download and install I get the following errors:-

In terminal mode after the command "/tmp/desktopsecure.sh" I get "verifying archive integrity.........All good"

then several lines later
"/install .sh:29: ./panda - language:not found"

In gedit I get "Could not open the file /tmp/desktopsecure.sh" as per below.

Sounds as if it might be something simple :confused: ( I've just put an order into Amazon for the offical guide to Ubuntu so I can get up to speed with the OS  in general)

Any thoughts?

---

### Post by wormser on 2007-06-24
The standard virus scanner in Linux is Clamav.

```
sudo apt-get install clamav avscan
```

AVscan is the gui front end.

---

### Post by roystondh on 2007-06-24
> **wormser said:**
> The standard virus scanner in Linux is Clamav.


Thanks I shall give it a try if I can't get DesktopSecure to run

---

