---
title: "Wireless problem with Feisty - Intel wireless"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by jtb108 on 2007-04-30
Hello,

New to Linux.  I have been using Edgy Eft for about two months.  My wireless card (Intel(R) 802.11a/b/g,b/g Driver) on a Toshiba Satellite S4342 worked fine under Edgy.

When I up graded to Feisty Fawn my wireless option disappeared.

I can connect via dsl but not wireless.

I would appreciate any advice on how to regain my wireless capabilities.

Thanks for any help.

John Boncheff

---

### Post by csf111 on 2007-04-30
Hi John,
If you open a terminal window;
Applications -> Accessories -> Terminal

Type in 'lspci' (no quotes) and hit Enter

You are looking for a line that says:
Network controller: Intel (blah blah woof woof)
(Sorry I don't have that adapter, BUT look for Intel)

That will tell you the hardware is installed correctly.

If so, then from that same terminal window type

dmesg | grep "Intel"  (USE the double quotes around Intel)

If successful you will see "Detected Intel blah blah woof woof)
(Again look for Intel)

If this is ok, then you need to ensure that the nm-applet is running.

I'll wait until you get caught up......

---

### Post by jtb108 on 2007-05-01
Thank you for taking the time to help me out.

When I type in "Ispci" (no quotes), the response is "command not found"

Please advise.

Thank you,

John B.

---

### Post by jtb108 on 2007-05-01
Hello,

I finally realized the first letter was an "l" in "lspci".  I have found my network controller:  it is an Intel 3945ABG.  Please let me know the next step.

Thank you,

John B.

---

### Post by Inxsible on 2007-05-01
I did a fresh install for Feisty and my Intel 3945 Pro worked right out of the box !
 
What kind of security do you use on your wireless router ?
 
I use plain and simple MAC address filtering and leave the network unsecured...since it allows only my machine's MAC address to pass through. You can however add WEP or WPA to your network

---

### Post by jtb108 on 2007-05-01
I have no special security or unusual set-ups for my wireless card. I have never set anything other than the default settings. 

My wireless connection worked fine in Edgy Eft, then disappeared when I did the upgrade to Feisty Fawn.  I wonder if there is a conflict between something left over from Edgy Eft and Feisty Fawn.

John B.

---

### Post by Inxsible on 2007-05-01
Do you atleast see the network that you are trying to connect to?
 
The difference might just be in how Edgy displayed the icon to you and how Feisty does. I am just throwing ideas here. Can you see a computer icon in the system tray?
 
I never used Edgy, so I don't know how it displayed the wireless connection :(
 
If so, single click on it and click the network you are trying to connect to. It might just be as simple as that, since you say that "lspci" told you that your Intel 3945 was correctly installed.
 
If you do not broadcast your SSID, then you need to click on Connect to Other network and supply the name of your network. Thats what I did.
 
 
Hope that helps !
 
Else post again and we will see what we can do :)

---

### Post by jtb108 on 2007-05-01
When I click on the computer icon, I have two options, wired network and manual configuration.  Under Edgy the wireless showed up as a third option.   This time it doesn't.

John B.

---

### Post by csf111 on 2007-05-01
OK, lspci shows an Intel controller

How about dmesg? "Driver" is loaded?

Looking at the conversation between you and Inxsible
it looks as if there is confusion between NETWORK MANAGER
and the NETWORK MONITOR

From a terminal window, type in "nm-applet" (no quotes)
and hit Enter. Let's see what happens.....

---

### Post by jtb108 on 2007-05-02
Hello,

Thanks again for your help

When I type dmesg, there is about 100 lines of code.  If there is something I should be looking for please let me know.

When I type nm-applet and hit return, nothing happens.

Thanks,

John B.

---

### Post by csf111 on 2007-05-02
OK, however, if you look at my original post:

------------------------------------------------------
If so, then from that same terminal window type

dmesg | grep "Intel" (USE the double quotes around Intel)

If successful you will see "Detected Intel blah blah woof woof)
(Again look for Intel)

------------------------------------------------------------

This command "pipes" the output of dmesg to grep,
which then searches for the string "Intel"

Give that a try please

---

### Post by jtb108 on 2007-05-02
Hello,

Here is what I get for dmesg|grep "Intel"

:~$ dmesg|grep "Intel"
[   25.498270] CPU: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz stepping 06
[   30.010255] Intel(R) PRO/1000 Network Driver - version 7.3.15-k2-NAPI
[   30.010260] Copyright (c) 1999-2006 Intel Corporation.
[   30.382871] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   19.840000] agpgart: Detected an Intel 945GM Chipset.
[   20.400000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   20.496000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   21.024000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   21.024000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   21.024000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection


Please let me know the next step.

Thank you,

John Boncheff

---

### Post by csf111 on 2007-05-02
OK, this is good we are making progress.

Would you please open a terminal and type

 lsmod | grep "ieee" (and hit Enter)

{Please post the output}

[ Your dmesg output indicates the firmware is loaded,
now we have to see if the device drivers are there as well]

When you said you typed in "nm-applet" (no quotes) and
NOTHING happened. Did you mean that you saw nothing
on the screen and the terminal window seemed to "freeze"?

If that is the case then all we have to do is add the 
Notification Area to your panel, and you will be working!

---

### Post by jtb108 on 2007-05-02
Hello,

First point:

 lsmod|grep "ieee"
ieee80211              33608  1 ipw3945
ieee80211_crypt         6144  1 ieee80211
ieee1394              297656  2 sbp2,ohci1394

second point:

When I type nm-applet and hit return, the cursor goes to the next line and blinks.

Thanks,

John B.

---

### Post by csf111 on 2007-05-02
OK.

Open a terminal please and:

 ls /usr/bin/nm-applet (and hit Enter)

[This looks for the NetworkManager applet]

---

### Post by jtb108 on 2007-05-02
Hello,

Assuming that the first letter in "ls" is "l" as in larry, here is what I get.

ls/usr/bin/nm-applet
bash: ls/usr/bin/nm-applet: No such file or directory

Thanks,

John B.

---

### Post by NilsE on 2007-05-02
Put a space between the ls and the /

---

### Post by jtb108 on 2007-05-02
Oops!

Thanks for the heads-up.

Here is what I get:

 ls /usr/bin/nm-applet
usr/bin/nm-applet   (This line appears in green)

Thanks,

John B

---

### Post by TomFumb on 2007-05-02
> **Inxsible said:**
> I use plain and simple MAC address filtering and leave the network unsecured...since it allows only my machine's MAC address to pass through. You can however add WEP or WPA to your network

This really isn't such a great idea, mac address spoofing is easy in Windows and even easier in Linux (though harder with network manager). If you're connected to a wireless network it's not hard for someone to find out your mac address, using aircrack-ng for example, and then a one-line edit to /etc/network/interfaces spoofs your computer. 

Don't give up on wireless security just because it's a hassle! If someone uses your internet connection to break the law, it's your door the police will be knocking on!

---

### Post by csf111 on 2007-05-02
Alright. How about you go up to the TOP panel and
(You know to the LEFT of where the Date is displayed)

 RIGHT CLICK on the panel and Select - ADD TO PANEL
Scroll down to the Utilities area and select NOTIFICATION AREA

 Then open up a terminal window and "nm-applet" (no quotes)

---

### Post by jtb108 on 2007-05-02
Hello,a

I right-clicked on panel,  selected add to panel, found utilities, highlighted "notification area" .  I went to terminal, typed in nm-applet and hit return.  The cursor went to the next line and blinked.

I did it again, this time I clicked on "add" and then typed nm-applet into terminal.  The same response.  The cursor just blinks on the next line.

Thank you,

John B.

---

### Post by csf111 on 2007-05-02
"The cursor blinks on the next line",
 BUT is there any display of signal strength,
 or any type of network activity in the panel
 (A network icon of any time) 
 (Next to where the date is displayed?)

 You should be able to RIGHT CLICK on it
 and ensure ENABLE NETWORKING and
 ENABLE WIRELESS is selected.

 Next take a look at the Sessions

 System -> Preferences -> Sessions

 Look at the Startup tab

 Ensure that Network Manager 
 has a check mark (in the box)

---

### Post by csf111 on 2007-05-02
<Finger Check>
 
 (A network icon of any time)  <<<--- TYPE

---

### Post by jtb108 on 2007-05-02
Hello,

Thanks for sticking with this.

When I clicked on the add panel, and then notification area, a thin gray line was added to the panel.  Nothing else happened.

I run a dual-boot system.  When I log onto to Windows it shows eight wired networks available.

I have the two-computer icon but it only gives 'wired network' and 'manual configuration' as options.  

I am running a wired connection right now.  

In the startup tab, network manager is checked.

Under system, preferences, sessions, current sessions, is the following: 

nm-applet  --sm-disable.

Thanks again.

John B.

---

### Post by csf111 on 2007-05-02
...hmm, and this is a CLEAN Feisty install?
 No mods or tweaks?

Where we are:

a) Hardware is installed (lspci)
b) Firmware is loaded (dmesg)
c) Device Driver is loaded (lsmod)
d) NetworkManager Applet is present (ls /usr/bin)
e) NetworkManager Applet is started (Sessions)
f) Notification Area is present in the panel 

A WIRED connection would show up in the
panel as well. Why does Windows show 8 wired
connections? Do you have 4 NICS?

Are you running this under a VM?

---

### Post by csf111 on 2007-05-02
Wait a minute, are you sure Windows says
 8 WIRED networks or does it say 8 wireLESS networks?

---

### Post by macogw on 2007-05-02
Are you right or left clicking?  Right click.  It should say:
Enable Networking
Enable Wireless
Connection Information
About

Make sure "enable wireless" is checked.  Also, make sure you didn't press the "turn the wireless card off" button on your laptop's keyboard.  Try hitting it and seeing if it turns back on.

And yeah, the terminal will just blink the cursor.  There isn't meant to be any output.  You can type a & after the command to make it so you can close the terminal after it starts running.

---

### Post by jtb108 on 2007-05-03
Hello,

Thanks to everyone for their suggestions.

Answers to questions:

1) The installation of Feisty was done by clicking on the upgrade star that appeared on the panel.

2)  My bad:  8 wireless connections when I log onto Windows.

3)  When I right click on the two-computer icon, I get enable networking and connection information.  There is no wireless option.

John B.

---

### Post by n00utkast on 2007-05-07
Hi, I am having the same problem, with the nm-applet when i added to the panel its just a gray divider that i can move around when i left click on it and read "about" it does say its "notification area" but i don't see any option for connection or anything.

When I typed in "nm-applet" into terminal this is what I got:

nick@nick-laptop:~$ nm-applet

(nm-applet:15304): Gtk-WARNING **: Unable to locate theme engine in module_path: "candido",

I am just spend two days on linux...so i have no clue how to fix that any help would be great. Thanx

---

### Post by csf111 on 2007-05-08
Hang in there jtb108.

Have you "modified" the network settings?
When you indicate that the "two computer icon"
only has 'wired network' and 'manual configuration'
as options, then that would suggest your wireless is
not working, BUT the other steps we took:
a) Hardware is installed (lspci)
b) Firmware is loaded (dmesg)
c) Device Driver is loaded (lsmod)
d) NetworkManager Applet is present (ls /usr/bin)
e) NetworkManager Applet is started (Sessions)
f) Notification Area is present in the panel

Would suggest it is. 

If you go to 
System -> Administration -> Network you should
have Wireless Connection with a minus sign next 
to it, with Roaming Mode Enabled under it.

As a simple explanation, nm likes DHCP........

---

### Post by csf111 on 2007-05-08
n00utkast - 

Do you have gtk2-engines-pixbuf installed?
Sounds like more of a theme problem, then wireless
(at this point)

From a terminal "sudo apt-get install gtk2-engines-pixbuf"
(no quotes) and then let's see what happens

---

### Post by jtb108 on 2007-05-09
Hello,

Thanks for all your efforts.

You wrote:

"If you go to System -> Administration -> Network you should
have Wireless Connection with a minus sign next
to it, with Roaming Mode Enabled under it."

When I go to this point I only have two options:  "Wired connection  address  dhcp" and "modem connection      this network interface is not configured"

Somehow it doesn't find my wireless card.

Thanks again.

John B

---

### Post by csf111 on 2007-05-09
Yes, I agree that it doesn't find your wireless card.

(Interesting that all our other steps seemed to indicate success)

With that said, I think we are in the land of diminishing returns here.

As you mentioned you had migrated versions via the gui; would it be 
possible for you to reinstall from CD? 

I have experienced anomalies like this myself. Nuke it from Space!

---

