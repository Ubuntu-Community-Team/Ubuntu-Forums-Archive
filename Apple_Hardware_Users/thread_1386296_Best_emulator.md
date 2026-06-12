---
title: "Best emulator"
date: 2010-01-20
forum: Apple Hardware Users
---

### Post by malfindin on 2010-01-20
I need to virtualize a Power PC MAC running OS 9.22 and retire the physical system. Does anybody know what the best emulator is for this task.

I have gotten conflicting reports that Qmem and PearPC work, but have failed to get them running.

This is not just something on my wish list of things to do Tuesday, I need it for my business.

Any help would be really appreciated.

OS = Ubuntu 9.10 Karmic Koala

~malfindin

---

### Post by Ken147 on 2010-01-20
I would look at [Basilisk II]("http://basilisk.cebix.net/"). its a great emulator if you are going to use 9.2.2

---

### Post by malfindin on 2010-01-21
Baslisk II looks like it will do the trick. I'll post again when I've had a chance to implement it. Any thoughts on how to migrate a pre-existing sys to the Virtual version?

---

### Post by linuxopjemac on 2010-01-21
Google is your friend. You need at least a Mac ROM file. I tried Basilisk in the past. It works very well to emulate classic MacOS under Linux. Maybe you can make an image file of that computer of yours and open it up within the emulator.

some links
[http://wiki.oldos.org/Mac/68kEmulator](http://wiki.oldos.org/Mac/68kEmulator)
[http://www.math.colostate.edu/~reinholz/freebsd/apps_computer_emulators.html](http://www.math.colostate.edu/~reinholz/freebsd/apps_computer_emulators.html)
[http://www.emaculation.com/articles/intro.html](http://www.emaculation.com/articles/intro.html)

---

### Post by malfindin on 2010-01-21
Well here's the thing. I have upwards of 40 Virtual Linux/Windows systems I have made in VirtualBox and 10 or so in VMWare 7.5 which I just purchased, but I'm afraid to say, "I have no idea what a ROM file is or how to make one". 

Oh...I do know that "ROM" stands for read only memory, I just don't know why that would have anything to do with Virtual system migration.

I have never had to do anything with ROMs or BIOS before, even with all the VBox systems I have made.

---

### Post by linuxopjemac on 2010-01-21
You can download such a ROM file, if you don't want to make it yourself. I used one of a PowerMac Quadra, [here]("http://files.oldos.org/files/macdl/quadra650.rom").Just follow the links I provided, it will work.

---

### Post by Ken147 on 2010-01-22
for those people that need roms.....apple states that it is illegal to distribute there rom files without actually owning the computer that you have the rom image from, but people still distribute them anyways :)

---

### Post by malfindin on 2010-01-22
Well I do own three MAC's. Can I get the ROM off my own computers?

---

### Post by Ken147 on 2010-01-22
yes there is a utility that come with some versions of basilisk that lets you extract a rom.....what are the macs that you own?

---

### Post by linuxopjemac on 2010-01-22
[http://www.emaculation.com/quick/copyrom.hqx](http://www.emaculation.com/quick/copyrom.hqx)

---

### Post by igor_av on 2010-01-22
> **malfindin said:**
> Baslisk II looks like it will do the trick. I'll post again when I've had a chance to implement it. Any thoughts on how to migrate a pre-existing sys to the Virtual version?

BasiliskII is a 68040 emulator. It will only run 68k compatible OS (up to 8.1). If you need to emulate a PowerPC, look for Sheepshaver.

---

### Post by linuxopjemac on 2010-01-23
Igor: I am afraid that you are right. I used MacOS 7.5.something, the one you can download from Apple.

---

### Post by malfindin on 2010-01-25
What MAC's do I own...hmm...that's a good question?

One looks like a monitor. iMAC I think.
One is silver with translucent handles at all 4 corners.
The last is Blue and Gray with translucent handles at all 4 corners.

The have no writing on them, so how does one tell???

---

