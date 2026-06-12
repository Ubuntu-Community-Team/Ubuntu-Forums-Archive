---
title: "Speed Stream USB Modem Issues"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by wehttamb on 2006-12-24
Hi

](*,) 
I have a Seimens SpeedStream 4200 conected to my computer via USB and ubuntu will not detect it. What do I have to do to use it. 

:( PLEASE HELP ME!!!:( 

Thanks

:confused: wehttamb:confused:

---

### Post by MkfIbK7a on 2006-12-24
what happens when you plug it in?

---

### Post by wehttamb on 2006-12-24
When I plug the modem in absolutely nothing happens on the computer but the USB conectivity light on the modem lights up.

---

### Post by MkfIbK7a on 2006-12-24
if you look in the home folder is there a removable media icon?
also does the harddrive light flicker after you plug it in

---

### Post by wehttamb on 2006-12-24
There is no icon in the home folder. Is that /home/ you were talking about. When i plugged the modem in the light flashed.

---

### Post by MkfIbK7a on 2006-12-24
> When i plugged the modem in the light flashed.
at least that means the hardrive knows something is there...

---

### Post by wehttamb on 2006-12-24
In the device manager i found the modem but in the device type section it was unknown. Ubuntu does not know what the modem is but it does detect it.

How can i make ubuntu use the modem. Do I need drivers? If so where will i get them?

Thanks

---

### Post by logos34 on 2006-12-25
assuming you're on the gnome desktop,

what listed on connections tab in network settings?  (system>admin>networking)

You probably have PPPoe dynamic ip, so your usb modem should show up as a 'wired connection address: DHCP'.  Is it enabled (>properties) and set for 'automatic config'?

---

### Post by wehttamb on 2006-12-25
When i clicked on the propeties it wasnt enabled. when i enabled it it wanted dial up settings and would not work. 

What is wrong.:confused:

---

### Post by logos34 on 2006-12-25
sounds like you clicked on 'modem connection' but that's for dial-up...i guess there's no 'Wired Connection' because your modem is hooked up through usb port, not ethernet/cat5/rj-45 jack.  

(Why do usb devices cause so many headaches in linux?) 

You say it shows up in device manager but linux doesn't know what it is.  In the left panel, did you expand the tree all the way under 'usb controller' to the device?  How is it listed there (as opposed to the main window, where it says 'device: unknown')? On the 'device' tab in the main window, what does it say on the lines 'Device type' and 'Capabilities'?  In the advanced tab, what does it say on the line 'info.product' (type, value)?

---

### Post by wehttamb on 2006-12-28
I have bought an ethernet card and now have the modem connected via ethernet. In ubuntu the ethernet connection comes up but it wont work. The ethernet card is a D-Link DFE-528TX connected via PCI. Do i need to install more drivers??? the address of the modem is 10.1.1.1 and when i put that into firefox it says the page cannot be displayed.

PLEASE HELP ME!!!

---

### Post by logos34 on 2006-12-28
That was going to be my very next suggestion...Some swear USB stands for 'unsuitable for broadband'!

Assuming that in Network Settings 'Wired connection Address:DHCP' is CHECKED, and under Properties it is 'Enabled' and set for 'Automatic Configuration (DHCP)' (not Static IP address)... 

Try this:

In Firefox go to
Edit>preferences>advanced>network tab>settings.

'Direct connection to the Internet' should be selected.

Then enter 'about:config' in the address bar.

In the 'Filter' bar enter 'ipv6'

then disable ipv6 by toggling the boolean value to 'true'.

(ipv6 protocol is enabled by default for some strange reason.  It can cause problems and is not really needed--yet at least)

Close and reopen the browser.  

If no connection, open a terminal and enter:

$ sudo ifdown eth0

$ sudo ifup eth0

(or eth1)


If still no connection, shut down the computer and cycle the power on the modem.  Boot the computer.  

It can be tricky getting a connection up.  You might even try turning off the modem and  disconnecting both cables from the modem and the computer.  Then with the modem OFF connect the cable from the wall to the modem and turn it on.  When it syncs up (green) plug in the crossover/patch cable and connect it to your pc.  (Router users have to go through this routine). 

If that doesn't work, just enter the following commands and post the output:

$ ifconfig -a
$ lspci | grep Eth
$ route -n
$ cat /etc/resolv.conf
$ cat /etc/network/interfaces
$ cat /etc/dhcp3/dhclient.conf

---

