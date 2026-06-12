---
title: "KTorrent crashes (data included)"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by FleetAdmiral74 on 2007-07-15
It shows the window for a half second, and then reverts to the crash window. 

```
ed@database:~$ ktorrent
Qt: Warning: X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Qt: Warning: Failed to open device
Qt: Warning: X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Qt: Warning: Failed to open device
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
Qt: Warning: QObject::disconnect: Unexpected null parameter
Qt: Warning: QObject::disconnect: Unexpected null parameter
ed@database:~$ Qt: Warning: QGArray::at: Absolute index 0 out of range
KCrash: Application 'ktorrent' crashing...

```

What can I do?

---

### Post by forestpixie on 2007-07-15
I had that - I solved it by getting rid of stuff in xorg.conf it's taken me a while to remember where I found it but this was the one I used.

Post 3  and 7

[http://ubuntuforums.org/showthread.php?t=293023](http://ubuntuforums.org/showthread.php?t=293023)

Hope it helps :)

---

### Post by FleetAdmiral74 on 2007-07-15
From that thread, 

"I tried to do what you suggested and commented out all devices with wacom-drivers (3 to be exact). After this I couldn't start X, it complained the xorg.conf was incorrect/incomplete and I had to remove the comments to be able to restart X. I did comment out the start and finish-lines."

hehe, I don't want to kill my GUI :popcorn:

---

### Post by forestpixie on 2007-07-16
If you've got it backed up it'll be easy enough to sort :)

Like I said I got rid of the wacom stuff and since then have not had the problem

---

### Post by daschmidty on 2007-07-17
About the xorg lines..there is also a part at the bottom of xorg.conf that lists the server layout.

```
Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"

```

and these lines controls what modules x loads on boot. you need to comment out the stylus eraser and cursor lines here to make everything work/

---

