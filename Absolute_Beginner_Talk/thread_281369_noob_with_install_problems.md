---
title: "noob with install problems"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by grahamo87 on 2006-10-20
I tried search for my problem, but just couldn't locate it.
when I try to go through the install, it goes through the whole check list and the bar gets completely loaded, but then it says

Failure to start the X server. It is likely that it is not set up correctly.

Any assistance on this?

---

### Post by ReaderRat on 2006-10-20
If you are installing from the Live CD, you may have a bad disc. Did you download an .iso image and burn it to get your copy?

---

### Post by ReaderRat on 2006-10-20
How much RAM do you have installed? What kind of machine is it?

---

### Post by grahamo87 on 2006-10-21
yeah its an iso image CD

i've got an amd64 3800+ with 2GB of DDR Ram, a ATI X800Pro and 2 160GB hard drives. One has XP installed, the other is the linux drive.

---

### Post by ReaderRat on 2006-10-21
You have **plenty** of RAM to run any distro....Did you burn the disc slooowly (4X)? Fast burns usually don't work.

---

### Post by grahamo87 on 2006-10-21
i did it at 40x, looks like the lowest i can go is 8x. i'll try that and report back.

---

### Post by ReaderRat on 2006-10-21
There is an option to check the disc in the boot screen. This takes a while, but it catches disc errors.

---

### Post by grahamo87 on 2006-10-21
ok. i'm just about done burning. If I don't respond in 10 or 15 minutes, it worked.

Thanks

---

### Post by ReaderRat on 2006-10-21
These are for your future reference:

ATI - How to install the drivers
          **[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)**

Dual Booting - On Two HDDs
    **[[b]Dual-Booting (Two HDD)**](http://www.ubuntuforums.org/showpost.php?p=1606469&postcount=1)[/b]

---

### Post by grahamo87 on 2006-10-21
I ran the disc checker, came out ok. Then when I tried the install,  the error came up again

---

### Post by ReaderRat on 2006-10-21
> **grahamo87 said:**
> I ran the disc checker, came out ok. Then when I tried the install,  the error came up again
This is as far as I can help. All of these things cleared up what it's **not**, but someone with more experience will have to help you now.

Good Luck...

---

### Post by grahamo87 on 2006-10-21
anybody?

---

### Post by progmanalpha on 2006-10-21
ok, I'm assuming you are trying to install 6.06 LTS. I have had problems with those install disks on a few computers. and especially radeon cards and the X server have not always been the best of friends.  There are a few things you can try though:

If you can get to a terminal prompt (command line) then you can install manually using apt-get doing something like 

```
sudo apt-get install ubuntu-desktop
```

I'm not sure if you can get to a command prompt but this might work if you can.

If that works then at least ubuntu is installed and you can go about trying to fix your X server configuration file.  It is probably just a matter of changing your driver to a different one (i.e. if it says ati, try switching to fglrx

I know this might not be very clear so if you have any questions just post and I'll try to clarify what I mean.

---

