---
title: "How automatically select network adapter on boot?"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by Fanatico on 2008-01-10
I have computer which run Ubuntu 7.10. The computer has two network interfaces: PCI Ethernet card and wireless USB stick. By default after booting PCI Ethernet card is always enabled.

I want instead that after boot PCI Ethernet card will be disabled by default and Wireless USB adapter:
1) Enabled
2) Configured with static IP address
3) Automatically connect to specified wireless network

Please explain how can I configure that.

Thanks

---

### Post by julian67 on 2008-01-10
Disconnect the ethernet cable. Network manager, given the choice of available wired or wireless networks, will prefer the wired network. 

If you manually select a particular wireless network in preference to others when several are available then network manager should remember this preference and  subsequently it will try to connect to that network (if it is available) rather than the others. 

Easiest and best way to get a static IP address is to set this on the router, either by mac address or by host name. You need admin rights on the router to do this. If the router has DHCP enabled and you assign a static IP address only in your PC's OS there is always the chance that this same address has already been assigned to another PC (assuming your PC is not the only one on the LAN).

edit: Alternatively you can uninstall network manager and in its place use wicd. Wicd can be easily set up to automatically connect to specific networks and conversely to not connect automatically to others.  It would be very easy to set your preferred wireless network to connect automatically but have your wired network only connect when you choose.  No need to disconnect the ethernet cable.

---

### Post by Fanatico on 2008-01-13
Bump

---

### Post by julian67 on 2008-01-13
If this didn't work then you might want to say what didn't work, and why....it might enable someone else to actually have a clue what you did and see a way to help you out.  Simply writing "Bump" is not a great way to describe a situation or get constructive advice. Good luck with any help you get from other forum members.

---

### Post by Kzin on 2008-01-13
I cant spell out the steps, but I can tell you exactly where you need to go for it.
Goto a terminal and type
```
man interfaces
```
I am pretty sure this will give you fairly straightforward instructions for this exact procedure.

---

### Post by Fanatico on 2008-01-14
> **julian67 said:**
> If this didn't work then you might want to say what didn't work, and why....it might enable someone else to actually have a clue what you did and see a way to help you out.  Simply writing "Bump" is not a great way to describe a situation or get constructive advice. Good luck with any help you get from other forum members.

Sorry, you are absolutely right. I wasn't very descriptive. When I was asking my question I hoped to get info about what configuration file I have to edit (I assume /etc/network/interfaces), example of such files and details about how to disable wired interface and enable wireless, etc. All examples I saw so far dealt with configuring only one interface (wired or wireless) From there I usually open man pages and search for details.

Thanks

---

### Post by amingv on 2008-01-14
Well, if you wish to manually set your card in /etc/network/interfaces, a basic configuration may be as follows:

```
auto wlan0
iface wlan0 inet dhcp
wireless-essid <essid>
wireless-key <hex_key>
```

The 'auto wlan0' line will make it come up at boot-time. Of course, change wlan0, <essid> and <hex_key> to whatever corresponds.
Also, make a backup of the file before modifying it:

```
sudo cp /etc/network/interfaces /etc/network/interfaces.backup
```

More information in how to customize your interfaces file in

```
man interfaces
```

A possible drawback to this: some network managers will not handle the connection if you choose to manually set it up.

EDIT: Ohh!!! I almost forgot; do NOT delete the configuration from any other interface in the file. It does not matter if many of them are up at the same time. But if you do not wish them to come up at boot-time you may comment the 'auto <device>' line, just don't delete it. Or you may turn it off with:

```
sudo ifdown <interface>
```

---

### Post by julian67 on 2008-01-14
If you want to do it by editing config files, like amingv said, you will have to uninstall network manager. You will then have the choice of learning wpa_supplicant and either memorising its syntax or writing/finding some shell scripts to enable you to connect to protected (wep or wpa) wireless networks. It's a pita. Second choice is to install Wicd which will allow you to do exactly as requested and retain a flexible and easy to use tool for managing different connections....or stay how you are, use network manager and follow advice as outlined above.

Despite the reputation of Linux not everything is best done via cli these days. Some distros such as openSuse have gui admin tools which will overwrite the changes you make in certain config files......you are *supposed* to use the gui! Network manager is one of those tools that combines several tedious (and sometimes complex) cli tasks into (to the user) a superb simple applet that makes all kinds of connectivity as easy as possible. But if you want to edit the interfaces file you had better uninstall Network manager first or you will have broken your networking ability.  I would also uninstall network manager if my wireless adapter was not fully supported (i.e. needed ndiswrapper) but otherwise it's a great tool that does a lot of boring work for you.

---

### Post by Fanatico on 2008-01-15
Amingv wrote: "A possible drawback to this: some network managers will not handle the connection if you choose to manually set it up."

Can anyone explain why this might happen?

I wonder why should I uninstall network manager before editing /etc/network/interfaces file?
Is network manager changes the very same /etc/network/interfaces file after all?
May be I am wrong, but I heard that it is impossible to uninstall network manager ...

I do use the my wireless card (Edimax USg 7318) configuration utility. (This utility by the way doesn't support static IP addresses:( ) This is one of the reasons why I don't want to use Network Manager which comes with standard installation of Ubuntu. Besides that I didn't find Network Manager very user friendly.

---

### Post by amingv on 2008-01-15
If they both worked at the same time, basically you would be getting the same as if you played your MP3s and a movie at the same time. Neither work would get properly done and you wouldn't be able to enjoy neither as well.

Actually you do not need to uninstall the network manager, in my case I just disabled it so it doesn't come up at startup. But if you decided to uninstall it or needed the 1.5MB, it is quite possibe, and souldn't be any more difficult than (if you're using KDE anyway):

```
sudo apt-get remove knetworkmanager
```

Finally; although this setup works flawlessly for me (plus that's one less icon in my taskbar), it DID take much headache at the begining (mainly because of ignorance), and it is not advisable if you are going to be roaming from one network to another (there's some ways to configure more than one ESSID, but I don't quite know them).

Overall I would suggest you to follow julian67's advice and try wicd; and only use this setup as a last resort or if you have the time/mind to tinker.

---

### Post by julian67 on 2008-01-15
network manager requires the /etc/network/interfaces file to be in a particular form; after you manually edit that file network manager will not work. It is perfectly possible to uninstall network manager and you can then manage your connectivity by manually editing config files if you wish, or by using an alternative gui tool like wicd.  Imo if you connect to different protected wireless networks and also sometimes use a wired connection (typical laptop use) you need a good gui tool to automate or semi automate the process. There is absolutely no advantage in doing this by hand in these circumstances and there are plenty of disadvantages.  You can do everything you need to do with either of the gui tools (network manager or wicd) but you will likely struggle to do the same things via the terminal.  If you have a single connection (wired or wireless) it might be simpler to use the terminal the one time and then forget it, but tools like wicd and nm are specifically designed to deal with the situations you outline, you can even think of them as a custom solution, seems silly to me to be dispensing with the ideal tools for no apparent reason.  Again if you absolutely need a static IP adress then set it on the router, not the PC.

---

### Post by Fanatico on 2008-01-16
Thank all of you guys for detailed explanation.

I will definitely take a second look at gui configuration tools like Network manager and wicd. The main reason why I didn't want to use these tools was that I assumed that these tools might not support "fine tuning" for specific adapter, like putting adapter in monitor/promisc mode, static IP addresses etc.

Anyway I will definitely take a look today again on these utilities.

By the way as I understood neither Network Manager, nor wicd supports configuration static addresses. Is there proper way to configure static IP addresses only via router?

Thank you

---

### Post by julian67 on 2008-01-16
Using either wicd or nm you should be able to assign static ip address without any problem...click on the nm applet and select manual configuration.  In Wicd gui you just use the settings options for that particular interface....you can have different settings for each network and/or interface. If you're using monitor mode probably you need to uninstall network manager. I don't know how wicd works with monitor mode, haven't tried it.  You also need to check that the driver you're using supports monitor mode as sometimes this is not enabled in the binary drivers packaged with Ubuntu so you might need to compile your own.

---

