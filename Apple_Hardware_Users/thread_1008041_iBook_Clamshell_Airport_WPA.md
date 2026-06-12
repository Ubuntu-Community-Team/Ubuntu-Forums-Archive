---
title: "iBook Clamshell Airport WPA"
date: 2008-12-11
forum: Apple Hardware Users
---

### Post by eraker on 2008-12-11
I can't post in this thread: [http://ubuntuforums.org/showthread.php?t=304217](http://ubuntuforums.org/showthread.php?t=304217)
so I guess I'll just post here.

For the past four years, I've periodically wandered around trying to see if anyone had found a solution to getting WPA to work under an old airport card (orinoco chipset) on an ibook clamshell. This has been almost like a part-time hobby, but I don't know anything about kernel coding so I just wait around for someone to figure out a driver/kernel-module solution and I try it and then if it doesn't work, I wait around some more.

Anyway, I was reading updates to an old thread (the one posted above), and I decided to try this kernel module again to see if it would work. It compiles fine and even seems to load fine but the problem appears to be in associating with the airport card. 

I figured out, for instance, that I have to blacklist not only the orinoco_cs module, but also the airport module and the orinoco modules (and in **that particular** order) in order to get the airport/orinoco modules not to load. But then the compiled module never gets connected with the airport card

For instance, when I run lsmod under the old system I get
```

Module                  Size  Used by
orinoco                45172  1 airport
hermes                  8352  2 airport,orinoco
```

But then with the new module loaded and the orinoco module removed, lsmod reads like this (the above lines now missing):
```

Module                  Size  Used by
wlags49_h1_cs         192298  0 
pcmcia                 48528  1 wlags49_h1_cs
pcmcia_core            49176  1 pcmcia
```

It seems that after years of part-time looking I'm close to getting a solution on this, but I don't know enough to know why the wlags module is not getting used by the airport/orinoco card. If I could figure that out, I think I could get it to work with WPA_supplicant.

Any ideas anyone would have would be greatly appreciated.

---

### Post by guybrush.d on 2009-10-15
Hi,
I just solved it!:P It was since February (when i got the clamshell) that i was looking for the solution! Well the problem is the airport and orinoco modules needs a firmware to manage
the airport card, if you look into the boot logs you shoould find some lines that say "Lucent/Agere firmware not found in /lib/firmware" or something. You just need to copy 
a file called "agere_sta_fw.bin" to /lib/firmware reboot and the wifi will work, you can get all the needed info on [COLOR=Red]_[http://linuxwireless.org/en/users/Drivers/orinoco](http://linuxwireless.org/en/users/Drivers/orinoco)_[/COLOR] 
2 more things:

1) you will need git-core to download the git repository.
2) the reported problem on firmare broken didn't happen to me so i didn't used recode_utf8, see the webpage for details.

The only thing that i don't like is that the light of wireless doesn't work i asked help and i'm waiting, i know it can because i tried opensuse before xubuntu and the light was flashing on it, but i love xubuntu for the laptop! so i'm waiting...CIAO!

---

### Post by orinoco77 on 2010-04-22
hi guybrush.d,

I think you might possibly have the solution to my problem. I'm hoping you can point me in the right direction at least. I have 2 clamshell iBooks. 1 Indigo and 1 Blueberry. Both have airport cards. The airport cards both work perfectly in the indigo, but neither will work in the blueberry. Both have Debian Lenny with XFCE installed (so not much different to your Xubuntu setup). The blueberry gives an error message on boot saying "failed to initialize firmware" when trying to set up the airport card. I've downloaded the agere firmware and put it in /lib/firmware, but it doesn't make any difference, the card still isn't set up correctly and the error message is exactly the same.

Obviously there's nothing wrong with either card, since both work in the indigo (flawlessly). I wondered if you might have any insight into what I might need to do to get this working.

When I installed Debian on the Indigo, it detected the airport card and allowed me to use it to download other packages during the install. The Blueberry does not detect the airport card during the install. I have no idea why.

Hope you have some ideas because I'm running out of them fast. :(

---

