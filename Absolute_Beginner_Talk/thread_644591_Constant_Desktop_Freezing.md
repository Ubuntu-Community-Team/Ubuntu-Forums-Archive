---
title: "Constant Desktop Freezing"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by The Tronyx on 2007-12-19
Ok, I have read as many threads on desktops freezing as I can before feeling like my head is going to burst.  Long story short I have a Toshiba A215 with an ATI X1200, restricted drivers are enabled, 

Here is as full of a description as I can give:

I am using openbox.  
When the desktop freezes I have firefox, gnome-terminal and xchat open (usually).  
If i ctrl+alt+backspace out of the freeze, it usually does it shortly after I get back in.  
It only freezes when I am typing as in entering something into the terminal or into xchat
If it freezes and I close my laptop, open it back up, tap the mouse it is not frozen, but usually freezes shortly after.
The only way I have found to keep it from freezing again is to reboot my machine.

Here is a snippet of my syslog.

```
Dec 19 01:16:04 wrekx dhclient: DHCPACK from 192.168.11.1
Dec 19 01:16:04 wrekx avahi-daemon[5268]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.11.7.
Dec 19 01:16:04 wrekx avahi-daemon[5268]: New relevant interface wlan0.IPv4 for mDNS.
Dec 19 01:16:04 wrekx avahi-daemon[5268]: Registering new address record for 192.168.11.7 on wlan0.IPv4.
Dec 19 01:16:04 wrekx dhclient: bound to 192.168.11.7 -- renewal in 73956 seconds.
Dec 19 01:16:04 wrekx modprobe: WARNING: Not loading blacklisted module ipv6 
Dec 19 01:16:05 wrekx kernel: [   44.148000] [fglrx] total      GART = 130023424
Dec 19 01:16:05 wrekx kernel: [   44.148000] [fglrx] free       GART = 114032640
Dec 19 01:16:05 wrekx kernel: [   44.148000] [fglrx] max single GART = 114032640
Dec 19 01:16:05 wrekx kernel: [   44.148000] [fglrx] total      LFB  = 134217728
Dec 19 01:16:05 wrekx kernel: [   44.148000] [fglrx] free       LFB  = 119828480
Dec 19 01:16:05 wrekx kernel: [   44.148000] [fglrx] max single LFB  = 119828480
Dec 19 01:16:05 wrekx kernel: [   44.148000] [fglrx] total      Inv  = 0
Dec 19 01:16:05 wrekx kernel: [   44.148000] [fglrx] free       Inv  = 0
Dec 19 01:16:05 wrekx kernel: [   44.148000] [fglrx] max single Inv  = 0
Dec 19 01:16:05 wrekx kernel: [   44.148000] [fglrx] total      TIM  = 0
Dec 19 01:16:06 wrekx ntpdate[5529]: adjust time server 91.189.94.4 offset 0.324383 sec
Dec 19 01:16:10 wrekx gdmgreeter[5545]: GdkPixbuf-CRITICAL: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed 
Dec 19 01:16:10 wrekx gdmgreeter[5545]: GdkPixbuf-CRITICAL: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed 
Dec 19 01:16:10 wrekx gdmgreeter[5545]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed 
Dec 19 01:16:10 wrekx gdmgreeter[5545]: GLib-GObject-WARNING: invalid (NULL) pointer instance 
Dec 19 01:16:10 wrekx gdmgreeter[5545]: GLib-GObject-CRITICAL: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
Dec 19 01:16:10 wrekx gdmgreeter[5545]: GdkPixbuf-CRITICAL: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed 
Dec 19 01:16:10 wrekx gdmgreeter[5545]: GdkPixbuf-CRITICAL: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed 
Dec 19 01:16:10 wrekx gdmgreeter[5545]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed 
Dec 19 01:16:10 wrekx gdmgreeter[5545]: GdkPixbuf-CRITICAL: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed 
Dec 19 01:16:10 wrekx gdmgreeter[5545]: GdkPixbuf-CRITICAL: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed 
Dec 19 01:16:10 wrekx gdmgreeter[5545]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed 
Dec 19 01:16:10 wrekx gdmgreeter[5545]: GdkPixbuf-CRITICAL: gdk_pixbuf_new_from_file_at_scale: assertion `width > 0 || width == -1' failed 
Dec 19 01:16:10 wrekx gdmgreeter[5545]: GLib-GObject-WARNING: invalid (NULL) pointer instance 
Dec 19 01:16:10 wrekx gdmgreeter[5545]: GLib-GObject-CRITICAL: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
Dec 19 01:16:10 wrekx gdmgreeter[5545]: GdkPixbuf-CRITICAL: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed 
Dec 19 01:16:10 wrekx gdmgreeter[5545]: GdkPixbuf-CRITICAL: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed 
Dec 19 01:16:10 wrekx gdmgreeter[5545]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed 
Dec 19 01:16:10 wrekx gdmgreeter[5545]: GdkPixbuf-CRITICAL: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed 
Dec 19 01:16:10 wrekx gdmgreeter[5545]: GdkPixbuf-CRITICAL: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed 
Dec 19 01:16:10 wrekx gdmgreeter[5545]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed 
Dec 19 01:16:10 wrekx gdmgreeter[5545]: GdkPixbuf-CRITICAL: gdk_pixbuf_new_from_file_at_scale: assertion `width > 0 || width == -1' failed 
Dec 19 01:16:10 wrekx gdmgreeter[5545]: GLib-GObject-WARNING: invalid (NULL) pointer instance 
Dec 19 01:16:10 wrekx gdmgreeter[5545]: GLib-GObject-CRITICAL: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
Dec 19 01:16:20 wrekx modprobe: WARNING: Not loading blacklisted module ipv6 
Dec 19 01:16:26 wrekx last message repeated 14 times
Dec 19 01:17:01 wrekx /USR/SBIN/CRON[5804]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 19 01:17:22 wrekx modprobe: WARNING: Not loading blacklisted module ipv6 
Dec 19 01:19:18 wrekx modprobe: WARNING: Not loading blacklisted module ipv6 
Dec 19 01:20:04 wrekx modprobe: WARNING: Not loading blacklisted module ipv6 
Dec 19 01:24:30 wrekx modprobe: WARNING: Not loading blacklisted module ipv6 
Dec 19 01:24:32 wrekx last message repeated 2 times
Dec 19 01:29:03 wrekx modprobe: WARNING: Not loading blacklisted module ipv6 
Dec 19 01:29:41 wrekx last message repeated 6 times
Dec 19 01:31:11 wrekx modprobe: WARNING: Not loading blacklisted module ipv6 
Dec 19 01:32:31 wrekx modprobe: WARNING: Not loading blacklisted module ipv6 
Dec 19 01:33:05 wrekx last message repeated 2 times
Dec 19 01:34:35 wrekx last message repeated 38 times
Dec 19 01:35:52 wrekx last message repeated 2 times
Dec 19 01:41:36 wrekx modprobe: WARNING: Not loading blacklisted module ipv6 
Dec 19 01:42:24 wrekx kernel: [ 1622.476000] APIC error on CPU1: 00(40)
Dec 19 01:42:24 wrekx kernel: [ 1622.476000] APIC error on CPU0: 00(40)
Dec 19 01:45:42 wrekx modprobe: WARNING: Not loading blacklisted module ipv6 
```

Thanks ahead of time as any help is **greatly** appreciated.

---

### Post by The Tronyx on 2007-12-19
Bump. :)

---

### Post by steve_s on 2007-12-19
I'm getting the same exact error, I just installed Gutsy.  I never used Edgy, but I ran Breezy and everything earlier and never ran into this problem.

---

### Post by fs3rp4 on 2007-12-20
Try to use this commands in boot kernel line inside grub:

noapic nolapic

---

### Post by jan quark on 2007-12-20
having similar freezing issues on my dell laptop. could it be linked with the touch pad, because i have the feeling that when I accidentely touch the touchpad :) on two spots simultaneously the sreen just freezes.

---

### Post by The Tronyx on 2007-12-21
> **fs3rp4 said:**
> Try to use this commands in boot kernel line inside grub:

noapic nolapic

Would i need to edit grub.conf to do that permenantly?

---

### Post by rkd on 2007-12-21
> **2point0 said:**
> Would i need to edit grub.conf to do that permenantly?

I'm pretty sure that is correct.

---

### Post by The Tronyx on 2007-12-21
> **rkd said:**
> I'm pretty sure that is correct.

Just a follow-up and a small bump, the tips listed above have so far kept lockups from happening.  If anyone comes searching for Toshiba Satellite A215 lock up or freeze or freezing or those CPU errors involving APIC CPU errors this did the trick for me. =D

---

### Post by fs3rp4 on 2007-12-21
> **2point0 said:**
> Just a follow-up and a small bump, the tips listed above have so far kept lockups from happening.  If anyone comes searching for Toshiba Satellite A215 lock up or freeze or freezing or those CPU errors involving APIC CPU errors this did the trick for me. =D

Probaly yes. Try to update your BIOS to last version.  This solve my HP problems...

---

