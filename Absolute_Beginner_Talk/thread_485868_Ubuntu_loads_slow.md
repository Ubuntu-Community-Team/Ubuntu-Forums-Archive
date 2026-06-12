---
title: "Ubuntu loads slow"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by mkeithcloud on 2007-06-27
I recently reinstalled Ubuntu on my laptop and this time around, it loads a lot slower. (the part before the login screen. with the Ubuntu logo and load bar). The only reason I know it is slower this time is because I had it installed before too. So....I am not sure where to go with this, and if there is anything I can do. If anyone has a solution that would be great!

---

### Post by testube_babies on 2007-06-27
When you see the loading image, hit CTRL+ALT+F4 to display the boot-up text.  Then report back where it gets stuck.

---

### Post by mkeithcloud on 2007-06-27
it seems to hang the longest on configuring the network interfaces....I don't see what could be different this install...

---

### Post by Seisen on 2007-06-27
Are you running wireless, that tends to be a pain sometimes.

---

### Post by testube_babies on 2007-06-27
If you use Network Manager, then you can safely do this to avoid setting up network interfaces at boot-time:
```
gksudo gedit /etc/network/interfaces
```
Comment out all lines except for the ones for the loopback interface (lo).

So it should end up looking similar to this:
```
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#et cetera...
```

---

### Post by TheFoe92 on 2007-06-28
I am having a similar problem. So, I followed testube's advice:

> **testube_babies said:**
> If you use Network Manager, then you can safely do this to avoid setting up network interfaces at boot-time:
```
gksudo gedit /etc/network/interfaces
```
Comment out all lines except for the ones for the loopback interface (lo).

So it should end up looking similar to this:
```
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#et cetera...
```

The start-up speed is greatly improved, but when I am at the desktop, my wireless adapter does not work (the light does not even turn on!). Am I commenting-out the wrong one? I have a Gateway 7330GZ laptop with a Broadcom wireless card. I use my wireless to browse the net. What is wrong? Should I comment-out the 'auto lo' instead of 'wlan0'? I am guessing that since I am commenting them out, I am disabling them. Is that correct? And yes, I am running Network Manager. Any help is greatly appreciated. Thanks in advance!

---

### Post by testube_babies on 2007-06-28
Hmmm...I hadn't considered the Broadcom factor :)

To get Broadcom cards working in Linux it takes a bunch of hacks and workarounds, so an intact interfaces file is  usually needed.  You could try leaving the wireless card uncommented, but if that doesn't work, here's another method to try (although I'm not sure it will work):

[http://ubuntuforums.org/showpost.php?p=2322994&postcount=9](http://ubuntuforums.org/showpost.php?p=2322994&postcount=9)

---

### Post by canucks222 on 2007-06-28
i have the same problem; the first, home, installation boots/runs fast.
the second, at work (pc connected to lan), takes about 5 minutes to boot up - there are regular booting messages at the beginning, then several minutes black screen and finally login screen.

---

### Post by Mazehero55 on 2007-06-29
here you go.
[http://www.zolved.com/synapse/view_content/28311/Tune_Boot-Up-Manager_for_better_performance_of_Ubuntu](http://www.zolved.com/synapse/view_content/28311/Tune_Boot-Up-Manager_for_better_performance_of_Ubuntu)

I couldn't find it in my add programs thing, but it's in synaptic. the package name is bum

---

