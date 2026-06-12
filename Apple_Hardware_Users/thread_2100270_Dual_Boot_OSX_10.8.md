---
title: "Dual Boot OSX 10.8"
date: 2013-01-01
forum: Apple Hardware Users
---

### Post by MTSR on 2013-01-01
Hy,
First of all, best wishes for the new year.

I have the last Imac 21.5 inches, 2.7 Quad Core, OSX 10.8. I'd like to Dual boot on it:
I applied exactly that recipe:
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx)
Because, thanks to the "new Imac" you even cannot use a CD to boot on it...
Anyway, no problem with it, worked perfectly.
The tricky stuff comes when I'm rebooting on the usb, I can "see" my usb key named "windows", I ask to boot on it, then I got this screen:
[http://doc.ubuntu-fr.org/_detail/installation/live_cd_maverick1.png?id=efi](http://doc.ubuntu-fr.org/_detail/installation/live_cd_maverick1.png?id=efi)
Then a black screen with lot of codes on it, the install stops:
"
[sdb] Write Protect is off
[sdb] Mode Sense: 00 00 00 00 
[sdb] Asking for cache data failed
[sdb] Assuming drive cache :write through
[sdb] Asking for cache data failed
[sdb] Assuming drive cache :write through
[sdb] Asking for cache data failed
[sdb] Assuming drive cache :write through
[sdb] Attached SCSI removable disk

"

So apparently it doesn't boot on the flash key, we can see it, as soon as the screen "non EFI" appears...

I tried with:
ubuntu-12.04-LTS (32 bits)
ubuntu-12.04-LTS (64)
ubuntu-12.10-desktop-amd64+mac.iso


notes: The flash key is 8 GB. Gave 500GB to Freespace, 500GB to OSX

In my opinion the pb comes from EFI, I though we could avoid it by using 64 bits.. apparently not..

I'm a bit depressed to be honest, any idea will be welcome...:(

Regards

---

### Post by MTSR on 2013-01-02
Any ideas ?):P

---

