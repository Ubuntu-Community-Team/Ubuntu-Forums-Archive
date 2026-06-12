---
title: "Ubuntu 14.04 dual boot on MacBookPro1.1 - slow boot 75 seconds"
date: 2015-07-03
forum: Apple Hardware Users
---

### Post by Claudio81 on 2015-07-03
Hi everyone,
I have a MacBook Pro 1.1 still in good working order.
I installed:
 - Snow Leopard
 - Refind in SL in order to get the Ubuntu live USB booting
 - Ubuntu Trusty Tahr

The drive is a good old sataI, that makes no secret when it is working, a good grinding noise.
What I cannot bear is the silence of the drive for a whole minute during boot, except some sparing noise.
After that a real noise for 15 seconds.
That leads me to the conclusion that the actual boot is of roughly 20 seconds!

Things I've done so far to improve the situation:
 - Installed Refind in SL again, in order to work also on the new Linux partitions
 - Ran in Ubuntu the Refind script mkrlconf.sh
 - edited /etc/default/grub as follow:
     ```
GRUB_HIDDEN_TIMEOUT=0.0
GRUB_TIMEOUT=0.0
GRUB_CMDLINE_LINUX_DEFAULT=""
```
         then command:
    ```
sudo update-grub
```
 - installed bootchart

Here is the bootchart image, right-click/view-image for full size:
(I couldn't attach it because it would shrink and be unreadable, therefore I'll be responsible for hosting it for the next decade)
[IMG]http://www.cinemacorallomonselice.it/claudio-MacBookPro-trusty-20150703-3.png[/IMG]

And here is a breakdown of what I see during boot, left column are seconds:

```
0   EVENT : Select the Penguin on Refind
0   START : white screen with Penguin
4   END   : white screen with Penguin
4   START : black screen
11      START : flashing dash on top left screen
14      END   : flashing dash on top left screen
17  END   : black screen
17  START : purple screen
40  END   : purple screen
40  START : black screen
40      START : scrolling white messages lines
44      END   : scrolling white messages lines
60      EVENT : screen blanks/clear
60      START : half screen of yellow messages lines
61      END   : half screen of yellow messages lines
61      START : scrolling white messages lines
66      END   : scrolling white messages lines
70      EVENT : screen blanks/clear
71      EVENT : mouse pointer appears
75  END   : black screen
75  MISSION ACCOMPLISHED : Ubuntu drum sound in login screen
```

Hard Drive noises:
 - some minor noise between 11 - 14
 - little bit less minor noise between 40 - 46
 - drive really kicks in from 58 till the end

Any help will be highly appreciated!

---

### Post by este.el.paz on 2015-07-04
Yes.  That is correct.  It takes some time to boot the linux system when there is dual boot set up . . . moving through the various screens.  Be happy, don't worry . . . if you are booting into linux system you've done well.  General wisdom seems to be to use dual boot for apple computers . . . don't forget to read the "Mactel" sticky at the top of the sub-forum here . . . you might need to add "macfancntrl" or something like that . . . check it or find the "mike braxner" posts on the forum.

e..

---

### Post by Claudio81 on 2015-07-06
Thank you for your concern @este.el.paz, 'macfancntrl' is already at the top of my 'Ubuntu in Mac set up' list.
If I'm understanding right, I could have a fast boot 'blessing' the Ubuntu partition, but at this point I would end up with a single boot pc.
A lot of sources online (including the 'Mactel sticky' here) explain how to get a fast single boot, I wish I found one source stating to just give up on a dual boot.
You are so far the first one.
The 'Mactel sticky' states:
> Why is there are long delay booting up with only Ubuntu installed?
Because of how the Mac firmware works, it does not readily look for what Apple calls a "legacy OS" and searches for an EFI executable before resorting to starting the Linux bootloader.
If that is the case, why I have the purple Ubuntu screen at second 17 ?
If I could get Ubuntu start loading up at 17 it would be much better then 58, as it does now.
In this thread @vsh3r is complaining about 10 seconds of hard drive hesitation, not a whole minute!
[http://ubuntuforums.org/showthread.php?t=1613648](http://ubuntuforums.org/showthread.php?t=1613648)

---

### Post by este.el.paz on 2015-07-06
> **Claudio81 said:**
> 
, but at this point I would end up with a single boot pc.
A lot of sources online (including the 'Mactel sticky' here) explain how to get a fast single boot, I wish I found one source stating to just give up on a dual boot.
You are so far the first one.


@C81:

Hopefully you are understanding that I am suggesting that dual boot is considered to be better for being able to do any apple firmware updates that might come along . . . .  I have triple boot on my 09 MBPro . . . .  Maybe someone will be able to look through your charts and see something to adjust.  In my own experience if I don't set up a separate partition for GRUB . . . without that the linux system won't boot at all.  Possibly you could post your GParted partition map here to show what is there . . . ???

e..

---

