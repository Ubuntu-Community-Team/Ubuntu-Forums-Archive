---
title: "RT61 Wireless Problem, Cant create folder"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by super.rad on 2007-03-23
Im trying to install my wireless card in ubuntu dapper drake, im following this guide [http://www.ubuntuforums.org/showthread.php?t=132980]("http://www.ubuntuforums.org/showthread.php?t=132980")  (scroll down for the dapper guide) everythings going fine until i get to
```
sudo mkdir /etc/Wireless/RT61STA
```
when i type this into the console i get this message
```
mkdir: cannot create directory `/etc/Wireless/RT61STA': No such file or directory

```
anyone know why im getting this and how i can solve it, i also tried just going into the etc folder in filebrowser and right clicking but make folder is greyed out. A little help anyone? Thanks

---

### Post by super.rad on 2007-03-23
ok i managed to create the folder, but the next step is giving me errors aswell, the step is
```
cp *.bin /etc/Wireless/RT61STA/
```
when i type that i get this error
```
cp: cannot create regular file `/etc/Wireless/RT61STA/rt2561.bin': Permission denied
cp: cannot create regular file `/etc/Wireless/RT61STA/rt2561s.bin': Permission denied
cp: cannot create regular file `/etc/Wireless/RT61STA/rt2661.bin': Permission denied

```

any help would be much appreciated

---

### Post by super.rad on 2007-03-23
can anyone help? i need to get this sorted tonight, thanks

---

### Post by super.rad on 2007-03-23
ok sorry to keep posting but once again i've got 1 step further, now i need to edit the file rt61sta.dat, i've opened it in gedit but im not too sure what i need to change, if anyone could help me out i would really appreciate it, The name of my wireless network is NETGEAR and theirs no security, so if someone could tell me what i need to change and what to it would be great
```
[Default]
CountryRegion=0
CountryRegionABand=7
WirelessMode=4
SSID=NAME_OF_ACCESS_POINT
NetworkType=Infra
Channel=0
AuthMode=OPEN
EncrypType=WEP
DefaultKeyID=1
Key1Type=0
Key1Str=10_CHAR_WEP_KEY
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
WPAPSK=abcdefghijklmnopqrstuvwxyz
TxBurst=12
PktAggregate=0
TurboRate=0
WmmCapable=0
AckPolicy1=0
AckPolicy2=0
AckPolicy3=0
AckPolicy4=0
BGProtection=0
ShortSlot=0
IEEE80211H=0
TxRate=0
RTSThreshold=2347
FragThreshold=2346
PSMode=CAM
TxPreamble=0
```

---

