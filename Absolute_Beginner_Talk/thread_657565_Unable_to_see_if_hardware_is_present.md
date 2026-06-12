---
title: "Unable to see if hardware is present"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by scopo on 2008-01-03
Hi all, I am looking for help yet again !

For some reason my wireless networking has stopped working.  
I started my computer as normal, but no wireless network has displayed, so I went to...
SYSTEM > ADMINISTRATION > WINDOWS WIRELESS DRIVERS
and when this 'starts' i get the following error message...
[SIZE="5"]"Unable to see if hardware is present"[/SIZE]

I tried un- & re- installing both the helper and pciutils (at the suggestion of a google search), but it this hasn't helped ?
Also when I click on the .inf driver to unistall under WINDOWS WIRELESS DRIVERS - nothing happens, is their another method of uninstalling this ?

Thanks for any help !

---

### Post by steve8track on 2008-01-04
Are you using ndiswrapper for your wireless?  On my laptop, I have a USB wireless adapter, and I get it working by typing this every time I plug it in:
```

sudo modprobe ndiswrapper
```

You said it was working before, so I'm guessing that your drivers were installed right already.  You can check with this:

```
ndiswrapper -l
```

Good luck.

---

### Post by balagosa on 2008-06-10
i would like to revive this thread because i am having the same problem but the above statements didnt solve it for me.

output of "sudo modprobe ndiswrapper"
```
WARNING: /etc/modprobe.d/blacklist line 41: ignoring bad line starting with '"blacklist'
WARNING: /etc/modprobe.d/blacklist line 43: ignoring bad line starting with 'blacklsit'

```

output of "ndiswrapper -l"
```
WARNING: /etc/modprobe.d/blacklist line 41: ignoring bad line starting with '"blacklist'
WARNING: /etc/modprobe.d/blacklist line 43: ignoring bad line starting with 'blacklsit'
net5211 : driver installed
	device (168C:001C) present (alternate driver: ath_pci)

```

Note: 
1) i blacklisted ath_hal, ath_pci. will be posting my blacklist document later
2) net5211 is the driver for my Wireless Card

**My Blacklist document from /etc/modprobe.d**
```

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

blacklist ath_pci
"blacklist ath_pci"   <---- Line 41

blacklsit ath5k       <---- Line 43

```

---

### Post by balagosa on 2008-06-11
*bump*

---

### Post by balagosa on 2008-06-13
i expected people know something of this know-how

*bump*

---

