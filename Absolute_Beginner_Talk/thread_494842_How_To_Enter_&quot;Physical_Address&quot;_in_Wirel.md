---
title: "How To Enter &quot;Physical Address&quot; in Wireless Network"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by bme on 2007-07-07
I was informed by our university IT department that we are a "windows only" network thus no help can be provided on Linux based systems such as my laptop.
There is an on line instruction where a windows pc can be setup to use the university wireless network in which we key in a 12 digit character "Physical Address" which is displayed when we issue the "ipconfig.exe" command from the windows command line. It also says that the network is based on 802.11g...
I don't believe that linux cannot be used here thus my question is-How to connect to the wireless network in Ubuntu?

---

### Post by tartarian on 2007-07-07
To set the physical address for a wireless network, you need to use the command 
```

sudo iwconfig ap <YOUR_ACCESS_POINT>

```

or if that doesn't work, try editing /etc/network/interfaces and add the line
```

wireless-ap <YOUR_ACCESS_POINT>

```
(Make sure you put that under the wireless interface though!

Good luck!

(friendly note: Wireless is pretty tricky to set up in Ubuntu, but it can be done. You just need a lot of patience!)

---

### Post by bme on 2007-07-07
If that is the case then would it also be difficult to use Ubuntu in free wireless networks such as in Airports?
I use windows in those hotspots and I  did not have to do any config..It just connects automatically...
But security is a concern to me when using such free networks su I want to try out Ubuntu...

---

### Post by tartarian on 2007-07-07
I imagine that it would be quite difficult to use hotspots, but it would probabl depend on wether your card supports scanning (iwlist scan) 
Thats total guess work though, you'd probably be better trying it out. 
I know for a fact that Kubuntu is much more wireless friendly, it worked for me first time and has its own GUI which shows available networks (quite similar to windows)
And if you're after securit then Ubuntu's the place. Hardly any virus's, no  need for a firewall and generally faster surfing :)

If you;ve any more questions, post back, bt it might be 45 mins or so before I reply.

---

### Post by MikeDX on 2007-07-07
> **tartarian said:**
> 
(friendly note: Wireless is pretty tricky to set up in Ubuntu, but it can be done. You just need a lot of patience!)

I use ubuntu with several wireless networks on a day to day basis. just install wifi-radar from add/remove programs and use that. Alternatively on feisty it has wifi stuff out of the box.

---

### Post by Inxsible on 2007-07-07
> **bme said:**
> I was informed by our university IT department that we are a "windows only" network thus no help can be provided on Linux based systems such as my laptop.
There is an on line instruction where a windows pc can be setup to use the university wireless network in which we key in a 12 digit character "Physical Address" which is displayed when we issue the "ipconfig.exe" command from the windows command line. It also says that the network is based on 802.11g...
I don't believe that linux cannot be used here thus my question is-How to connect to the wireless network in Ubuntu?
The physical address of a wireless device is the same no matter what OS you use. If your question is how to get it in Ubuntu, you can do ```
ifconfig
``` Look for your wireless device (mine is eth1) and in that the address following the word "HWaddr" is what is your physical address. 

if you log into windows and do an ```
ipconfig /all
``` at the command line, you will get the same hardware address for your wireless device.

---

### Post by bme on 2007-07-07
Inxsible,
ok I know my physical address....
How to setup in Ubuntu-where to place the physical address? That is my question....
I am new to Ubuntu so please "step by step" instruction?

Thanks !

---

### Post by Inxsible on 2007-07-08
> **bme said:**
> Inxsible,
ok I know my physical address....
How to setup in Ubuntu-where to place the physical address? That is my question....
I am new to Ubuntu so please "step by step" instruction?

Thanks !
you do not have to setup anything in Ubuntu with the hardware address. You have to set it up in the wireless router of the network you are trying to access.

---

