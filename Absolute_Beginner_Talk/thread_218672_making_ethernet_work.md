---
title: "making ethernet work"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by macogw on 2006-07-18
I gave up on trying to dual boot.  There's no Windows on my laptop now...meaning I need to get this working FAST.

I'm in Network Tools - Devices.  There are 3 options: lo, eth0, and eth1.  I'm pretty sure the "configure" button is what I need, but that's all greyed out.  Is there a command line I can use to get around this?  What should I do?

---

### Post by skale on 2006-07-18
Go to System > Networking instead. Enable whichever you like. Post what happens.

---

### Post by macogw on 2006-07-18
eht1 and eth0 are both active it says.  the modem's not configured (but i dont give a damn).  in the "properties" thing for eth0 (the one i want to use...there's no wireless in my house) there's no ip address or gateway address or anything in there.  it is dhcp, it says.  i clicked for eth0 to be the default gateway device.  should i type an ip address into the properties thing?  if yes, where do i find out what the ip address should be?  i'm guessing that seeing as I'm yanking the network cable out of the desktop and putting it into the laptop back and forth to do this, it is probably the same as the desktop one (since it's the same modem).  so...how do i find out what that is cuz i haven't needed to look up an ip address (in windows) since i set up wireless in my dad's house about a year ago.

---

### Post by skale on 2006-07-18
Click on eth0, and go to properties, and check "enable this connection" and set it to DHCP. There are a million things that could be wrong, try to find a howto on this website.

---

### Post by macogw on 2006-07-18
it is enabled and it is dhcp.  it just doesnt work.

since i have the terminal open this time, when i clicked "default gateway device: eth0" it gave me a message in the terminal.  it says:
```

** (network-admin:10427): CRITICAL **: gst_xml_element_set_content: assertion 'node != NULL' failed

```

and by the way, [http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430) didn't work for me

---

