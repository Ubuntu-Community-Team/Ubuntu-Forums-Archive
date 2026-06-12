---
title: "Wireless Networking"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by Twelveone on 2007-02-24
Hi All,

Completely new to Ubunto. I have a little Unix experience, but I have no idea how to get my wireless network connection working. :( 

I have a Allied Telesyn AT-WCP200G PCI card installed and Ubunto detects it OK. It appears in the Network Settings and I have enabled it and tried setting the properties to use both DHCP and Static IP but it does not seem to be communicating. 

Is there something I need to do to get it to connect to the network? If so What? :-k

Cheers

Stewart

---

### Post by hyper_ch on 2007-02-24
can you open a command line terminal and post the output of the following two commands?

```

iwconfig

```

```

ifconfig

```

---

### Post by i.am.canadian on 2007-02-24
Hey there,

If Ubuntu detects your wireless card you may want to try downloading (over a wired connection I guess) network-manager by entering the following into the terminal
```
sudo aptitude install network-manager-gnome
```

Then you will want to go to system > preferences >sessions.  Then click the 'startup programs' tab and then click 'add' and enter the following into the text box
```
nm-applet
```

You may have to logout and log back in to see the effect, but it should be a little icon up next to the clock and it looks like two flat panel monitors overlayed on a wired connection, and shows signal bars for a wireless one.

I hope this helps, if not, I'm sure someone with a bit more know-how will be able to.

Cheers.

---

