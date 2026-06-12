---
title: "Live cd on an a Core Duo (first) Macbook"
date: 2007-02-21
forum: Apple Intel Users
---

### Post by hansoffate on 2007-02-21
I am trying to boot the kubuntu Fiesty Fawn Herd 4 on my macbook.  I get an error when it tries to boot.  It says try running apic=debug    or  noapic.  

Any ideas?
Thanks,
Hans

P.S.  I am just trying to install it, I don't really want to only use the LIVECD aspect of it.  Should i try the regular Ubuntu Fiesty Fawn Herd 4 live cd?

---

### Post by Gen2ly on 2007-02-22
I read something in the Fawn subforum that herd 4 is having trouble booting. u might wanna look there.

---

### Post by r.macfarland@gmail.com on 2007-02-22
Try this.. It worked with mine on Edgy..

To prevent a kernel panic which might occasionally occur, press F6 and enter one of the following parameters at the boot: prompt:
lpj=8000000 (for 2 GHz MacBook) or lpj=7330000 (for 1.83 GHz MacBook)
N.B.: It will automatically be applied to the installed system so you won't have to enter it manually ever again!


I also added this to my lilo.conf, just incase

append="lpj=8000000" 

I have the 2 Ghz Macbook. If you have the 1.83 use lpj=7330000  instead.

---

### Post by hansoffate on 2007-02-23
I just tried   doing what you said.  I pressed F6 then it said Boot Options:  so i typed.

lpj=8000000

It got further this time, now the error is as follows
VFS: cannot open root device "<NULL>" or unknown-block(8,1)
please append a correct "root=" boot option
kernel panic - not syncing: VFS: unable to mount root fs onunknown-block(8,1)

Any ideas? 
Thanks for the help
-Hans

---

### Post by r.macfarland@gmail.com on 2007-02-23
Try using this instead after hitting F6 and Boot Options. Try with and without hw-detect/start_pcmcia=false

install lpj=8000000 hw-detect/start_pcmcia=false

---

### Post by hansoffate on 2007-02-23
I'll try that when I get home today.  In the meantime, yesterday I tried to install kubuntu 6.10.  

It installed but when I chose the linux partition from rEFIt (the osx bootloader) it booted to grub with just the 

grub> _

With the _ blinking. What should i do? I know my / partition is /dev/sda3

Any ideas?
Thanks
-Hans

---

### Post by oskarloko on 2007-02-26
> **hansoffate said:**
> my / partition is /dev/sda3


Ok, I think this migth work

When you boot onto GRUB, lets do
```

find /boot/grub/stage1
root (hd0,2)
setup(hd0,2)
quit

```

As you can [see]("http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System"), the number for /dev/sda3 on GRUB is hd(0,2) 


Use rEfit as boot manager, it's ok.

Then reboot (it migth be automatic ) and may you boot on Ubuntu

---

