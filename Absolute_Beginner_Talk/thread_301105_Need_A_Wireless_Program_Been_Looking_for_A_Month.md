---
title: "Need A Wireless Program: Been Looking for A Month"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by meseleto on 2006-11-16
In order to get on my school's secured network I need a connection manager that will allow me to do this:


    1) Create a new network profile
    2) Enter GrinnellCollegeWireless as the ssid
    3) Security Type: IEEE 802.1x Authentication
    4) Access Point authentication: WPA
    5) Data encryption: TKIP
    6) EAP type: PEAP
    7) Authentication protocol: MS-CHAP-V2
    8) Enter user credentials – Check “Prompt for username and password.”
    9) Check Validate server certificate **This is important to guard against connecting
       to a rogue access point**
           - allow any Certificate Authority
           - server name: grinnell.edu
           - Select the Domain name must end in specified name button

Been Looking for over a month. I tried wlassistant but that asks me for a WEP key which the IT guy said it shouldn't. any ideas?? :mad:

---

### Post by Marsolin on 2006-11-16
Have you tried [WiFi-Radar]("http://linuxappfinder.com/package/wifi-radar")? It should do what you want.

---

### Post by meseleto on 2006-11-16
No i'll go home and try it. thanks

---

### Post by meseleto on 2006-11-16
Still doesn't work. It doesn't allow me to choose the authentication method and there is no option to prompt me for a username/password. Need another app.

---

### Post by compuguy1088 on 2006-11-16
> **meseleto said:**
> In order to get on my school's secured network I need a connection manager that will allow me to do this:


    1) Create a new network profile
    2) Enter GrinnellCollegeWireless as the ssid
    3) Security Type: IEEE 802.1x Authentication
    4) Access Point authentication: WPA
    5) Data encryption: TKIP
    6) EAP type: PEAP
    7) Authentication protocol: MS-CHAP-V2
    8) Enter user credentials &#8211; Check &#8220;Prompt for username and password.&#8221;
    9) Check Validate server certificate **This is important to guard against connecting
       to a rogue access point**
           - allow any Certificate Authority
           - server name: grinnell.edu
           - Select the Domain name must end in specified name button

Been Looking for over a month. I tried wlassistant but that asks me for a WEP key which the IT guy said it shouldn't. any ideas?? :mad:
What I think you are more looking for is network manager, which can be installed by pasting these commands into the terminal

```

sudo apt-get install network-manager-gnome network-manager-pptp

```

This should (if your using GNOME as your desktop) come up on the next reboot, and supports WPA2. Though from what 7, 8, and 9 mention, is more to seem like a type of vpn like setup after connection, the network-manager-pptp should do the trick (I know its in Edgy, though I don't know if it is in Dapper). Hopefully network manager will at least get you to connect to your school's network, but for the other parts, I'm not quite sure how to go by that...

---

### Post by meseleto on 2006-11-16
This is what i got

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package network-manager-pptp
root@me-laptop:/home/tolcha#

---

### Post by meseleto on 2006-11-16
Bahh. This is BS i've been workin at it for over a month. I guess it's time to switch to Windowx Xp. It's been fun *wave*

---

### Post by Marsolin on 2006-11-16
Did [wpasupplicant]("http://linuxappfinder.com/package/wpasupplicant") get installed along with [WiFi-Radar]("http://linuxappfinder.com/package/wifi-radar")? It handles the WPA piece.

---

### Post by meseleto on 2006-11-16
> **Marsolin said:**
> Did [wpasupplicant]("http://linuxappfinder.com/package/wpasupplicant") get installed along with [WiFi-Radar]("http://linuxappfinder.com/package/wifi-radar")? It handles the WPA piece.

Yes. it still didn't work. the problem is that there is no place to choose the security type/authentication and no place to check an option for promtping the user to enter the username/password. I'm sooooooooo frustrated.

---

### Post by tubasoldier on 2006-11-16
> **meseleto said:**
> Bahh. This is BS i've been workin at it for over a month. I guess it's time to switch to Windowx Xp. It's been fun *wave*

BYE. Nice to see you.

---

### Post by meseleto on 2006-11-18
So nobody on this entire forum knows enough about networking and the applicatios on ubuntu to help me? Is there a number I can call for expert advice. I don't really care if I have to pay b/c this problem is taking up way to much of my time and I need it resolved immediately.

---

### Post by videodrome on 2007-01-05
And so this thread illustrates why Linux is NOT ready for prime time. Yet another user lost back to Windows. Why? Because there isn't one usable wifi application in existance, and no one can help this guy. I don't know what works the worst: rutilt, wifi-radar, or network-manager? Wireless support is integral to the success of Ubuntu, and so far it isn't even close.

---

### Post by ArgentSilver on 2007-01-05
The problem is that there is (as far as I know) no good gui interface to get what he wants done. For WPA connections, you need to use wpa_supplicant, which is a command line utility, and requires manual setup of its configuration file. I think it will do what he requires (which is much more advanced than the simple WPA access I use on my home WAP!). Then you can use Wifi-radar as a gui front-end to launch the WPA connection procedure. That's what I'm using. This is one area where Linux is not even close to the ease of WinXP. It has to be a labor of love, or else why put up with the difficulty of the process!

---

### Post by videodrome on 2007-01-07
But does it still need to be a labor of love? "It just works" is what most users want, not 7 different wifi apps, none of which work right. If all developers would just work on one or two, and actually made them work, then non-free OS's might actually have something to worry about.

---

### Post by macogw on 2007-01-07
Use nm-applet (the network manager) then choose "connect to other wireless network" and enter your info.  The username/password stuff sounds like a VPN client thing.  For that I'd use vpnc and vino.  

My school claims Linux and FreeBSD users can't use the school's wireless because they only give out Windows and Mac binaries for Cisco's VPN.  All you do is unzip the Windows .exe and get the secret passwords out of there, decode the encrypted one (someone wrote a decoder, it's online now), and plug them into vpnc, and bam! Linux users have wireless on a "no wireless Linux" campus.  The guys at the Engineering School didn't believe it was possible, but I told them my friend's little bro did it on Fedora and another friend did it on FreeBSD.  I haven't gotten around to it on mine.  I almost always have a wired connection handy.

---

### Post by macogw on 2007-01-07
> **ArgentSilver said:**
> The problem is that there is (as far as I know) no good gui interface to get what he wants done. For WPA connections, you need to use wpa_supplicant, which is a command line utility, and requires manual setup of its configuration file. I think it will do what he requires (which is much more advanced than the simple WPA access I use on my home WAP!). Then you can use Wifi-radar as a gui front-end to launch the WPA connection procedure. That's what I'm using. This is one area where Linux is not even close to the ease of WinXP. It has to be a labor of love, or else why put up with the difficulty of the process!

wpagui is the GUI for wpa_supplicant

---

### Post by computerwiz3491 on 2007-01-07
I was also having a lot of trouble getting wifi to work on my laptop. I searched the forums for hours, and I finally found a program called connection-manager. Just do a search for it. I was also worried about wifi at school. My school has 10 APs on the same network and in connection-manager, it displayed it as 10 separate networks, so I thought I was going to have trouble, but it seems to roam from one to another without any difficulties. The only problem I still have, which isn't really a problem anymore anyway is that my school uses a software-based webfilter called ImLua, which requires you to run a windows executable. It's OK anyway, because first of all it doesn't work well, and I could break through it fairly easily.

---

### Post by videodrome on 2007-01-16
For example, on my Inspiron 8000 laptop, network manager will not work no matter what. Three different wireless cards, hoary, breezy, edgy. It simply never connects. It just hangs there forever. Either on gnome or xfce or fluxbox or whatever.

However, those same cards on the same machine do work with that new connection manager program mentioned above.

---

### Post by ArgentSilver on 2007-01-20
> **macogw said:**
> wpagui is the GUI for wpa_supplicant

And does it run as a daemon when you boot so you automatically connect to your WAP with WPA authentication?

---

### Post by Duppy on 2007-01-20
wifi-radar is a bag of crap if you want to connect to a secured network. 

Infact, I have installed every wifi program in add/remove on edgy on my laptop today and not 1 of them worked to connect to my secured network.

---

### Post by ArgentSilver on 2007-01-26
> **Duppy said:**
> wifi-radar is a bag of crap if you want to connect to a secured network. 

Infact, I have installed every wifi program in add/remove on edgy on my laptop today and not 1 of them worked to connect to my secured network.

Well I would have to disagree with you there. Fact is, I personally am using wifi-radar to connect to my WPA secured WAP. But you must bear in mind that wifi-radar doesn't do WPA itself. You have to install and correctly configure wpa_supplicant (ie the file /etc/wpa_supplicant/wpa_supplicant.conf must be edited to contain your WAP SSID & password) before you can connect with wifi-radar. But once that's done, wifi-radar does a good job of establishing & maintaining a wifi-connection, whether with DHCP or static IP. If you are using WEP or, God forbid, no security at all on your WAP, wifi-radar doesn't need wpa_supplicant...definitely does not deserve the "bag of crap" label!

---

