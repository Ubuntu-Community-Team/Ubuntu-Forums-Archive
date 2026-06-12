---
title: "Bluetooth OBEX Client"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by paogeorge13 on 2006-10-16
I installed Bluetooth OBEX Client to send images and sounds from my mobile to pc and from my pc to my mobile. I have Sony Ericsson K700i. I bought a bluetooth for pc which is Fujitsu Siemens. Now I can send files from my pc to my mobile but I can't send files from my mobile to my pc. My mobile says: connection failed. What's wrong?

---

### Post by graz848 on 2006-10-28
I have a Sony Ericsson k750i and the opposite problem: i can easily send files from the mobile to the pc but i can't send ANYTHING from the PC to the mobile. When trying to send files via bluetooth using nautilus-sendto or gnome-obex-send, he keeps on looking around for dispositives but doesn't find nothing. Yet a command like > hcitool scan  gives this output: > hcitool scan
Scanning ...
        00:16:20:34:26:49       Graz K750i
. So he FINDS it, in some cases... what's wrong? why cant i get gnome-bluetooth-manager? Any help?
I have Edgy just installed, gnome-bluetooth and bluez libs.

---

### Post by samoht on 2006-12-22
Take the device-number from "hcitool scan" and do "gnome-obex-send -d $device /path/to/file" . Scanning is broken in gnome-bluetooth version shipped with edgy...

---

