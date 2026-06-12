---
title: "Help with T43 Wireless and Video"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by zcrxsir88 on 2007-02-02
Hey all,

I just loaded Edgy in and everything seems to be working.  Having a couple probelms though.  The graphics card works (ATI Mobility 300)  But its still very very jerky.  I dont think i have the proper driver installed, but I went to ATI's website and tried to run the auto install (didnt work)
I couldnt convert the .rpm package with alien.  Help please!?

Second is with the wireless connection.  I understand needing to put in the SSID/Password.  But I want to scan for wireless networks without having to know what the SSID is.  But in the Network Settings I cant enable the connection without the SSID


Help!?!?!?  

V/R

-V

---

### Post by mikewhatever on 2007-02-02
To scan for wireless networks, you need to install a network manager. Gnome network manager works fine, but there are more if needed. The following command would install it
```
sudo apt-get install network-manager-gnome
```
Then you'll need to disable the current wireless configuration. 
```
gksudo gedit /etc/network/interfaces
```
will open a window with current network info. If there is an error message in the terminal, disregard it. Comment out (put # in the beginning of the line) the lines with network name and WEP if any, and save. After rebooting, you'll have another icon in the panel, and should be able to see other networks by clicking it.

---

