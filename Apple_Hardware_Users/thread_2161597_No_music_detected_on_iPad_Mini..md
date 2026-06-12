---
title: "No music detected on iPad Mini."
date: 2013-07-11
forum: Apple Hardware Users
---

### Post by TheFallout1994 on 2013-07-11
Greetings,

I'm using ubuntu 12.04 LTS and I have an iPad Mini. The system does detect my device, and it shows up in rhythmbox.
Everything seems to work well as I can sync my iPad with the music library in rhythmbox. And it does ! The music I want is on my iPad. It takes the memory it needs. But unfortunately, none of my musics are detected from the iPad.
So I've tried to look it up, and it seems that I'm not the only one to be confronted with this issue.
I've followed the instructions on this [http://ubuntuforums.org/showthread.php?t=1823227](http://ubuntuforums.org/showthread.php?t=1823227) and I've tried a sudo lsusb -v | grep -i Serial in terminal, and have found no 16 digits serial code
:
iSerial                 0 
  iSerial                 1 0000:00:1d.0
  iSerial                 1 0000:03:00.0
  iSerial                 1 0000:03:00.0
  iSerial                 3 ff8850d1370e5aaa5af797d634af1b8424dde984
  iSerial                 0 
  iSerial                 3 SN0001



So I can't edit [COLOR=#000000][FONT=Ubuntu Mono]/mnt/ipod/iPod_Control/Device/SysInfo
[/FONT][/COLOR]Although, when I go to device/iTunes_Control/device/ there is a SysInfoExtended file. So I guess it was the one I'm supposed to edit. But the serial seems to be fine : 

<key>SerialNumber</key>
    <string>DLXK2CSNF197</string>
    <key>VisibleBuildID</key>
    <string>6.0.2</string>
    <key>FireWireGUID</key>
    <string>ff8850d1370e5aaa5af797d634af1b8424dde984</string>
    <key>UniqueDeviceID</key>
    <string>ff8850d1370e5aaa5af797d634af1b8424dde984</string>


So yeah ... I'm kind of stuck as a new Linux user.
Someone please help me ? :)

---

### Post by ajgreeny on 2013-07-11
The music on the ipod may be crippled with DRM if it has come from iTunes and, so you will not be able to play it, if that is the case, even if you can see it.

---

