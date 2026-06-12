---
title: "Tips for Ubuntu on PowerBook G4"
date: 2006-10-19
forum: Apple PPC Users
---

### Post by joonahoi on 2006-10-19
I collected few good notes and tips for installing Ubuntu on PowerBook G4 while doing it myself.

It includes synaptic settings for trackpad, finnish / swedish keyboard layout (PC-like tho), Java installation, MOL installation and GPRS on mobile phone using bluetooth.

Hope someone finds it useful.

[http://joona.kuori.org/ubuntu-powerbook/]("http://joona.kuori.org/ubuntu-powerbook/")

--
joona

---

### Post by bogoliubov on 2006-10-19
> **joonahoi said:**
> I collected few good notes and tips for installing Ubuntu on PowerBook G4 while doing it myself.

It includes synaptic settings for trackpad, finnish / swedish keyboard layout (PC-like tho), Java installation, MOL installation and GPRS on mobile phone using bluetooth.

Hope someone finds it useful.

[http://joona.kuori.org/ubuntu-powerbook/]("http://joona.kuori.org/ubuntu-powerbook/")

--
joona

Nice work. I've been looking for Java stuff on PPC linux.

---

### Post by iAndy on 2006-10-19
Been able to get the Wireless Airport Extreme card to work properly?

My dapper installation detects it there and can enable it, but I just cannot scan or connect ot anything with it!

---

### Post by joonahoi on 2006-10-19
Andy, I didn't even try as I have experiences from using Gentoo that Airport Extreme drivers are still far from usable... You will be able to get 11M connection working, but only with WEP if i recall, so still pretty useless.

My solution was to order D-Link DWL-660 card, which I'm still waiting to arrive to get me online wirelessly.

bogoliubov, hope that those tips worked out for you :)

---

### Post by APU on 2006-10-20
Airport Extreme does work, even including WPA. It does need some configuration work done from the Terminal to get it work but it does work! You are ritght regarding the connection speed tough. It only works reliably (or at all?) with 11 MBit. But for most Internet Connections this should be fast enough anyway.

I was using a PowerBook G4 and am now using a PPC Mac Mini with Airport Extreme and it works just fine. Unfortunately I don´t have Links with Howtos ready, but there are many of them out there. Just utilize you most favourite Search Engine.

BTW: AirportExtreme also works in Gentoo since about Kernel 2.6.16 (and before with additional Kernel Patches)

---

### Post by AlphaMack on 2006-10-20
About MOL:

Override root privileges:

```
sudo dpkg-statoverride --update --add root root 4755 /usr/lib/mol/bin/mol
```

If you want to be able to go online, install ipmasq, dnsmasq, and dhcpd.  Then edit your /etc/default/dhcp and enable tun0 or just add:

```
netdev: tun0 -tun
```

In /etc/mol/tunconfig add the lines

```
/etc/init.d/ipmasq restart
/etc/init.d/dnsmasq restart
```

just before exit 0.

Install sysv-rc-conf if you haven't done so and invoke it in a terminal window:

```
sudo sysv-rc-conf -s 2S
```

Go down to the two ipmasq entries and turn them off (startup scripts).  MOL will automatically start them up when called.  If you don't turn off those scripts, you won't have a working internet connection when you start up (as I found out the hard way).

If you prefer, you can shorthand the command to start MOL by adding an alias to your ~/.bashrc.  I called mine "osx."

```
alias osx='startmol --osx'
```

Now close any current terminal windows, open a new terminal window, and type "osx."  You're all set.

Full screen:  CTRL+ALT+F8
Escape full screen:  CTRL+APPLE+F7 (NOT ALT!!!)

And don't forget to install the ethernet driver package when you log in to OS X. ;)

---

### Post by AlphaMack on 2006-10-20
> **iAndy said:**
> Been able to get the Wireless Airport Extreme card to work properly?

My dapper installation detects it there and can enable it, but I just cannot scan or connect ot anything with it!


You need to install bcm43xx-fwcutter from the universe repo.

Find yourself a copy of AppleAirPort2, which is on your OS X system in /System/Library/Extensions/AppleAirPort2.kext/Contents/MacOS/AppleAirPort2

Save a copy of that file to a USB stick or wherever so that you can bring it over to the Ubuntu side.

Now do the following...

```

$ sudo bcm43xx-fwcutter -w /lib/firmware <location of AppleAirPort2>
$ sudo modprobe bcm43xx
```

Try to see if you pick up anything by typing iwconfig.  Scan for networks using iwlist ethX scan (where X is either 0 or 1 depending on your setup).

If you're only using wireless, you can install gnome-network-manager.  Be sure to go to /etc/network/interfaces and comment out everything but the two lo entries.  Reboot.

HTH

---

### Post by joonahoi on 2006-10-20
alphasubzero949, hope you don't mind if I add your tips to the page? 
I'll credit you ofc.

Yeah! Got the Airport Extreme working, with WPA, here's few notes about the WPA thingies:

First install wpa_supplicant:
```

sudo apt-get install wpasupplicant
```

Next, create entry for your wpa_suppplicant.conf :

```

wpa_passphrase NETWORK-SSID NETWORK_PASSPHRASE

```

And you'll get something like following:

```

joona@joona-pb:~$ wpa_passphrase Testnetwork testpassword
network={
        ssid="Testnetwork"
        #psk="testpassword"
        psk=ad1b0027d025072e20e5b554229290a61b9d5547f3644324f5af61ab66b5d5f9
}

```

Now, create file /etc/wpa_supplicant.conf and paste the lines from wpa_passphrase there, and add few arguments, after the operation, your wpa_supplicant.conf should look something like this:

```

network={
  ssid="Testnetwork"
  #psk="testpassword"
  psk=ad1b0027d025072e20e5b554229290a61b9d5547f3644324f5af61ab66b5d5f9
  scan_ssid=1
  proto=WPA
  key_mgmt=WPA-PSK
}

```

Next, create file /etc/default/wpasupplicant with lines as follows:

```

ENABLED=1
OPTIONS="-i#### -Dwext -c/etc/wpa_supplicant.conf -w"

```

The #### should be your AE interface (mine was eth1)

Next, open up your /etc/network/interfaces , and edit iface #### (again, your interface id) to look like this; mine as example:

```

auto eth1
iface eth1 inet dhcp
  wpa-conf /etc/wpa_supplicant.conf

```

Now you should be ready to go! /etc/init.d/networking restart should bring your WLAN interface up, and fetch IP from DHCP thru it.


I'll add these up to guide when i got more time.

---

### Post by joonahoi on 2006-10-20
Oh, one thing. I couldn't get AppleAirport2 - firmware file to work with fwcutter, so I had to get another one that worked. Can't remember where I got it, but here it is now:

[http://joona.kuori.org/ubuntu-powerbook/wl_apsta.o]("http://joona.kuori.org/ubuntu-powerbook/wl_apsta.o")

Despite that, installation went smoothly, just had to use the brand new wl_apsta.o instead of AppleAirport2.

```

sudo bcm43xx-fwcutter -w /lib/firmware /path/to/wl_apsta.o

```

---

### Post by AlphaMack on 2006-10-20
> **joonahoi said:**
> 
Despite that, installation went smoothly, just had to use the brand new wl_apsta.o instead of AppleAirport2.

```

sudo bcm43xx-fwcutter -w /lib/firmware /path/to/wl_apsta.o

```


Awesome. :)  And yes, you can copy those tips.

---

### Post by soapboy on 2006-10-27
About the trackpad tweaks, where the heck is the Input Devices section?  Is it a file?

---

### Post by ivelasco on 2006-10-27
it is part of the file /etc/X11/xorg.conf

---

### Post by Paul Klinkenberg on 2006-10-27
Thanks for the tips, i installed 6.10 on my powerbook yesterday and my touchpad definitely needs some work.

Something else for in your tips maybe:
After installation i thought the machine was behaving a bit weird, and i remembered the same behaviour from when i was playing with cpuscaling in Debian on the same machine.
This is a Titanium 400 mhz g4 machine and switching the cpuspeed (it goes between 300 and 400 mhz) causes it the hang for about half a second.
Powernowd scales the cpu depending on the load and this makes for a horrible experience.. it keeps hanging for short moments.

My solution was to uninstall powernowd and switch the cpuspeed manually, but i suppose it would be more elegant to e.g. use the lower speed when using battery power.
I couldnt find out how to do that before i ran out of patience (and uninstalled powernowd :)

---

### Post by akindy on 2007-03-22
Hey, I don't know if this thread is at all still active but I thought I would try here first before asking anywhere else. I'm new to Linux but am very mac savy, so terminal isn't new to me, but I cannot for the life of me figure out how to enable the wireless even with all these great instructions. If someone could just explain the parts of this thread to me in noob form it would be of great help. Thanks!

---

