---
title: "[SOLVED] I want to connect only to 1 available wireless signal."
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by stevelasvegas on 2007-09-20
My Network Manager Applet shows several available wireless network connections. I only want to automatically connect to my listed network. Most of the time, that's how it works. Sometime, for whatever reason (I don't care) it doesn't automatically connect to my network, but instead connects to another 'open' available network. I don't even realize that I have connected through my neighbor's network.
I want to automatically connect only to my network, and still retain the ability to manually connect to any available network.
Any suggestions?
Thanks

---

### Post by Chris S. on 2007-09-20
I managed this with wpa_supplicant.  It allows you to specify the ESSID of each network you want it to automatically connect to.  This will prevent it from connecting to just any open network (unless you tell it you want to).

---

### Post by w4ett on 2007-09-20
You might like Wicd:

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by stevelasvegas on 2007-09-20
I am installing wicd and I see that it is going to remove network manager. That's how I connect now and it's working. What if I run in to problems for whatever reason after making the change. How to I get back to where I was. Uninstall, reinstall? Backup a section to restore from? 
(Sorry, relative noob coming from Windows)

---

### Post by w4ett on 2007-09-20
I use it...no problems so far in 4 months on 5 different machines....it does the same as the network manager with extended capabilities......to reinstall the original Net Manager, you can use the Synaptic Package Manager.

---

### Post by mridkash on 2007-09-21
I connect to a wireless using network manager. 
A click on the system tray icon or in terminal sudo network-admin brings up a window listing network devices.

For wi-fi, i choose wireless and select properties then disable the roaming mode. In the network name(ESSID) I select the wireless connection I want.

I hope it solves your problem.

---

### Post by stevelasvegas on 2007-09-21
I installed wicd. I could not get an ip address when I tried to connect to my wpa network. I was able to connect to the neighbor's open network.
mridkash - that's what I tried to do before installing wicd, but after un-checking roaming mode, network manager would only ask for a wep password, not a wpa. Although, at some time it must have allowed me to set a wpa, because that's what is was using. Hmmmm

---

### Post by stevelasvegas on 2007-09-21
Oops! My bad. I found the drop down arrow to configure the WPA on my listed network and now it's working.
Thank you all for your suggestions and advice.

---

