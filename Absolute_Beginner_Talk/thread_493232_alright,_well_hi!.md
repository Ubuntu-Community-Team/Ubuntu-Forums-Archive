---
title: "alright, well hi!"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by i986 on 2007-07-05
my name is Isaac, apperently there is already someone here named that cause it would not allow me that name.  But anyway, I'm new to debian and have very limited experience running *nix in a networked enviroment.  I have a 2001 Dell with a Pentium II 800 Mhz processor, 128 Mb's of RAM and a 56k modem.  I have it running Xubuntu, but I'm having issues getting it onto my LAN, which currently consists of a Windows XP desktop (what I'm on) w/ ether connection and a Windows XP Laptop w/ wifi connection (it also has ether, but connects by wifi).

now, the NIC's I have avalible to use in the 2001 Dell are:
Linksys WMP300N 802.11n wifi card
Netgear GA311 Gigabit ether card
D-Link DWA-542 802.11n wifi card

the Netgear is recognized, but I can't get it to do anything; the Linksys was in there but it was not recognized at all; and the D-Link I've not tried yet.... but I don't have alot of hope for anything 802.11<em>n</em>.....

so does anyone have advice (and, there is something wrong with my phone line; there is too much static for a dial up connection to work without me moving the computer to the kitchen where there simply isn't the space to set up a computer)

---

### Post by Raineer on 2007-07-05
A good resource is madwifi.org 

They might have a solution for one of the cards that will help.

---

### Post by i986 on 2007-07-05
oh yea, and of coarse.  the router for the network (which is going to be replaced with a 1998 Dell that I plan to run FreeBSD on) is a Netgear WGR614 w/ fast ether and wireless g.

---

### Post by mysticrider92 on 2007-07-05
Other than the fact it is wireless-n, I would say the D-Link one is most likely to work wirelessly. I have not seen where anyone has had problems with D-Link wireless cards (I was using one myself until recently). Since the Netgear one is wired, I would say with some setup that would be the better one to use (I just don't like wireless much, just a personal opinion).

---

### Post by i986 on 2007-07-06
well, how do I go about configureing the netgear card?

and does anyone with old shitty 802.11g PCI cards feel like trading?  by what I read, older motherboards will not be able to use modern high powered wireless cards.  So does anyone feel like trading me something I could use?

---

### Post by lbelloq on 2007-07-06
Set a static IP in the wired card and then access the Internet. After that you can install drivers for your wireless cards; ndiswrapper will save you in the wost case.

---

### Post by i986 on 2007-07-06
> **lbelloq said:**
> Set a static IP in the wired card and then access the Internet. After that you can install drivers for your wireless cards; ndiswrapper will save you in the wost case.

just curisoty; is there a ndiswrapper equivlent for FreeBSD?  cause the other machine is a 98 and will be running FreeBSD.... that will be the firewall/router/nic box/light file server, and it needs 2 ethers and one wifi.... and I've tricked my router in the past into thinking that it's assinging IP addresses by having it bind an IP address to a MAC address and setting the IP staticly on the machine.  But I don't know how to get the Mac address of the netgear so that I can trick the router....

---

### Post by lbelloq on 2007-07-06
Dunno if there's a ndiswrapper fro *BSD, try googling it.
Most of wireless routers have an option where you can change the MAC of the WAN port, therefore effectively fooling the modem/router/whatever. Check your Netgear's manual for that.

---

### Post by i986 on 2007-07-06
no no, I mean I need the MAC off of my Netgear gigabit PCI card; so I can enter it into my router as a static route.  The router will not recognize connections for which it did not provide the IP address, so tell the router to always give MAC addy such and such IP and then tell the NIC card with that MAC address that it's IP is always such and such IP....

---

### Post by i986 on 2007-07-06
switch ether cable going to 2005 WinXP with the ether cable going to 2001 Xubuntu.  Now 2005 WinXP won't connect!  And best of all, this means that I'll need to get a new ether cable even though soon there will be no need for pc<->device ether cables as soon I will need only one pc<->pc patch cable... well, one ether cable to connect the firewall to the modem.... but that still leaves 2 spares..... spares are always nice.

---

### Post by i986 on 2007-07-07
well, I tried compiling madwifi; but this the result I got...

isaac@onetwoeight:~/Desktop/madwifi-0.9.3/madwifi-0.9.3$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath/if_ath.o
  CC [M]  /home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath/if_ath_pci.o
  LD [M]  /home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath/ath_pci.o
  CC [M]  /home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/ah_os.o
  HOSTCC  /home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c: At top level:
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c: In function 'main':
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal/uudecode] Error 1
make[2]: *** [/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3/ath_hal] Error 2
make[1]: *** [_module_/home/isaac/Desktop/madwifi-0.9.3/madwifi-0.9.3] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [modules] Error 2

---

### Post by sailor2001 on 2007-07-07
you have static on your line (rf) so you're going to get weird stuff.....get filters for each telephone in your house....

---

### Post by i986 on 2007-07-07
I'm using DSL.... the dial up was just a proposal because I was having troubles getting the other NIC's working.... now I need help getting the wifi working because where this computer is currently isn't where it's going to be for the long run.  It's going to be moved to a different room and using a power drill to run ether cables through the attic just ain't an option for various reasons..... the readout from my command line is when I tried installing madwifi.... and I don't know C very well (I recognize that the syntax isn't much different from js, that's about it... and I don't know js very well either), so I can't do much interms of checking the source code to see what these error messages are talking about.......

---

### Post by TechZilla on 2007-09-22
y9our best bet is with the netgear Gig eth card.  load the r8169 module by typing 

```
sudo modprobe r8169
```

that should do it, then make sure to throw that module name in the /etc/module
file... (which tells kernel which extra modules to load at boot)

im guessing you will have to put that in the file and reboot; unless you can manually ifconfig.

we can deal with the wifi cards later... 
post back w/ your responce

---

