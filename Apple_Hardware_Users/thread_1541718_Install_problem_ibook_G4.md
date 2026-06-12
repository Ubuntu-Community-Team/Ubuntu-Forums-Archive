---
title: "Install problem ibook G4"
date: 2010-07-29
forum: Apple Hardware Users
---

### Post by bjoernes on 2010-07-29
Hi!

I'm relatively new to both mac and linux. I'm trying to install the ppc version of ubuntu 10.4 on my ibook G4.

The problem I have is that the ibook refuses to boot from the cd.
When holding down c during start-up the cd/dvd drive is working for a while before it just starts up OSX.
I tried to purge the ram something but that did not change anything.
I also tried to boot with open firmware but that produces no results at all as long as i hold option+command+f+o i have a constant black screen and the machine seems to lock up, I have to use the power button to get it going again...

Any help with this issue would be greatly appreciated.

Best regards
Bjoernes

---

### Post by zeroti on 2010-07-29
Hm, maybe there's a password protecting your firmware..

Try booting-up holding the option button. If it asks for a password, you'll have to get the password or reset it.

This article gives a brief description of how to reset it:

[http://www.securemac.com/openfirmwarepasswordprotection.php](http://www.securemac.com/openfirmwarepasswordprotection.php)

You need to allow the computer to reboot three times while holding down the described keys (after removing or swapping a piece of memory.) If you need more details, there are some more articles out there. If you can boot into OS X and have administrator privileges, you can instead use sudo at the command line to reset or retrieve the encrypted password.

---

### Post by bjoernes on 2010-07-29
Thanks for the reply!

I just tried to boot while holding the option key... Unfortunately it produces no results other than black screen and lock up of the machine ](*,)

---

### Post by zeroti on 2010-07-30
This seems strange to me. If you can't use the option key.. Do you at least get the clickable button to choose the cd when you use the option button? If not, I'd guess it's not a problem with the GNU/Linux CD, but probably with your computer.. You might have some luck taking it to an apple store.

---

### Post by khelben1979 on 2010-07-30
Open it up and replace the harddrive? Then that would definitely say bye bye to MacOS X on it.

---

### Post by bjoernes on 2010-07-30
Hi!

I don't think it's a problem with the cd.. It must have something to do with the computer... Anything I try except starting OSX normaly results in the machine hanging at startup, nothing happening exept sounds from the drives and a totally black screen..

They said once you go mac you never turn back..... I on the other hand feel the urge to throw the mac out the window and not look back:x

---

