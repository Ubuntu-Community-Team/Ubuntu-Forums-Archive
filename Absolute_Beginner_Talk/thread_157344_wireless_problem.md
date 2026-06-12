---
title: "wireless problem"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by xxFelixDCatxx on 2006-04-08
okay I have a toshiba satellite L25 S1192.  this model has an internal wireless card.  With other linux distros, it worked fine, I want to know if in ubuntu there are any other configurations.  I did notice a bit of traffic, but when I started playing around it stopped working.  I am sitting right next to my wireless router with configuration screens pulled up on it.

---

### Post by trent dillman on 2006-04-08
Hmmm...well, there's always the command line.

Could you post the chipset/driver info, your /etc/network/interfaces (with your wep key removed), and maybe what you configured to make it stop working?

In the meantime, try restarting your connection....

First, iwconfig and find the device name that corresponds to your card(probably wlan0 or eth0 or whatever). Then, restart the connection:

```
sudo ifdown wlan0
sudo ifup wlan0
```

---

### Post by xxFelixDCatxx on 2006-04-08
here's the output from the command iwconfig:

ath0      IEEE 802.11g  ESSID:"Houston"
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:11:95:0A:FC:E2
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

aaaand i tried the two commands, I'm still not showing any signal strength at a range of inches away from my wireless access point, I saw the signal strength go up once after disabling it, but am so far unable to reproduce this occurance.

---

### Post by trent dillman on 2006-04-08
If you have WEP enabled, you'll need wpasupplicant. Search Synaptic for that.

Also, what do you have under /etc/network/interfaces?

Be sure to remove your WEP key (if any) before posting it though....

---

### Post by xxFelixDCatxx on 2006-04-08
i would also like to say under the 'support' tab it is listed as an ethernet device, is this correctly listed???

---

### Post by trent dillman on 2006-04-08
Yes, this is fine. Mine is, too. :-)

---

### Post by xxFelixDCatxx on 2006-04-08
[QUOTE=trent dillman]If you have WEP enabled, you'll need wpasupplicant. Search Synaptic for that.

Also, what do you have under /etc/network/interfaces?

Be sure to remove your WEP key (if any) before posting it though....[/QUOTE]


ummm... there were no results for wpasupplicant, and did you mean another program?

and here's the interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0



iface ath0 inet dhcp
wireless-essid Houston
wireless-key ***********************



iface eth0 inet dhcp

auto eth0

auto ath0

---

### Post by xxFelixDCatxx on 2006-04-08
i'm currently connected via CAT 5e :)

---

### Post by trent dillman on 2006-04-08
Nope, wpasupplicant. It's in the Universe repo:

[http://packages.ubuntu.com/breezy/net/wpasupplicant](http://packages.ubuntu.com/breezy/net/wpasupplicant)

---

### Post by xxFelixDCatxx on 2006-04-09
man i'm a n00b, alright I have that package, but don't know how to install it.... and I'm afraid I don't know how this will help me in that I still can't see any antenna strength

thanks for the help though, this is much better than I'd have done on my own

---

### Post by moffa on 2006-04-09
```

sudo apt-get install wpasupplicant

```

or to install the deb file:

```

sudo dpkg -i [package_name.deb]

```

---

### Post by trent dillman on 2006-04-09
install w/ dpkg

```

cd /path/to/where/you/downloaded/to
sudo dpkg -i wpasupplicant*.deb
```

---

### Post by xxFelixDCatxx on 2006-04-09
ugh, i'm still not figuring this out, this is the first time I've ever installed anything in linux, in fact this is only the 2nd linux distro I've ever run.
Sorry for being such a noob, but thanks for the help.

---

### Post by trent dillman on 2006-04-09
It's ok. I was a beginner once as well, and went 2 months with no net or access to my external drive. Did you get wpasupplicant installed?

---

### Post by xxFelixDCatxx on 2006-04-09
what directory is desktop?

---

### Post by trent dillman on 2006-04-09
/home/<your user name>/Desktop

Or, if you're logged in, it's

```
~/Desktop
```

The ~ is shorthand for the current user's home directory....

---

### Post by xxFelixDCatxx on 2006-04-09
alright never mind i've got it instaled.... the output says disabled...

---

### Post by xxFelixDCatxx on 2006-04-09
sooo.. what now?

---

### Post by xxFelixDCatxx on 2006-04-09
okay so i disabled security and it works great now... so obviously you were right, i just need to know how to enable that install that you had me do... thank you very much btw.

---

### Post by trent dillman on 2006-04-09
No problem!

Here, try this: [https://wiki.ubuntu.com/WPAHowto](https://wiki.ubuntu.com/WPAHowto)

---

