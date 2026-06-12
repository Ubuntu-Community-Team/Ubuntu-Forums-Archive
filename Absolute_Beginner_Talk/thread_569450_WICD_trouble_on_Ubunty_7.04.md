---
title: "WICD trouble on Ubunty 7.04"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by Tac2 on 2007-10-07
Hello everyone.

After trying out the Ubuntu 7.04 LiveCD I decided to go ahead and install it as a dual boot with Windows XP (I've never used Linux before). First challenge was the partitioning part, which I eventually overcame - the next is making it work with my wireless network at home.

I am using a Netgear WG311v3 (wireless PCI) in my Dell desktop (Dimension 5150). I found that Feisty does not have a native driver for this card, so I downloaded and installed ndiswrapper 1.48. I first tried to install it using the Windows XP drivers that came with the card, but couldn't get this working, so instead I downloaded and installed the Marvell  mrv8335driver, which seems to work (I get "driver installed, device present" when typing "ndiswrapper -l" in terminal). I went into Network Manager, and was able to see the wireless networks that broadcast their SSID. 

While troubleshooting ndiswrapper and the driver I read a lot of threads that suggested getting WICD instead of using Network Manager, as it's supposedly easier to use and works with WPA encryption. So I went ahead and uninstalled Network Manager, downloaded and installed WICD 1.3.1. However, at this step I got stuck. When I open WICD I simply get the message "No wireless network found". Which is odd, as I typed some command in terminal (I forgot which, sorry) and it showed a list of available wireless networks (there's a bunch of them). I have tried uninstalling and then installing WICD again, but I simply get the same message. In Preferences it's set to use wlan0 as wireless interface (which is the logical name I get when I type "lshw -C network" in terminal) and to use ndiswrapper as WPA Supplicant Driver. 

It should be said, that when I go to System -> Administration -> Network, it does show a Wireless Connection.

So - any idea what the problem with WICD could be?

---

### Post by julian67 on 2007-10-07
I've used wicd and network-manager applet and there are not that many situations when wicd is better. Network-manager and nm-applet were previously rather badly implemented in Ubuntu and wicd was a very nice alternative. Since Ubuntu 7.04 network-manager implementation in Ubuntu is massively improved and can now deal with different adapters using respectively DHCP and static address at the same time and some other   improvements. I'd suggest go back to network-manager unless you run a desktop environment that doesn't support the applet (fluxbox for example). nm is very simple on the surface and does clever stuff under the hood, like remembering which network you preferred last time (i.e. when using wi fi and multiple networks available). I use nm on my laptops and it's the best. On my desktop i also prefer nm over wicd because wicd didn't let me run 2 network adapters (essential for sharing a connection), it was either or. 

*If you only need to connect to one network* you can easily configure it and then set nm-applet so it doesn't appear in the tray (network manager will just do the work in the background). Or you can do without either nm or wicd and configure your adapter in the terminal.

---

### Post by Tac2 on 2007-10-07
Thank you for your reply. 

I suppose I just might go back to Network Manager. Will Network Manager work with WPA encryption, with a router that does not broadcast ESSID?

And how would I configure my adapter in the terminal?

---

### Post by compwiz18 on 2007-10-07
If you just need one network:
[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539) that's an excellent post for setting it up.

Also, if memory serves, ndiswrapper + hidden networks = lots of problems.

---

### Post by kevdog on 2007-10-07
Id install the 1.34 version of WICD -- the "stable" version is old and actually has a lot of problems "makes you wonder why they call it stable".  Did you follow all the installation instructions by removing network manager??

---

### Post by julian67 on 2007-10-07
hidden essid: I don't know if you have control of the router but if you do then you might as well broadcast the essid. Hiding it doesn't offer any real advantage or protection and if hiding the essid gives problem with ndiswrapper then you're better off with it visible. Anyone who is really interested can see your "hidden" network anyway. 

If wicd is installed from the deb then network manager is correctly uninstalled. There shouldn't a problem to install/re-install/uninstall wicd or network-manager multiple times on a working system.

---

### Post by Tac2 on 2007-10-07
Thanks for the suggestions guys. I decided to go ahead and broadcast the ESSID.

I decided to try out this guide [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539) - and it's working fine, except when I have to restart the network: When I type "sudo /etc/init.d/networking restart" it returns "command not found". Hmm?

---

### Post by kevdog on 2007-10-07
Are you still using wicd??

I think with wicd its:
sudo /etc/init.d/wicd restart

I think:confused:

---

### Post by Tac2 on 2007-10-07
No, I uninstalled WICD... and I don't have Network Manager either, heh. That could be the problem? I feel silly

---

### Post by julian67 on 2007-10-07
Just re-install network-manager-gnome and you'll quickly be back to Ubuntu default and it will only take a couple of minutes to have your encrypted wi-fi up.

---

