---
title: "Lubuntu - setting up uShare headache"
date: 2011-09-07
forum: Any Other OS
---

### Post by wiiija on 2011-09-07
Hi all,

I'm currently attempting to get uShare to share a directory over my network and it is proving to be a real pain!

Firstly I connect to my vm superhub from the laptop wireless (that contains the directory to share), I have 2 other devices that I wish to share the files from said directory, Xbox360 which is hard wired into the superhub and a WDTV Live which is connected wireless.

The xbox360 is not THAT important so if we could concentrate on the WDTV that would be great.
The WDTV is using a D-Link DIR615 as a client bridge to connect to the Superhub, the connection etc is absolutely fine and it works a treat. The issue I have is that it just does not pick up my uShare (network shares) at all.

The 360 does see uShare but cannot access it, as you can see this is a pain that I cannot seem to fix, networking/sharing on linux is completely alien to me, I simply cannot see where the issue lies. The uShare config looks fine, I do not know where to go from here.

Any help is hugely appreciated.

Sean

---

### Post by kerry_s on 2011-09-07
Does samba do the same thing?
If so, go to /usr/share/applications & double click on shared folders, click the lock to unlock & set it up.

---

### Post by wiiija on 2011-09-07
I seem to get no where at all with samba, uShare at least makes it visible to one device (360), I get nothing at all with samba :(

---

### Post by kerry_s on 2011-09-07
post the ushare.conf so we can look it over.
you say the dir you trying to share is not on the same device, how do you have it mounted?

i'm installing ushare right now to try, be back in a bit.

---

### Post by wiiija on 2011-09-07
```
# /etc/ushare.conf
# Edit this file with 'dpkg-reconfigure ushare'
# Configuration file for uShare

# uShare UPnP Friendly Name (default is 'uShare').
USHARE_NAME=Movies

# Interface to listen to (default is eth0).
# Ex : USHARE_IFACE=eth1
USHARE_IFACE=wlan0

# Port to listen to (default is random from IANA Dynamic Ports range)
# Ex : USHARE_PORT=49200
USHARE_PORT=

# Port to listen for Telnet connections
# Ex : USHARE_TELNET_PORT=1337
USHARE_TELNET_PORT=

# Directories to be shared (space or CSV list).
# Ex: USHARE_DIR=/dir1,/dir2
USHARE_DIR=/home/sean/Downloads/complete

# Use to override what happens when iconv fails to parse a file name.
# The default uShare behaviour is to not add the entry in the media list
# This option overrides that behaviour and adds the non-iconv'ed string into
# the media list, with the assumption that the renderer will be able to
# handle it. Devices like Noxon 2 have no problem with strings being passed
# as is. (Umlauts for all!)
#
# Options are TRUE/YES/1 for override and anything else for default behaviour
USHARE_OVERRIDE_ICONV_ERR=

# Enable Web interface (yes/no)
USHARE_ENABLE_WEB=yes

# Enable Telnet control interface (yes/no)
USHARE_ENABLE_TELNET=

# Use XboX 360 compatibility mode (yes/no)
USHARE_ENABLE_XBOX=yes

# Use DLNA profile (yes/no)
# This is needed for PlayStation3 to work (among other devices)
USHARE_ENABLE_DLNA=yes


```

That is the config as it stands, the directory is on the same device that is running uShare.
The 360 says it cannot connect (there may be a firewall or something, which there is not), the WDTV Live just doesn't see anything at all!

---

### Post by kerry_s on 2011-09-07
it works fine for me on my xbox360.
this:
USHARE_ENABLE_DLNA=yes
needs to be:
USHARE_ENABLE_DLNA=no

did you do the:
sudo service ushare restart

after you made changes?

---

### Post by wiiija on 2011-09-07
The DLNA=no has fixed it on xbox, thank you :)

Still no joy with the most important WDTV Live though, it see's nothing at all, very odd.

---

### Post by kerry_s on 2011-09-07
> **wiiija said:**
> The DLNA=no has fixed it on xbox, thank you :)

Still no joy with the most important WDTV Live though, it see's nothing at all, very odd.

does that require a special port?

---

### Post by wiiija on 2011-09-07
I don't believe so, google seems to show it running fine for some people but mine just doesn't see anything. I'm going to guess its something to do with the router (running DD-WRT) that I'm using as a client bridge, so its going to be a port issue, the fact its connected to the superhub router fine though and has network/interent access is very puzzling to say the least!

---

### Post by kerry_s on 2011-09-07
> **wiiija said:**
> I don't believe so, google seems to show it running fine for some people but mine just doesn't see anything. I'm going to guess its something to do with the router (running DD-WRT) that I'm using as a client bridge, so its going to be a port issue, the fact its connected to the superhub router fine though and has network/interent access is very puzzling to say the least!

i'd also set the port so i can access the web gui:
USHARE_PORT=49200

you might want to do that to.
[http://localhost:49200/web/ushare.html](http://localhost:49200/web/ushare.html)

i'm running DD-WRT as a bridge as well.
under nat/qos did you enable upnp?

---

### Post by wiiija on 2011-09-07
Yeh I have upnp enabled, I also have all the firewall stuff turned off on the bridge. This is frustrating.

---

### Post by kerry_s on 2011-09-07
> **wiiija said:**
> Yeh I have upnp enabled, I also have all the firewall stuff turned off on the bridge. This is frustrating.

well it's not the ushare setup, so the problem is after it leaves your box, you know it's working on xbox, so whats the difference from the xbox & wdtv on your network?

---

### Post by wiiija on 2011-09-07
The xbox is wired straight into the superhub, the WDTV live is connected to it wireless using the bridge.

---

### Post by kerry_s on 2011-09-07
> **wiiija said:**
> The xbox is wired straight into the superhub, the WDTV live is connected to it wireless using the bridge.

so wireless to the superhub? tell me more about this superhub.

---

### Post by wiiija on 2011-09-07
Yes wireless to the hub, it's basically a cable modem and router, from virginmedia here in the UK, made by Netgear I believe. What is confusing me is the fact the WDTV is connected to it perfectly fine, with net access.

---

### Post by kerry_s on 2011-09-07
> **wiiija said:**
> Yes wireless to the hub, it's basically a cable modem and router, from virginmedia here in the UK, made by Netgear I believe. What is confusing me is the fact the WDTV is connected to it perfectly fine, with net access.

just found something, you said you have ddwrt setup as a client bridge, here [http://wdtvhd.com/index.php?showtopic=7371](http://wdtvhd.com/index.php?showtopic=7371)
says a repeater bridge works, so i think you should try repeater bridge, mine is repeater to fyi:
[http://www.dd-wrt.com/wiki/index.php/Repeater_Bridge](http://www.dd-wrt.com/wiki/index.php/Repeater_Bridge)

it's basically just like client.

---

### Post by wiiija on 2011-09-07
Thank you, I will take another look at repeater, I did actually spend a couple of days setting it up as repeater, although its very similar to setting up a client bridge I actually never got it to work! Setup as client bridge and voila it connected straight away.

---

### Post by kerry_s on 2011-09-07
> **wiiija said:**
> Thank you, I will take another look at repeater, I did actually spend a couple of days setting it up as repeater, although its very similar to setting up a client bridge I actually never got it to work! Setup as client bridge and voila it connected straight away.

good luck! it's 3 in the mourning here so i got to catch some z's, i'll check in on you when i wake up.

---

### Post by wiiija on 2011-09-07
Ok buddy, thanks a lot for the help.

Searching around for all intents and purposes client bridge is fine for me as the WDTV is just wired into the second router anyway so repeater is not needed. I will continue to search for a solution to this odd problem :)

---

### Post by wiiija on 2011-09-07
Update, tried pluggin the WDTV Live straight into the superhub as the 360 was and it has no issue seeing or playing the files from uShare.

Also I tried unplugging the xbox from the superhub and using the second router/bridge, the xbox could see the uShare no problem but would not access it, so the issue is for sure the bridging router.

---

