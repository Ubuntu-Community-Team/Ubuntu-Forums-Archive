---
title: "boot loader help."
date: 2011-09-15
forum: Asus Ubuntu Support (CLOSED)
---

### Post by mthees08 on 2011-09-15
Good evening everyone,

First some background. I just bought an asus eee PC 1015 PED. First thing I did was partition the hard drive up and install ubuntu 11.04 on about 125 gb and mint os on 53 gb and shrink windows 7 down to 50 gb. I got all of this working without an issue. 

Then I attempted to install droid 2.2 . This is the issue.

it installs fine and if I use the old grub bootloader supplied by droid I get into win7 and droid os. If I use the new version I can get into mint ubuntu and win7. How can I add the droid os to the menu.lst. 

The problem here is this. I installed mint last in order to overwrite the droid grub. I now cannot find menu.lst on any of the partitions. How can I get all 4 os in the menu upon start up.

solved:Update: So to sum up adding drois os to the grub2 menu is doable in a simple way with just a little reading. open /etc/grub.d/40_custom add it there and run sudo update-grub.

---

### Post by garvinrick4 on 2011-09-15
grub2 and grub legacy do not play together well. When there is a Operating system I want to install
that does not use grub2 but legacy I just choose not to install grub legacy when asked by installation
program (usually anaconda). I then go to my grub2 install and update grub there it picks up the new
Operating system in os-prober and makes part of config and as a menuentry to boot from.

# There is no menu.lst in grub2
# Will this droid 2.2 even run on a P.C. or is it just cell phone software?

---

### Post by garvinrick4 on 2011-09-15
I do not know what droid 2.2 is have never used it.

---

### Post by mthees08 on 2011-09-15
> **garvinrick4 said:**
> I do not know what droid 2.2 is have never used it.

It is a phone operating system. I think I need to do some clean up and read the grub manual at the same time... Most likely that will help clear most of this up. Since I literally kept allowing everything to install it's own loader I think I created a bit off a mess... Though realistically it shouldn't be so hard to fix...

---

### Post by garvinrick4 on 2011-09-15
> Since I literally kept allowing everything to install it's own loader I  think I created a bit off a mess... Though realistically it shouldn't  be so hard to fix... Hey if it has got a file system and uses a boot manager you can fix it. Only one grub can go in mbr at any given time so purge what you do not need
and let OS with control make config file and if os-prober can pick it up as a operating system?????

---

### Post by David Andersson on 2011-09-15
I assume the latest system you installed also installed a boot loader in MBR. If you wish Ubuntu to control the boot, you can issue the commands *grup-install* and/or *update-grub* from within Ubuntu. Update-grub should detect other systems and add them to the menu.

Obviously, you need to run Ubuntu from a liveCD/liveUSB. Then parameters are required to the grub-install command, and some preparation. See "Reinstalling GRUB2" in [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

(Another alternative is to have grub legacy in MBR that chainloads secondary bootloaders placed in the partitions of each operating system. This is more initial work, but clean and elegant (in my opinion). Also less problem that systems are stamping on each others bootloaders when the they are updated.)

---

### Post by mthees08 on 2011-09-16
So basically it adds to grub 2 just like any other os you just need to add it in the 40_custom file under /etc/grub.d/

---

