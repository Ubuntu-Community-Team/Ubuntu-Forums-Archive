---
title: "where do i go to view wireless interenet servers available?"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by the_anarchist_artist on 2008-02-16
i  have the new Compaqq Presario V30 notebook pc, its an hp that recently had windows vista home premium. I just had a friend changemy operating system to ubuntu. The problem i am having is with interent, I have no idea how to check for wireless internet servers in detecable my detectable range, and much less how to add my houses wifi? where do i go to find my server????
taby the 
ninja

---

### Post by mbsullivan on 2008-02-16
Hi the_anarchist_artist,

I think I can help you, here. However, one thing that you'll soon find on these forums is that, although we all use Ubuntu, our setups are vastly different! This often leads to use of command-line commands, which are useful because the basic commands are often available, regardless of what window manager / installation package you use. Also, they are convenient because one can paste commands on the forums, and others can simply put these commands into a terminal and run them, instead of posting a complicated visual "how-to".

I'm sure that somebody can give you a simple, visual way to do this, but I have a very non-standard Ubuntu setup, so I can only tell you how to do it from the command line.

So, without further ado, I will post some command line interface (CLI) commands that might help you. In order to run these, open up a new terminal window (ALT+F2 I believe, in a default Ubuntu installation), paste the commands and press enter.

Wireless internet is somewhat more difficult than wired internet connections may be. This combined with the fact that I don't know what kind of internet card you have may lead to some extra steps below.

(1) Figure out the name of the "interface" for your wireless card... these are different for different vendors, which is why this step is needed:

```
ls /sys/class/net
```

This will list the interface names for all NICs on your computer. It will probably include eth0 (hardwired NIC), lo (interface for this computer... it's used in complicated situations, don't worry about it), and something for your wireless card (like wifi0, or wlan0). For these steps let's call whatever name you find [wifi interface].

(2) Just to be sure it's not being used, bring your interface down then put it back up:

```
sudo ifconfig [wifi interface] down
sudo ifconfig [wifi interface] up
```

These commands require superuser priviledges (i.e. root access), so the sudo command precedes them.

(3) Scan for open networks

```
sudo iwlist [wifi interface] scan
```

This should return results that look something like this:

> wlan0     Scan completed :
          Cell 01 - Address: 00:04:E2:D0:D1:96
                    ESSID:"SMC"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz
                    Quality=78/100  Signal level=-56 dBm  Noise level=-127 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000039cdb32ac3


The ESSID, Frequency and Address are important, here.

(4) Set the wireless NIC so that it will connect to the found wireless network:

```
sudo iwconfig [wifi interface] ap [whatever you found for address]
sudo iwconfig [wifi interface] essid [whatever you found for essid]
sudo iwconfig [wifi interface] freq [whatever you found for frequency]G
```

Note the "G" after the frequency, to denote "GHz".

(5) Acquire a DHCP address from your wireless router:

```
sudo dhclient [wifi interface]
```

Okay... assuming that your DHCP address was acquired properly, you should have a internet connection all set up.  Now, this is probably too complicated of a process to do everyday, so perhaps you should figure out how to do it in your window manager =] My guess is it's under a setup menu somewhere...

This probably will just confuse the matter...
Mike

---

### Post by PeterJS on 2008-02-16
If you're using the Gnome desktop, which is the default for Ubuntu, there should be an icon in the top panel on the right side that looks like two computers, that's the network manager, if you click on that it should open up a drop down list of networks.

---

