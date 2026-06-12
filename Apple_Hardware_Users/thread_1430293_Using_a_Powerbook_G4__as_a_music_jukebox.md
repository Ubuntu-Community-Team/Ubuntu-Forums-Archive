---
title: "Using a Powerbook G4  as a music jukebox"
date: 2010-03-15
forum: Apple Hardware Users
---

### Post by polar11 on 2010-03-15
I want to use an old Powerbook i have as a music juke box and am thinking of using ubuntu to run it - assume that i will dual boot with a small partition for osx?

and then run an external hard drive with flac encoded music - into laptop then usb dac to hifi

Will ubuntu run ok on this machine?
I have removed all the stuff on the old hDD - anything else i need to do?
any hints that will make the process easier?

thanks

---

### Post by polar11 on 2010-03-18
bump?

---

### Post by linuxopjemac on 2010-03-18
Ubuntu will run on that machine, although I would install Debian Lenny.
Go for the netinstall:

[http://cdimage.debian.org/debian-cd/5.0.4/powerpc/iso-cd/debian-504-powerpc-netinst.iso](http://cdimage.debian.org/debian-cd/5.0.4/powerpc/iso-cd/debian-504-powerpc-netinst.iso)

Boot:
hold the "c" key after the boing

If that does not work, boot in open firmware (command+Apple+o+f)
then:
```
boot cd:,\\:tbxi
```

hit ALT in the installer to see boot options. I would go for 32-bits on your machine ;)

---

### Post by linuxopjemac on 2010-03-18
I would make two partitions first from within an OSX installation disc. Install OSX on the first partition. Then install Debian on the second one, using the netinstall CD. You have to set yaboot.conf later to be able to dual boot your Mac.

---

### Post by polar11 on 2010-03-18
thanks for your reply linuxopjemac - i have looked at debian and TBH it looks a bit advanced? - i am a bit new to all this - it is fairly straightforward for a new user???

have also found Watt OS - that looks perfect - slimmed down unbuntu - however power pc in progress so no release yet.

hence thinking unbuntu would be a good first step -  then onto watt os?

so is debian the way to go? or something else?? (only have 512mb ram 1.5 processor)

thanks for info regarding install

ps:

the other issue, is i want sound drivers to work from the box or requiring minimal updating - any distros offer this?

---

### Post by linuxopjemac on 2010-03-18
Debian is easier to install on PPC than Ubuntu, believe me!

---

### Post by linuxopjemac on 2010-03-18
I have no experience with sound stuff. Looking at Watt OS, you can achieve the same with Debian. OpenBox/LXDE is also available for Debian.

---

### Post by linuxopjemac on 2010-03-18
If you have patience ...
[http://www.planetwatt.com/index.php?module=Dizkus&func=viewtopic&topic=760](http://www.planetwatt.com/index.php?module=Dizkus&func=viewtopic&topic=760)

---

### Post by polar11 on 2010-03-18
thanks for the debian idea- looking online seems like it could work really well on an older machine - i read somewhere that it only needs 90mb ram to run

also there do not seem to be the problems with sound drivers 

no live cd for powerpc - but i think i might take the plunge!
thanks

---

### Post by linuxopjemac on 2010-03-18
What do you have to lose? Just go for it!

---

### Post by tgalati4 on 2010-03-18
The Wolfsen codecs are pretty good on the powerbook.  Why do you need a usb dongle?  Can you hear the difference?

---

### Post by polar11 on 2010-03-18
just thought that using a USB dac would result in less interference?

thinking behringer uca202 or if this proves poor then musical fidelity v dac

however if the internal dac is good then perhaps, i will skip the behringer and just save for a v dac

---

### Post by polar11 on 2010-03-22
thanks for recomending Debian 5 linuxopjemac

Installed yesterday - went like a dream!

The Debian installer was great, all very simple and straightforward (i used CD1 ISO 650mb installer). 

It took about 40 minutes to install, i just wiped OSX in the end and am just running Debian as apple are no longer providing updates for 10.3.9 (actually havent been for over a year).

All the hardware was found without issue and depite what i had been expecting - having to search and download loads of packages through the command line -everything just worked. 

I have added grip and another small music player - all really easy and straightforward with the package manager.

The machine is only a 1.5ghz with a very small 512mb RAM - debian boots up needing about 120mb MB ram - so plenty spare and boots in about 1 minute 20 seconds.

So to sum up, if you have an old G4 gathering dust - debian lenny will revive it!

The only thing i need to sort is flash as currently i can't watch youtube on it - but hopefully this wont take long

---

### Post by linuxopjemac on 2010-03-22
Great work. If you want a fast desktop, switch to LXDE. I did that this weekend on my PowerBook G3 with Lenny and I must say, it rocks!!!

---

### Post by polar11 on 2010-03-22
had a quick look at lxde, looks great very light on system resources -a have a couple of stupid questions:
i assume i download with the package manager and install, then

will it prompt me to choose a desktop for each session? or do i make one default?
and will exaile etc still work or do i have to use the bundled music software?

---

### Post by linuxopjemac on 2010-03-22
yes, with synaptic package manager you install lxde and then you logout. From the GDM (login window), which you can also make light weight btw, you select lxde as session, you can also set it as default. All your software will still be working, unless exaile is a strict GNOME thing, which I doubt.

---

### Post by polar11 on 2010-03-22
thanks for the quick reply - i will download and give it a go

---

