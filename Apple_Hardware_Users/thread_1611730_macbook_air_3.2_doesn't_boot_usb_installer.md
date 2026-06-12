---
title: "macbook air 3.2 doesn't boot usb installer"
date: 2010-11-02
forum: Apple Hardware Users
---

### Post by Luke.Hoersten on 2010-11-02
Trying to install Ubuntu 10.10 on new Apple Macbook Air 3.2 with USB key. I'm able to partition and install REFIT fine, but when I tell REFIT to boot from the USB key, it goes to black and says "boot error".

I then tried dd'ing the USB key partition to a local partition on the Macbook Air and booting that via a suggestion from another thread. It actually started loading the purple Ubuntu bootsplash-looking background then went straight to black even before the screen to select "try" or "install". Anyone know how to get the install USB to boot?

---

### Post by apoth on 2010-11-02
Keep going down the partition route, I don't *think* you'll get it to boot of USB.

Boot from the partition and when the screen goes purple (are there icons at the bottom of the screen?) then press a key and hopefully you'll get a language choice, then press F6 and choose the nomodeset option, escape and continue as normal.

---

### Post by Luke.Hoersten on 2010-11-06
That worked and I was finally able to boot the install iso off the harddrive. The next problem is installing. The installer wants me to umount "/cdrom" which is the install iso. It says it needs to edit the partition table so I can't have partitions on the same physical disk mounted. Anyone know how to get the installer to attempt to install without changing the partition table?

---

