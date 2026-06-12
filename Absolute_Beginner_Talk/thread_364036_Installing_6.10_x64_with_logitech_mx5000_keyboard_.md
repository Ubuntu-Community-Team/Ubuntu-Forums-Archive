---
title: "Installing 6.10 x64 with logitech mx5000 keyboard and mx laser mouse"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by mikemargle on 2007-02-17
Hi everyone, I'm new to this whole linux thing and I've been told ubuntu's the way to go.  Plenty of support and features.  Currently I'm having trouble installing 6.10 x64 with my wireless mouse and keyboard (logitech mx5000 keyboard, mx laser mouse).  They both work fine in the BIOS and when ubuntu starts up prior to install.  However, both stop working when I come to the ubuntu desktop.  I believe it has something to do with X starting up.  Any help would be greatly appreciated.

Best regards,

Margle

---

### Post by mikemargle on 2007-02-18
Ok, so i solved the install problem by borrowing a USB mouse and keyboard.  Everything is installed and running, except  when i restarted and tried to boot up with the wireless keyboard and mouse, they do not work.  Any help would be greatly appreciated.

---

### Post by westis78 on 2007-02-21
I am having the same problems with my mx5000-set on x86_64-edgy. Everything works just fine until the login screen is loaded. The mouse pointer still moves a fraction of a second before it is time to use the keyboard. Then connection is lost and pressing the connect-buttons does not help at all. 	](*,)

The quick fix for this is to just replug the BT-reciever into the usb-port. Then the connection is remade and and everything works just fine. Now it is getting pretty annoying to replug the reciever every time I start my computer so I'll do some more troubleshooting to find out why it just dies. 

My usb smartcard reader also have to be replugged to work but my usb-mic works without replugging. Could it be that some daemon starting kills the connection? :-k

update:
Apparently the bluetooth daemon conflicts with the logitech mx5000. I just disabled the bluetooth daemon (System-Administration-Services, untick bluetooth device management)  and now it works as expected. 
Here is another thread on the topic: [http://ubuntuforums.org/showthread.php?t=341351](http://ubuntuforums.org/showthread.php?t=341351)

---

