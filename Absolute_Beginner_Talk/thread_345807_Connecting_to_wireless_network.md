---
title: "Connecting to wireless network"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by mc.7winkie on 2007-01-24
I've set up all my wireless drivers for my Belkin Wireless G USB adapter and now I'm trying to connect to my wireless network.  I've been working at this for about 2 days and have gained nothing except a little more knowledge of use in the terminal.  I've typed in all the commands they tell you to type in in the tutorial and it doesn't seem to work.  When I type in iwconfig wlan0 it shows me that my ESSID is set to off/any.  This is ridiculous since when I go to the graphical network manager under administration is say that I have my network ESSID set to my network. (On a side note is ESSID the same thing as SSID, just wanna be sure.)  My network does NOT use any filtering except MAC filtering which shouldn't hurt (though I have trued with it off) because I'm writing this using the same computer on Windows.  Also whenever I type in the iwconfig it tells me that all the settings are set to 0 or off.(At least the ones you would be able to change.)  I'm fairly certain that my card is connected correctly because in ndiswrapper it tells me that both the driver and hardware are installed and detected.  I have asked questions about wireless networking before and I usually do not get very much help.  I would really like to switch my primary OS o Ubuntu (Other than for games of course) but I just can't get online.  Any help please?

---

### Post by wimac on 2007-01-24
Try installing wifi-radar makes configuring a wireless network much easier.

---

### Post by macogw on 2007-01-24
I'd install network-manager-gnome 
then in the terminal
sudo gedit /etc/network/interfaces
and put # before everything but lo

ctrl alt backspace
to restart X

then run in the terminal
nohup nm-applet &

(the nohup and the & mean you can close the terminal after the thing loads in your panel)
You should be able to click on whichever wireless network you wanna connect to

---

