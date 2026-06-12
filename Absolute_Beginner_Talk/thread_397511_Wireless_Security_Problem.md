---
title: "Wireless Security Problem"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by KiwiPete on 2007-03-30
I'm using Xubuntu and managed to install dual boot with Win 98.
It works well with wired internet connection, and now I'm trying to set up wireless access.
I'm using a Linksys Wireless-G 2.4GHz broadband router and an Atheros Chipset PCI card.
The system works fine if I have no security running on the router, but I'm having no luck when I switch security on in the router.
The Linksys router offers a number of security options - WPA, Radius and WEP.
I've been trying WPA as that allows me to set a password, that the receiving PC can use.
WEP has WEP Encryption options (64 or 128 bit), and then asks for a "Passphrase" which it uses to generate keys. Radius I don't understand.

In the PC running Xubuntu the Network settings for the Wireless Connection properties only has limited options to select.
"Address:" -  the options are DHCP or Static IP. I'm using DHCP.
"Password Type:" - options are "Plain (ASCII)" and "Hexadecimal"
"Connection Setting" - set as "Auto Config (DHCP)" vs "Static IP"

I've tried all the combinations I can around setting WPA or WEP on the router with Plain / Hexadecimeal password on the reciving PC and - also tried using Static IP instaed of DHCP - but no luck.

I feel I must be close to success, given that if I switch off the security on the router and eneter a null password on the receiving PC it works perfectly.

What am I missing here?
Is there some other way to configure the Wireless Connection in Xubuntu that will ofer me more sophisticated security options to match what the Linksys router is using?

Thanks for any wisdom you can provide.

KP

---

### Post by Yoooder on 2007-03-30
Perhaps your PC's wireless card is to blame.

Wireless security is based in large part on the wireless router & wireless card's hardware, and as such if you have an old card that only supports WEP, and a new router that does WPA2, you'll have to use the lowest common denominator.

I would say it may be best to get wireless working in Windows first--as you can most likely get some utilities from your card's manufacturer to help ease the install.  Begin with WEP, and if you get it working then try to step up to WPA (WEP is very poor security-wise).

In any event, here's a couple security-related recommendations:
 - Use the best encryption that you can (obviously you're trying :) )
 - Disable the SSID broadcast on your router -- this is enabled by default to greatly ease the setup of a wireless router, but is a huge security flaw
 - Cover all exterior walls with a fine copper mesh--cause hey, it's fun to be paranoid sometime

---

### Post by joethenoob on 2007-03-30
> **Yoooder said:**
> 
 - Disable the SSID broadcast on your router -- this is enabled by default to greatly ease the setup of a wireless router, but is a huge security flaw


Just my two cents, disabling the SSID broadcast keeps the honest noobs honest. Most wireless sniffers will find it anyway. In Windows this can create another problem. Because the SSID is not being broadcaset, a Windows PC (by default) will broadcast the SSID of the it's preferred wifi network in an attempt to find it.

If you can't get the WEP or WPA working, I suggest you just disable (or unplug) your access point when you are not using it. Can't get more secure than that.

---

### Post by KiwiPete on 2007-03-31
Thanks Noooba & Joethenoob

The wireless security (WPA) works fine on Windows (I've set the machine up with dual boot to Win 98 / Xubuntu). So we know the WLAN PCI card has the ability to talk to the router using WPA. The question is why Xubuntu can't do that. 

I'll try the WLAN PCI card's manufacturer's site, but my hunch is it has something to do with Xubuntu's Networking settings. It doesn't give any options that mentio WPA / WEP - just DHCD / Static IP plus Password with ASCII or Hexadecimal options.

Any other suggestions out there?

KP

---

### Post by KiwiPete on 2007-03-31
Bump

---

### Post by empedocles on 2007-04-01
Hi KiwiPete

I'm a command line guy, I'm afraid so I do things the hard way.  I just upgraded to a router that supports wpa, so I'm still working all this out.  There is probaby (possibly) an easier way to make this happen, but this is what I did.


First, apt-get install wpasupplicant, if it's not already installed.

second, create a /etc/wpa_supplicant/wpasupplicant.conf file, make it look kind of like this:

===========================
ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="MySSID"
        key_mgmt=WPA-PSK
        proto=WPA
        pairwise=TKIP
        group=TKIP
        psk="myrouterpassword"
        scan_ssid=1
}
======================

routerpassword (for me) was the ascii key I used on my handmedown linksys router, not the hex.  I just set the router for WPA with password, left the rest of the security at defaults.

my /etc/interfaces file looked like this when I used wep on my wireless:
========================
auto eth1
iface eth1 inet dhcp
wireless-essid MySSID
wireless-key MyhexKey
========================

I changed it for wpa to look like this:

===========================
auto eth1
iface eth1 inet manual
wpa-driver wext
wpa-roam /etc/wpa_supplicant/wpa_supplicant.conf

iface default inet dhcp
===========================

Okay,  eth1  is my wireless adapter. Yours may be wlan0 or something else.
The "iface default inet dhcp" is magic,  just put it in.  I don't understand it well enough to explain it yet. Has to do with the way the wpasupplicant software starts up.

the wpa-driver 'wext' is the driver I use.  apparently wpa is only supported for certain chipsets.  man wpa_supplicant and look at the "available drivers" section, pick the best match for your hardware. Maybe madwifi for Aetheros. If nothing quite fits, try wext, its the generic driver. 

the wpa-roam file points tothe wpa_supplicant file we just created.

if everything works, you should just be able to issue a
ifup eth1 (or whatever) and the wpa_supplicant software should do what it's supposed to.  Check /var/log/wpa_action.log

if it works you're in business.  

If not you may want to investigate which wireless driver you're using for your card.  I seem to recall that I read somwhere in my google marathon for setting mine up that there's a problem with the madwifi-ng drivers and wpasupplicant.  Or maybe it's madwifi drivers that have the problem and madwifi-ng works.  I'm using intel chipset, so I didn't pay a lot of attention to that bit, sorry

Hope it work for you.

---

### Post by KiwiPete on 2007-04-02
Thanks empedocles

I'll give your suggestions a try.
Unfortunately I am snowed under with work for the next few days, so it may take a little while before I let you know how I get one. Watch this space!

Thanks again.

KP

---

### Post by fishdude21 on 2007-10-10
Ive got my Aetheros 5007EG card working for all unsecure routers.  However, if i try and connect to my router which is set to MAC address i cant get in.  Could someone help me with this?

---

