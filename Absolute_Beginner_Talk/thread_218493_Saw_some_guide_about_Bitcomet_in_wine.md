---
title: "Saw some guide about Bitcomet in wine"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by kris2pe on 2006-07-18
I saw some guide about Bitcomet in wine in a chinese site! I don't understand any of it but the regedit was in english. 
So I'm hopping someone out there could probably make sense of all of this!!! 
[http://my.opera.com/Gwwfps/blog/show.dml/332273](http://my.opera.com/Gwwfps/blog/show.dml/332273)
Remember the regedits are in english!!!

---

### Post by kinematic on 2006-07-18
no one can make sense of the windows registry....not even the folks at ms ;)

---

### Post by kris2pe on 2006-07-18
Can some out there translate this? I think this is a good guide!!!

---

### Post by mrvw0169 on 2006-07-19
I don't use BitComet anymore since so many trackers banned it after cheating the system (I use [www.utorrent.com](www.utorrent.com) now in WINE as it is much better)... All that it takes is download utorrent.exe from the site and wine utorrent.exe (no install required!)...

But anyway, the basic thing is to just wine bitcomet-installfile.exe then create a launcher (or right click the Applications menu and Edit menu...) with the command "wine /home/USERNAME/.wine/drive_c/Program Files/BitComet/bitcomet.exe" and that should run... My friend just confirmed that this is all it takes for BitComet but of course I don't know the actual file names to confirm them first!

---

### Post by kris2pe on 2006-07-19
I tried using them in wine but they need the msxml3! Which I really don't know how to make them work w/ wine!!!

---

### Post by mrvw0169 on 2006-07-19
Oh dang, yeah I just called my friend again and he said he had the same problem (I just assumed it ran because he was able to wine bitcomet.exe so now he's using uTorrent - really try it as it is much simpler, small (a hundred KB!), and guaranteed to work - I download at over 500 KB/s vs. sometimes 70 KB/s with Azureus)...

Here's my attempt to interpret the page (I'm not Chinese, but I've had some experience (limited) of the manual config of wine previously):

0. Well, this is obvious and not on the guide, but just in case - add to your /etc/apt/sources.list:
```
deb http://wine.budgetdedicated.com/apt dapper main
``` and run ```
sudo aptitude update && sudo aptitude install wine
```

1. Install EasyWine from [http://www.linuxgame.org/bbs/?thread-1896-1-1.html](http://www.linuxgame.org/bbs/?thread-1896-1-1.html) click the EasyWine3b2.sh link (examine the file as I did not d/l it, I don't know if it is safe) - This step is likely not necessary as running winecfg should get everything already setup (maybe you might have to install other things, i.e. with winetools, but see below)

2. Install DCOM following this guide: [http://wiki.winehq.org/NativeDcom](http://wiki.winehq.org/NativeDcom)

3. Install the MS Installer system from by running wine on (actually, I think you should copy paste the registry file part below before you wine this): [http://download.microsoft.com/download/WindowsInstaller/Install/2.0/W9XMe/EN-US/InstMsiA.exe](http://download.microsoft.com/download/WindowsInstaller/Install/2.0/W9XMe/EN-US/InstMsiA.exe)

Now open gedit and copy paste the following in it and save it somewhere as nativemsi.reg:
```
REGEDIT4

[HKEY_CURRENT_USER\Software\Wine]
"Version"="win98"

[HKEY_CURRENT_USER\Software\Wine\DllOverrides]
"msi"="native"
"msiexec.exe"="native"
```

Now run it by:
```
wine regedit nativemsi.reg
rm ~/.wine/drive_c/windows/system*/msiexec.exe
wine InstMsiA.exe
```

4. Follow the guide at: [http://wiki.winehq.org/NativeMSXML3](http://wiki.winehq.org/NativeMSXML3) and install the updated version at (This is a link to the English version instead of the Chinese version on that site): 
[http://www.microsoft.com/downloads/details.aspx?familyid=4a3ad088-a893-4f0b-a932-5e024e74519f&displaylang=en](http://www.microsoft.com/downloads/details.aspx?familyid=4a3ad088-a893-4f0b-a932-5e024e74519f&displaylang=en)

Then:
```
wine c:\\windows\\installer\\instmsi0\\msiexec.exe /i msxml3.msi
```

5. Download BitComet and run the installation with wine - the guide says 0.56 but try the latest version first, if it doesn't work then use 0.56...

Hope that helps! Another BT client comparable to BitComet is BitSpirit, but I would go with uTorrent still... At least it's less work!

---

### Post by kris2pe on 2006-07-19
I tried it but utorrent is slow as hell!!! If I  wanted to do that I rather stick w/ bittornado!!!

---

### Post by mrvw0169 on 2006-07-19
Lol... *shrug* I guess YMMV... It usually takes some time to get decent speeds and you have to tweak the settings to allow more connections per torrent, upload speeds, and any port forwarding needed by your router - this applies to all clients...

Any luck with BitComet installing?

---

### Post by kris2pe on 2006-07-19
Utorrent is slow & I don't even use routers!!! Is there other tweaks for either a linux compatible or utorrent? Would be nice if you can !!! 
Coz in bitcomet in windows I can reach as high as 100kbps!!!

---

### Post by mrvw0169 on 2006-07-19
In uTorrent, there is the Options>Speed Guide menu option... Of course this all depends on your connection (I have 6Mbps cable)...

These are my (sort of relevant) settings for uTorrent but applies to any BT client (Options>Preferences):

**Connections**
Port: whichever you want as long as you make sure it's not blocked by router/firewall/ISP
Disabled UPnP (never worked for me and I disable it on router anyway)
Global max upload: 25 KB/s (make it ~80% of max upload or your bandwidth will suffer)
Unlimited max download rate

**BitTorrent**
Enable DHT network and peer exchange
Global max connections: 512
Max connected peers/torrent: 100
Max upload slots per torrent: 5 (with use additional speed if upload speed < 90% checked)

**Queueing**
Max active torrents: 99
Max active downloads: 99

---

