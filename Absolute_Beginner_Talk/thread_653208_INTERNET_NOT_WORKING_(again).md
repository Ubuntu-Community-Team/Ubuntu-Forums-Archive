---
title: "INTERNET NOT WORKING (again)"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by akash238 on 2007-12-29
i had to use my sisters laptop just to on the internet
i dont know why my internet in ubuntu doesnt work

i have a dsl modem that is connected to a dlink router
and the dlink router is connected to my computer
my internet works on windows vista

when i first booted into ubuntu it connected to the internet 
while i was on the internet there was no network connection

---

### Post by akash238 on 2007-12-29
i need some help
HELLOooooooooooooooooooooooooooo

---

### Post by ugm6hr on 2007-12-29
How is your computer connected to the router (i.e. wifi or ethernet)?  

Which version of Ubuntu?

On your computer - post the result of:
```
lspci
lshw -C network
ifconfig
```

---

### Post by RomeReactor on 2007-12-29
Hi. What version of Ubuntu do you have? please open a terminal (Applications->Accessories->Terminal) and enter the following:
```
ifconfig -a
```
and
```
route
```

This is a wired connection to the router, correct?

---

### Post by akash238 on 2007-12-29
my router is connected via Ethernet so yes it is wired 
and thank you for the code

---

### Post by artinla on 2007-12-29
I had to disable ipv6 to get mine to work.  Search this forum for it, there are several threads that explain how.

---

### Post by RomeReactor on 2007-12-29
> **akash238 said:**
> my router is connected via Ethernet so yes it is wired 
and thank you for the code

Do you mean that your PC is connected to the router through an ethernet cable? or are you trying to connect to the router with a wireless card? are you still unable to connect to the internet?

---

### Post by akash238 on 2007-12-29
yes my pc is connected to my router through an Ethernet cable 
now ubuntu 7.04 wont even detect my router
and no im still not connected to the internet 
i was on windows vista a few minutes ago and the internet was working fine
:confused::confused::(

---

### Post by RomeReactor on 2007-12-29
Please post the output of the commands **ugm6hr** and me gave you.

---

### Post by jerrynewt on 2007-12-29
Did you try unplugging the power cord from your router for about ten seconds, then plug it back up again and let it reset. Then run "ifconfig" (without the quotes)  in terminal and see if your router assigned the comnputer an ip address. If so you should now be able to get on the internet.

---

### Post by akash238 on 2007-12-29
akashvikas@ubuntu:~$ ifconfig -a 
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0           
	  inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:5404 (5.2 KiB)  TX bytes:5404 (5.2 KiB)
akashvikas@ubuntu:~$ route 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
akashvikas@ubuntu:~$

---

### Post by akash238 on 2007-12-29
akashvikas@ubuntu:~$ ifconfig -a 
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0           
	  inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:5404 (5.2 KiB)  TX bytes:5404 (5.2 KiB)
akashvikas@ubuntu:~$ route 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
akashvikas@ubuntu:~$

---

### Post by jerrynewt on 2007-12-30
Go to System>Administration>Network and see if your wired connection is configured. If not click on it and go to properties. Mine is set to static ip, but you can check the "Enable Roaming" box, close the window, hit Control>Alt>Backspace to restart your session and see it if works then.

---

### Post by ugm6hr on 2007-12-30
@akash238:
The ifconfig output does not show any network interface - only *lo*.  Your network card should show as *eth0* in the list.  Hence it appears that it is not being detected properly.  Make sure the ethernet cable is plugged in when you turn the computer on.

Have you edited any config files?

You still haven't given the output from:
```
lspci
```

---

### Post by whosmatt on 2007-12-30
Sounds like you need to disable power management on the NIC in windows.  Not sure about Vista, but if you go to device manager in XP, the NIC will probably have a power management tab, and there's a checkbox for "allow Windows to turn off this device to save power."

I had the same problem and it was because every time I shut down windows, it would disable the NIC and wouldn't re-enable until I booted windows again.

-Matt

---

### Post by kleo skywalker on 2007-12-30
Akash, I suppose you're using an MTNL or BSNL broadband internet connection.

This is how to get it working:

Go to System-->Administration-->Network. Click on the "Properties" button next to "Wired Connection". Uncheck the "Enable roaming mode" box, set Configuration to "Static IP". Set the IP Address, Subnet Mask, Gateway Address. Back in the "Network Settings" menu, set DNS servers (primary and secondary). If you don't know what to put in these boxes, just call your local Junior Engineer (JE) and ask for them.

In the Terminal (Applications-->Accessories-->Terminal), run this command

```
sudo pppoeconf
```

Once done, reboot. You should be able to connect to the internet.

If you're using MTNL Triband, see my post in [this thread]("http://ubuntuforums.org/showthread.php?t=619110") for the values you need to enter.

---

### Post by akash238 on 2007-12-31
> **kleo skywalker said:**
> Akash, I suppose you're using an MTNL or BSNL broadband internet connection.

This is how to get it working:

Go to System-->Administration-->Network. Click on the "Properties" button next to "Wired Connection". Uncheck the "Enable roaming mode" box, set Configuration to "Static IP". Set the IP Address, Subnet Mask, Gateway Address. Back in the "Network Settings" menu, set DNS servers (primary and secondary). If you don't know what to put in these boxes, just call your local Junior Engineer (JE) and ask for them.

In the Terminal (Applications-->Accessories-->Terminal), run this command

```
sudo pppoeconf
```

Once done, reboot. You should be able to connect to the internet.

If you're using MTNL Triband, see my post in [this thread]("http://ubuntuforums.org/showthread.php?t=619110") for the values you need to enter. i dont have a wired connection option 
am i supposed to???:confused:

---

### Post by RomeReactor on 2007-12-31
Yes, if you are connected via ethernet cable to the router you should have that option in Network Manager. Have you changed anything in the configuration of the router recently? please run:
```
lspci
```
as ugm6hr suggested earlier and post the output. If you can connect in windows but not on Ubuntu then I don't think it's a problem with the ethernet cable. If you have an nForce chipset on your motherboard, or if it's a particularly rare one, then Ubuntu might be having problems detecting the ethernet connection.

---

### Post by kleo skywalker on 2008-01-01
> **akash238 said:**
> i dont have a wired connection option 
am i supposed to???:confused:

Yes. Try doing what RomeReactor says. Once your Ubuntu detects a wired connection, you can follow those steps.

---

### Post by flyingtiger on 2008-01-31
> **jerrynewt said:**
> Did you try unplugging the power cord from your router for about ten seconds, then plug it back up again and let it reset. Then run "ifconfig" (without the quotes)  in terminal and see if your router assigned the comnputer an ip address. If so you should now be able to get on the internet.

If the Vista PC is connected to the Internet why would you suggest that he re-boot the router? The router is apparently giving the Vista PC access to the Internet.

The problem is not the router ... the problem concerns the Ubuntu PC. Something is not configured properly. He says that the OS was able to access the Internet for updates, therefore the NIC is not the problem. I'm sure it has something to do with the Ubuntu PC Network settings under System>Administration>Network.

---

