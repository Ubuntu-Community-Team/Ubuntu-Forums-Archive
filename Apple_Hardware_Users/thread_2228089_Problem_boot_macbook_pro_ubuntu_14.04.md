---
title: "Problem boot macbook pro ubuntu 14.04"
date: 2014-06-05
forum: Apple Hardware Users
---

### Post by arnaud5 on 2014-06-05
[FONT=arial]Hey,[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]i am currently experiencing problem with the boot of my computer. I had to install ubuntu on my macbook pro 13' from july 2009 for my master thesis and, finding it very convenient, i adopted it in january (ubtunu 13.04 I think). I recently updated my computer to ubuntu 14.04 but now I have to install a mac partition for my work. I have the install cd from mac but when I start my computer and try to boot the cd, the computer freezes, tries to read the cd and then ejects the cd.

I tried boot repair recommended repair but nothing changes[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]This is the boot info: [http://paste.ubuntu.com/7582604/](http://paste.ubuntu.com/7582604/)

I tried my dvd reader with another cd and it worked, so the problem doesn't come frome there.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I would really appreciate your help, it is actually a very important matter for me now :)

Thank you a lot for your time[/FONT]

---

### Post by zircon_34 on 2014-06-06
don't you have a recovery partition on Mac, something like option+R at boot or so?

---

### Post by arnaud5 on 2014-06-07
Hey :)

i finally did it! So if anyone wonders, actually the dvd reader was kind of broken (kind of because some dvds could be read, odd ...). But i transformed the install dvd into a live usb ([http://news.softpedia.com/news/How-to-Create-a-Bootable-Mac-OS-X-USB-Disk-214329.shtml](http://news.softpedia.com/news/How-to-Create-a-Bootable-Mac-OS-X-USB-Disk-214329.shtml)) and could install mac.

Now the problem was that I could not access the grub anymore, so I looked it up on internet and found this ([http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)). Actually it did not work but I installed boot repair from the live usb ([http://askubuntu.com/questions/449428/unable-to-locate-package-boot-repair-in-14-04](http://askubuntu.com/questions/449428/unable-to-locate-package-boot-repair-in-14-04)) and now everything is working fine!

Arnaud

---

