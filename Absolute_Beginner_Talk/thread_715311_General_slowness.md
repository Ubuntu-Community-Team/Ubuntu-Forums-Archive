---
title: "General slowness"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by RyanZec on 2008-03-04
I am having issues with general slowness of the OS.  I am running 7.10.  for instance while running firefox I try to open a second tab, it take a few second where it should be pretty much instant.  When in Open office I have a 2 page doc open and when i scroll with the wheel it is sluggish.  anyone else ever have these issue.  BTW i have disabled compiz desktop effect and running default theme.

---

### Post by jan quark on 2008-03-04
try a light weighted web browser like kazehakase; any difference?

also you can check what processes are actually running with the terminal command:

```
top
```

anything eating up your resources ?

---

### Post by kool_kat_os on 2008-03-04
what are the specs of your computer?

EDIT: dang it...jan quark beat me!

---

### Post by PinkFloyd102489 on 2008-03-04
Here's a tweak to make Ubuntu use more RAM before it starts caching to the swap.


Open a terminal (Applications > Accessories > Terminal) and input this:

```

echo "vm.swappiness=0" | sudo tee -a /etc/sysctl.conf

```

After you restart, you'll notice a slight speed up. Nothing dynamic, but every little bit helps. :-)

---

### Post by jan quark on 2008-03-04
> EDIT: dang it...jan quark beat me!

there is no competition and no "beat me" when helping others

also 

great minds think alike :)

---

### Post by RyanZec on 2008-03-04
my computer should be able to handle firefox just fine.  my specs are:

CPU: Intel(R) Core(TM) 2 Duo Mobile T7500 Dual-Core Processor @ 2.20GHz 800FSB 4MB L2 Cache 64-bit
HDD: 250GB 5400RPM SATA150 HARD DRIVE 
MOTHERBOARD: Mobile Intel PM965 + ICH-8M Chipset Mainboard
MEMORY: 2GB (2x1GB) PC5300 DDR2-667 SODIMM Memory
NOTEBOOK: MSI MS-1719 Notebook 17" Widescreen WSXGA+ 1680x1050 Pixels w/ NVIDIA GeForce GO 8600M-GT 512MB Video, 1.3 Mega Pixels CMOS Camera, Mobile Core 2 Duo, & 802.11g Wireless
NB_LCD: 17" WSXGA+ Widescreen TFT Display 1680x1050 Pixels
NETWORK: Built-in 10/100/1000 Mbps Network Card
VIDEO: Built-in NVIDIA GeForce Go 8600M GT 512MB with Turbo Cache Technology Video

kazehakase is quicker but I am able to run firefox on vista with many plugins super fast, linux should be just as good(plus i need some of the plugins for my web development)

---

### Post by zerhacke on 2008-03-04
Blacklist ipv6 in /etc/modprobe.d/blacklist, then reboot.

---

### Post by Aeph on 2008-03-04
> **jan quark said:**
> there is no competition and no "beat me" when helping others

Why not? In what other community do people compete to help? (Don't answer, rhetorical)

---

### Post by {BzF}~JOKesTER on 2008-03-04
Also As Far As Overall Slowness Goes:

#In Terminal Type: 

sudo apt-get autoremove # This Will UnInstall Unused Add-ons From Your HD.

sudo apt-get autoclean # This Will Cleanup Packages From The Cache Area.

Hope This Helps A Bit!

---

### Post by RyanZec on 2008-03-04
how do i blacklist something and why blacklist that?  autoremove and autoclean did not help any

---

### Post by jan quark on 2008-03-04
you blacklist modules by adding them to the blacklist file

```
gksudo gedit /etc/modprobe.d/blacklist
```

just add the line

blacklist something for instance

```
blacklist ipv6
```

at the end of the file
and save
and reboot

sometimes the internet protocol ipv6 causes slow internet connections

---

### Post by philinux on 2008-03-04
What happens when IPV6 goes live?

---

### Post by RyanZec on 2008-03-04
hey thanks, blacklisting ipv6 improves speed much better

hopefully it get faster before ipv6 goes live.

---

### Post by RyanZec on 2008-03-05
I just did a fresh install on ubuntu 7.10 again and my firefox is not slow without blacklisting ipv6 so i guess something else was causing it too.  i keep a wtch on it as i install other applications.

---

