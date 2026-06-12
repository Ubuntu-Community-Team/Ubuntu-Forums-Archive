---
title: "I now use Arch after a whirlwind of problems!"
date: 2008-05-12
forum: Arch and derivatives
---

### Post by smartboyathome on 2008-05-12
I finally got arch booting up, and am configuring based on the excellent beginners guide on the arch wiki. Be prepared, a long story on my journey to using arch on my external hard drive is about to begin! :KS

#####--BEGIN LONG WINDED STORY---#####
I started because of E17, which, from what I was told by the experts on the channel #e, is excellent for it as it offers minimal hassles with E17. Anyway, I was hesitant because I had a working Ubuntu box which fit my needs almost until a few weeks ago when I was being too stubborn and tried to figure out how to get Entrance to work instead of GDM. To say that I eventually ruined that install is an understatement.

Anyway, I got the 2007.08 disk and worked my way through the installer find the partitioner not working due to an error which I could not remember now (had something to do with a logical partition being too big, Gparted didn't pick this up :(). I just went straight to mountpoints and had it just erase the spare partition I had on the external hard drive from when I used it with my laptop, and set it to where my swap was. I then went through the rest of the steps just fine, but upon rebooting, I got an error that it couldn't boot grub ( error 18 ). It took me until the next Linux users group meeting (which was lucking an install fest :D) to get it resolved, where we found out it should have been set so that arch was booting to hd(0,0) instead of (1,0).

After that whole mess, I dropped my external hard drive on the floor, and luckily didn't break the drive itself but the usb chord. Seagate shipped me a new one which arrived in two and a half weeks (which is today). I am so happy that the external hard drive itself didn't break, especially since it was so cheap.
#####-- END LONG WINDED STORY ---#####

So now I am setting up X and am looking forward to using E17 on it. Wish me luck that nothing else happens. :lolflag:

I will still be using Ubuntu on my laptop, as all hell (sorry for the language if it offends anyone) would break loose if it broke.

---

### Post by chucky chuckaluck on 2008-05-13
sounds like a party.

---

### Post by ynnhoj on 2008-05-13
tl;dr

..welcome to arch!

:o

---

### Post by mips on 2008-05-13
The grub issue would have happened on most distros from what I can tell seeing you are booting off an external drive.

Welcome to the club. Live long and prosper as Spock would say ;)

---

### Post by smartboyathome on 2008-05-13
> **mips said:**
> The grub issue would have happened on most distros from what I can tell seeing you are booting off an external drive.

Welcome to the club. Live long and prosper as Spock would say ;)

Yep, it would have been worse on Ubuntu because it installs grub to hd0 unless you specify otherwise. :(

---

### Post by Dr Small on 2008-05-13
Congrats on getting Arch installed. Have fun! :)

---

### Post by smartboyathome on 2008-05-13
I am having fun. It is cool. I got e17 and gtkpacman, and everything works great now. I got Some of the apps I had on Ubuntu, plus some others I didn't know about. E17 is getting tricked out. ;)

---

### Post by finferflu on 2008-05-15
Welcome home :D

---

