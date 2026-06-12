---
title: "LEAP wireless connection"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by slrohn on 2008-03-31
I'm having issues connecting to a wireless network that uses LEAP authentication in Ubuntu. I can connect to the network using my username and password if I disable networking with the NetworkManager first. Once I lose connection (by logging out or rebooting), connecting again requires disabling wireless and networking.

The NetworkManager tries to connect to the network over and over, which is filling up my log files. This is an example of what is filling up /var/log/syslog (this is a very small portion of what is found in the log, it repeats over and over):

```
Mar 31 18:39:40 user-laptop NetworkManager: <info>  Activation (eth1) New wireless user key for network 'networkName' received. 
Mar 31 18:39:40 user-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 31 18:39:40 user-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Mar 31 18:39:40 user-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Mar 31 18:39:40 user-laptop NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Mar 31 18:39:40 user-laptop NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Mar 31 18:39:40 user-laptop NetworkManager: <info>  Activation (eth1/wireless): access point 'networkName' is encrypted, but NO valid key exists.  New key needed. 
Mar 31 18:39:40 user-laptop NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'networkName'.
```

I don't have a problem with other wireless network connections, just this one that uses LEAP authentication.

I've searched high and low for information to fix this problem, but have yet to find anything useful. I am new to Ubuntu and linux and any and all help would be appreciated.

I'm running Ubuntu 7.10 on a Dell Inspiron 710m.

Thanks.

---

### Post by Whiffle on 2008-03-31
Well, I'd say you've got two options.  The first is to figure out what is wrong with networkmanager, the second is to just switch to another manager (such as wicd)h and use that.  First lets get some more info...

when you log in when w/ network manager disabled, how are you doing that?
what options are you using when you try it with netork manager?

---

### Post by slrohn on 2008-03-31
> when you log in when w/ network manager disabled, how are you doing that?
If connecting to the network isn't working (network manager tries over and over to connect) I can bring up the 'Connect to Other Wireless Network...' dialog box, then disable wireless & networking, type in the Network Name with my username & password for LEAP, enable networking again, and then hit connect.

It's a goofy way of getting around the problem, but so far it's the only way I've been able to get it to work. It will not connect if I don't disable and enable wireless and networking in this manner.

As for the options that I'm using, I'm not doing this from the terminal so I couldn't tell you.

---

### Post by Whiffle on 2008-03-31
> **slrohn said:**
> If connecting to the network isn't working (network manager tries over and over to connect) I can bring up the 'Connect to Other Wireless Network...' dialog box, then disable wireless & networking, type in the Network Name with my username & password for LEAP, enable networking again, and then hit connect.

It's a goofy way of getting around the problem, but so far it's the only way I've been able to get it to work. It will not connect if I don't disable and enable wireless and networking in this manner.

As for the options that I'm using, I'm not doing this from the terminal so I couldn't tell you.

Oh okay, i thought you might be using the terminal or something.

Funny enough, thats sounds similar to the only way I ever got LEAP to work when I was using networkmanager as well.   If I were in your position I'd either live with it till hardy comes out in a couple weeks and see if the newer version of networkmanager is better, or get your hands a little dirty and install WICD.  WICD is a little less polished but functions better for me.  It essentially uses a template to create wpa_supplicant configuration files on the fly, so if you can get it working with wpa_supplicant, you can make it work with WICD.

---

### Post by calraith on 2008-03-31
I concur.  Wicd works smashingly well for LEAP for me.  The biggest drawback is that it doesn't autodetect which driver to use for its wpa supplicant.  If you don't know whether you should be using madwifi, broadcom, wext, etc; or whether your wireless interface is added as wlan0, ath0, wifi0, etc; it might take a little trial-and-error to get the preferences tweaked until you can refresh and see wireless networks.  Otherwise, I like wicd better than Gnome's nm-applet.  Other than working well with LEAP, it also doesn't nag you for a keyring password every time you power your laptop on.

To install, do the following:
```
echo "deb http://apt.wicd.net feisty extras" | sudo tee -a /etc/apt/sources.list
sudo apt-get update
sudo apt-get install wicd
```Installing wicd via apt will automatically remove nm-applet, so there should be no conflict.  You'll also need to add a line to your System --> Preferences --> Sessions on the Startup tab to point to /opt/wicd/tray.py.

---

