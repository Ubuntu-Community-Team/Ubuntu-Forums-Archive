---
title: "Disable CDROM Probing?"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by Megatog615 on 2007-07-13
My old Toshiba laptop(which works GREAT by the way) has an odd problem. HAL, I believe, is constantly probing for a disc in the CDROM drive. Since this is obviously a resource hog, and is also causing the CDROM LED to blink every second, I'd like to be able to turn this feature off. I rarely use the drive anyway.

I fixed it temporarily by disabling the cdrom drive altogether with GRUB, but I don't know if I might need to use the CDROM drive in the near future.

How do I stop HAL from probing for a disc?

---

### Post by scxtt on 2007-07-13
do you need HAL to even be running constantly?  how often are you plugging things (CDs, USB) in? ... you could just "turn it off" until you *really* need it ...

---

### Post by Megatog615 on 2007-07-13
It's actually safe to disable HAL altogether?

---

### Post by scxtt on 2007-07-13
my gentoo install didn't even have HAL for a while ... but it's a bit different w/ ubuntu - HAL and DBUS are tied to eachother - so to stop HAL, you'd have to do **sudo /etc/init.d/dbus stop** - not totally sure if that's gonna hose up your box (i doubt it) and it wouldn't be permanent ... so, save all your work 1st ;)

---

