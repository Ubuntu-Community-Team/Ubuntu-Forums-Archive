---
title: "Ubuntu for older laptop?"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by TygerTung on 2008-01-29
My Fiance (Wife on friday) Has this old Dell Inspiron 5000 laptop.

I think somone has had a go at it because it's got a massive 320mb of ram.

Not sure what processor it has, maybe a P3 or somthing like that. It's got a 6 GB HDD and a CD Rom drive and a floppy drive and a whole 1 usb port!

Now while windows 98 runs alright on it, it is a bit crappy being a little unstable and it's not very plug and play friendly like the more modern windows. Also I can't get the internet to work on it.

Would it be possible to wack on ubuntu? Or would it be too slow, and would I be better off to wack on windows 2000, which should run alright as it has a designed for windows 2000 and windows 98 sticker on it. I also hear windows 2000 is quite plug and play friendly just like XP which is reasonably good except it wont run very fast on the laptop.

---

### Post by jan quark on 2008-01-29
I would suggest using Xubuntu, its a slim version of Ubuntu
runs perfectly on my older desktop pc

---

### Post by benfindlay on 2008-01-29
I would personally recommend xubuntu over ubuntu. The graphical interface of xubuntu is much more light-weight and older-machine-friendly. It still looks good too!

Alternately if you really wanted to put ubuntu on, I would recommend the alternate install cd over the live cd, as its installation is much better for older machines, but you still get the same end product of ubuntu-goodness!

Hope this helps

---

### Post by TygerTung on 2008-01-29
Actually I wacked in the ubuntu live CD which I used to fit ubuntu to this computer but the laptop didn't like it, it told me no file system or somthing like that.

Whats the deal with that eh?

---

### Post by jan quark on 2008-01-29
is the booting order correct on your laptop
does it first search for a bootable system on your cd rom drive?
just a guess

i would also recommend using the alternate CD it is much more stable than the Live CD

---

### Post by TygerTung on 2008-01-29
Yep it does, it only likes to boot off the hard drive it seems or it's so old fashioned that it has a hernia about it.

---

### Post by soleille on 2008-01-29
I have a pretty old laptop too (Thinkpad T20, Pentium 3, has the same designed for 98/2000 sticker) and while I'm still new to Ubuntu (Gutsy) and haven't had time to test how it performs if I do lots of stuff, it seems to be equal/a bit faster than Win2000 as long as you aren't running Crossover.

Win2K is fine on this machine, by the way, but as for plug and play, it isn't perfect- while USB plug and play works ok (most of the time), switching PCMCIA devices or the ultrabay (hot plugging capable) CD drive makes the system freeze.
Also, one USB port (and USB 1.0 I guess) would drive me crazy, but you can get PCMCIA cards that have 4 USB 2.0 port for under 10-20 dollars- saved my life :o)
And with your tiny hard drive and no burner, you'll need a way to transfer files in under a day's time :O)

A 6 GB drive is bad with Win2K though- while I've run it on a much slower desktop system (I think it was a P1) I felt the worst bit was how much space the system alone used up (don't know if that's much better with Ubuntu)

I've replaced the hard drive with 60 GB and the drive with a CD burner/DVD combo, by the way, but the rest should be fine for both Win2K and current Ubuntus.

---

### Post by TygerTung on 2008-01-29
Oh so is it pretty easy to change the hard drive and the optical drive so it has a CD burner on it is it?

I wonder why it doesn't want to load up ubuntu from the CD, hmmmmm.

---

### Post by soleille on 2008-01-31
How hard it is to replace parts really depends on the model - while I haven't done it myself, just watched, in T20 everything was pretty accessible, but we basically had to take my old (yes, the wayyyy older model is my "new" computer) R40e apart to get to the optical drive (the puter was just uable as spare parts anyway)
I'd say a "new" hard disk would be the most important, and that one is easy on almost all computers, for some you don't even need screwdrivers :o)
And if you get a USB extension, there's always external options, too.

By the way, I can report that Ubuntu Gutsy works like a charm for me, the partition it uses is less than 10 GB, by the way. If it weren't for Microsoft reader wich I can'tget to run, I think I'd get rid of Win altogether by now.
Sorry I'm no help with the load from CD issue, I had my boyfriend do the setup for me :o)

---

### Post by cbtengr on 2008-01-31
> **TygerTung said:**
> My Fiance (Wife on friday) Has this old Dell Inspiron 5000 laptop.

I think somone has had a go at it because it's got a massive 320mb of ram.

Not sure what processor it has, maybe a P3 or somthing like that. It's got a 6 GB HDD and a CD Rom drive and a floppy drive and a whole 1 usb port!

Now while windows 98 runs alright on it, it is a bit crappy being a little unstable and it's not very plug and play friendly like the more modern windows. Also I can't get the internet to work on it.

Would it be possible to wack on ubuntu? Or would it be too slow, and would I be better off to wack on windows 2000, which should run alright as it has a designed for windows 2000 and windows 98 sticker on it. I also hear windows 2000 is quite plug and play friendly just like XP which is reasonably good except it wont run very fast on the laptop.

I'm running Ubuntu 7.10 on an Inspiron 5000.  It has 512mb RAM, 12GB HD.  The USB is the older 1.1, I added a PCMCIA card with 4 USB 2 connections.  It had Win ME and was ready to be retired when I tried Ubuntu just to see what would happen.  Six weeks later and it is running just fine & Wifi also works.  Xubuntu would probably be a good choice too.

---

### Post by Martin Witte on 2008-01-31
> **TygerTung said:**
> Oh so is it pretty easy to change the hard drive and the optical drive so it has a CD burner on it is it?

I wonder why it doesn't want to load up ubuntu from the CD, hmmmmm.


Did you burn your Ubuntu live disk as an iso? See [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by TygerTung on 2008-03-06
Everyone will be pleased to know that I have successfully installed Xubuntu on the laptop.

It seems to go fine and I used the alternative installation which I prefer.

Not too many problems other than not being able to work out how to install flash, I don't know how to force quit any programs (currently have the update manager frozen and can't seem to make it go away, alt, ctrl, del doesn't seem to bring up the task manager), but other than that it seems pretty good, runs at a reasonable speed.

Does anyone know how to work out what CPU and other system specs it is fitted with?

Cheers,

Sam

---

### Post by oldos2er on 2008-03-06
For Force Quit, hit Alt-F2, type in "xkill" then click on the window you want to kill.

 For hardware specs, type "lshw" and "lspci" in a terminal.

---

### Post by Jay Jay on 2008-03-06
First of all, welcome to Xubuntu - you've made a good choice and I hope you enjoy using the distro :)

Like yourself I also use a P3 laptop - and I've beefed it up a bit to increase performance. I would suggest you upgrade the hard disk asap, 40 & 80GB 2.5" units can be found fairly cheaply and would give you much more room to play with. My rig also has just one built in USB (1.1) port, but I've got around that by using a four way splitter cable and I also use a PCMCIA USB 2,0 card for devices that require faster transfer speeds. So as you can see there's lots of options and none of them will break the bank.

As oldos2er has stated you can find out your hardware specs by using "lspci" or "lshw" from the Terminal. If you prefer a GUI format, you could also add one of the following programs from Add/Remove Applications:

Hardware Information
Sysinfo
Hardinfo
Device Manager

Plus you should be able to find out details from the Power On Screen Test that should be displayed when the machne powers up and the BIOS page too. 

Hope this helps and once again, welcome.

---

### Post by TygerTung on 2008-03-06
Well thanks everyone.

I found out by disabling the dell splash screen that it has a 500mhz celery processor.

It says ACPI: [package] has zero elements (debD6cc0) type of deal when I turn on the computer, it comes up a number of times, but then the computer seems to continue processing as usual. This error message seems to have no effect.

I have been reading up about this elsewhere on the forum and it seems that it has somthing to do with the fan? the fan seems to go all the time and it hasn't started smoking or anything like that so it can't be too bad?

---

