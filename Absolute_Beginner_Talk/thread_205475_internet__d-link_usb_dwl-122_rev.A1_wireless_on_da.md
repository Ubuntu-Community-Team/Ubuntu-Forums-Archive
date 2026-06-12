---
title: "internet / d-link usb dwl-122 rev.A1 wireless on dapper not working"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by iblastoff on 2006-06-28
alright so i've scoured this forum endlessly and i know there are tons of posts about this already. but i still cant seem to find one where it actually works for me. either the post is talking about another ubuntu build or the revision of the USB adapter is different or etc etc

i am running ubuntu dapper.
my router is a typical linksys wrt54g using WEP encryption.
my usb adapter is the d-link dwl - g122 revision A1. not A2 or B or C's.

if i lsusb, it shows up as:
id 2001:3703 D-Link Corp. [hex] DWL-122 802.11b

(edit: i just realized it may not be detecting it properly as its saying its a dwl-122 802.11b. my usb adapter is dwl-g122 and should be 802.11g?) 

the actual usb adapter seems to be detected fine. the light glows green and 
under system/administration/networking it is displayed as:
Wireless Connection
The interface eth3 is active.

shouldn't it be a wlan instead of eth? 

i also already have another wireless card that im using only because my usb one is not working and i would eventually like to remove the older wireless card completely. i cant do this yet because ubuntu isnt working with the usb adapter i want to use. im assuming the usb adapter should show up as wlan1 or something to that effect since i already have a wlan0.

so anyway the other pci wireless card i have is listed as:
Wireless Connection
The interface wlan0 is active. 
this card works fine (but i want to remove it completely as soon as the usb one starts to work)

i've tried disabling the working pci wireless card and that didnt really affect the usb wireless adapter in any way. 

the other threads seem to imply that ndiswrapper would be fine while newer posts say that i dont need to use it anymore? 

anyway so how do i get this working? i am not sure where to even start! the usb adapter seems to be detected just fine. it just wont work! its not broken cause i use it as my main wireless interface on xp and it works fine.

---

### Post by az on 2006-06-28
It is a prism2_usb device and you need to use a package that doesn not currently speak the same languages as th rest of the networking infrastruture:
[https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111](https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111)

---

### Post by iblastoff on 2006-06-28
[QUOTE=azz]It is a prism2_usb device and you need to use a package that doesn not currently speak the same languages as th rest of the networking infrastruture:
[https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111](https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111)[/QUOTE]


i am not even sure what im supposed to do with that? i am trying to follow it but i am not sure how it even applies to me. for example i am at the step that says:

-----------
Next, we must alias the wlan0 to the prism2_usb device. In Ubuntu 5.10 (Breezy), do this by adding the following to /etc/modprobe.conf. In Ubuntu 6.06 (Dapper) do this by adding the following to /etc/modprobe.d/wlan (only if needed):
-----------

firstly, my usb adapter isnt even recognized as a 'wlan' device yet. it keeps telling me its an 'eth3'. and i dont even have a wlan file in my /etc/modprobe.d directory. does that mean its 'needed'? i have no idea

---

### Post by az on 2006-06-29
[QUOTE=iblastoff]
firstly, my usb adapter isnt even recognized as a 'wlan' device yet. it keeps telling me its an 'eth3'. and i dont even have a wlan file in my /etc/modprobe.d directory. does that mean its 'needed'? i have no idea[/QUOTE]
Well, I did not have to do that in my case.  But it would seem that making that alias will do exactly what you need, make it a wlan0 device.

---

