---
title: "Dead iMac G3"
date: 2007-01-08
forum: Apple PPC Users
---

### Post by tom717 on 2007-01-08
I recently updated to Edgy on my iMac and 2 days later the thing dies on me. To describe the symptoms, the power button does not turn the computer on. I'm not that interested in fixing the thing (unless it's easily done), I'd much prefer ripping it apart. What I want to know is whether anything is worth salvaging from it.
It's the 400 MHz model with a 10GB hard drive and a DVD-ROM slot loading drive. Any advice greatly appreciated

---

### Post by teaker1s on 2007-01-08
could create a router or some other interesting linux project with it

---

### Post by 3rdalbum on 2007-01-09
The Ethernet card might be useful to someone. The Firewire card will probably get you a few bucks as well.

---

### Post by handylinux on 2007-01-09
> **tom717 said:**
> I recently updated to Edgy on my iMac and 2 days later the thing dies on me. To describe the symptoms, the power button does not turn the computer on. I'm not that interested in fixing the thing (unless it's easily done), I'd much prefer ripping it apart. What I want to know is whether anything is worth salvaging from it.
It's the 400 MHz model with a 10GB hard drive and a DVD-ROM slot loading drive. Any advice greatly appreciated
Sounds like [this model]("http://www.lowendmac.com/imacs/dv.shtml"). You can get the repair manual [here]("http://home.earthlink.net/~strahm_s/manuals.html#imcs") (should be the "iMac, iMacDV, iMacDV Special Edition").

See under "Troubleshooting" in the service manual for power-on problems. It's possible the problem could be solved by resetting the PMU. Unfortunately, you have to open it up, which is a bear, to get at the PMU reset button. If that doesn't help, could be any of a number of problems, e.g. bad analog/video/power board, bad logic board, etc., all of them a major pain. The logic board is relatively easy to get to, the others are increasingly difficult. Such old G3 iMacs are not really worth repairing anymore, unless you have another handy to get parts. Sometimes logic boards &c are available on eBay.

As for salvaging, probably only the RAM card/s, HD, and DVD drive are worth pulling. AirPort card if there is one is definitely worth something. Modem is worth a little. There is no separate Ethernet or FireWire card; these functions are built into the logic board.

Please make an effort to recycle the leftovers, which are full of toxic stuff (pounds of lead in the CRT, for starters).

---

### Post by zipperback on 2007-01-09
> **tom717 said:**
> I recently updated to Edgy on my iMac and 2 days later the thing dies on me. To describe the symptoms, the power button does not turn the computer on. I'm not that interested in fixing the thing (unless it's easily done), I'd much prefer ripping it apart. What I want to know is whether anything is worth salvaging from it.
It's the 400 MHz model with a 10GB hard drive and a DVD-ROM slot loading drive. Any advice greatly appreciated

It's an old system but it would make an excellent router / firewall for your network.

You could also run a nice little web server on it as well.

I have an old iMac G3 that I've been using as a webserver hosting a few domains on it, and it works great for it.

Contrary to popular belief you do NOT need the latest and greatest hardware to run a good solid web hosting system.

---

### Post by bodycoach2 on 2007-01-10
Try a different power cord. I had an iMac G3 333 Mhz have the same symptoms. Out of no where. Just before I was going to trash it, I tried another power cord. Booted right up just fine. Might even try simply pushing the power cord in a bit more.

BTW, when I tried to upgrade to Edgy, the iMac wouldn't work. It tried to boot, but never made it past the firmware. I reinstalled Xubuntu Dapper 6.06.1 (6.06 wouldn't install), and it's working normal again.

I'd like to hear if it works again.

> **tom717 said:**
> I recently updated to Edgy on my iMac and 2 days later the thing dies on me. To describe the symptoms, the power button does not turn the computer on. I'm not that interested in fixing the thing (unless it's easily done), I'd much prefer ripping it apart. What I want to know is whether anything is worth salvaging from it.
It's the 400 MHz model with a 10GB hard drive and a DVD-ROM slot loading drive. Any advice greatly appreciated

---

### Post by Peadar on 2007-02-06
I've had the same problem - with an iMac G3 350MHz. The on-button light comes on briefly, then it's dead. It seemed to happen when I connected an external HDD that was already powered. I've tried various key combinations with the on button, but it's completely dead.

I've tried a different power cord. Also opened up the little hatch where you can access the RAM, but can't see anything that looks like the PMU (?what *does *it look like?) anywhere near the RAM, or figure how to reset it.

Any suggestions? It's my first Apple, only had it for a week!!:(

---

### Post by ssam on 2007-02-07
if you do decide to sell off parts i would be interested in the dvd drive. thanks

---

### Post by nolageek on 2007-02-12
> **Peadar said:**
> I've tried a different power cord. Also opened up the little hatch where you can access the RAM, but can't see anything that looks like the PMU (?what *does *it look like?) anywhere near the RAM, or figure how to reset it.

It's a little button that you have to press with a pencil.  I had the same problem as both of you and that fixed it.

---

### Post by Peadar on 2007-02-13
Ive found the pmu and pressed it, also replaced the PRAM battery. Still the same.

---

### Post by cvmiller on 2007-02-14
> **Peadar said:**
> Ive found the pmu and pressed it, also replaced the PRAM battery. Still the same.

I suspect the power supply has failed. I had the same thing happen to my G3 iMac (slot loading). My son has just resurected the machine, but it doesn't look like it did before (he is using a PC ATX power supply to power the unit). If you aren't good with a soldering iron, you are probably better off donating the unit to someone who is.

I hope this helps,

Craig...

---

### Post by bodycoach2 on 2007-02-14
You could alway keep the computer, and use it for a case mod, like this:

[http://www.macmod.com/content/view/348/193/]("http://www.macmod.com/content/view/348/193/")

I've got two that actually work, but I'm hoping to have enough time, money, and knowledge to mod on up.

---

### Post by lfloyd on 2007-02-15
imac has overheating problems because there's no fan.  Take the motherboard out, hard drive cdrom, and their are websites that tell yu how to hook up motherbard to ATX power supply definitely not for the faint of heart.  But the imac board should run without mac's useless power supply heating up the whole motherboard.  Welcome to the imac grave their are many of us.  But in my case the imac board was indeed salvageable when remove from the imac case

---

### Post by tom717 on 2007-02-28
Restting the PMU worked! Although one corner of the screen is now inexplicably purple; it looks as if someone went at with a magnet.
Anyway, thanks for all the help. For anyone else having trouble finding the button, this helped me [http://mrjcd.com/junk/PMU.jpg](http://mrjcd.com/junk/PMU.jpg)
I can't believe it hasn't been working since boxing day when it was so simple to fix.

---

