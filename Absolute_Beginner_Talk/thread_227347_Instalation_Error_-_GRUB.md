---
title: "Instalation Error - GRUB"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by Xios on 2006-08-01
Please help, Dire emergancy

I run winXP and Ubuntu from the same hard dirve, split into three partitions
38gb for winxp
36gb for ubuntu
2gb for swap

but the installer always crashes at 96% with the text, installing bootloader.
every time i start my machine now, all i get on my screen is

> Checking for boot record from floppy.. Not found
GRUB


and i cant access windows or linux, i have to run the live CD again to start fgrom scratch, whats going on

here is the log that it gave me to report




> Traceback (most recent call last):
  File "/usr/bin/ubiquity", line 130, in ?
    install(sys.argv[1])
  File "/usr/bin/ubiquity", line 55, in install
    ret = wizard.run()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 266, in run
    self.process_step()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 741, in process_step
    self.mountpoints_to_summary()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 1029, in mountpoints_to_summary
    self.progress_loop()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 538, in progress_loop
    raise RuntimeError, ("Install failed with exit code %s; see "
RuntimeError: Install failed with exit code 1; see /var/log/installer/syslog and /var/log/syslog

Please help ASAP, i need my to get my banking sorted tonight before i open my shop tomorrow! and doing the paper version takes to long. 

Please help

---

### Post by ironfistchamp on 2006-08-01
I don't know how to get your linux working but you can get back into windows by getting a win98 floppy, botting from that and typing "fdisk /mbr" at the prompt. You should now be able to get into windows. Or at least that is what I do when GRUB goes weird on me.

Hope it helps

Ironfistchamp

---

### Post by Xios on 2006-08-01
ok that kinda helps a small bit, thank you,

But how do I get ubuntu to install with it coming up with this error all the time?

---

### Post by anaconda on 2006-08-01
I quess, that your ubuntu install CD is faulty! (it is quite a common problem)

Burn new one, and remember to burn it slowly.. 4 x speed max

And check that the burn was successfull.

---

### Post by Xios on 2006-08-01
how can i get a new CD though?
the only internet connection i have is this laptop, which doesnt even have a burner, its a CD-Rom

so i cant download and install it, and the main PC is now usless, cant boot into anything, and i dont have any other boot discs or CDs apart from the ubuntu LiveCD, 

please help

---

### Post by ironfistchamp on 2006-08-01
If you could boot using the live CD you could get the 98boot disk as i suggested and use windows to download a new ubuntu disk and burn it. Might work for you.

---

### Post by Xios on 2006-08-01
does that make me lose my data though? i have alot of shop records on the hard drive that i cant afford to lose.


i dont feel comfortable fdisking the mbr, so is there another way? a more friendly way :-P

---

### Post by ironfistchamp on 2006-08-01
not to my knowledge. But then I am not that experienced. I have used fdisk /mbr many many times and Ive never lost anything. If you accidentally left off the /mbr you would end up in the fdisk app so you would just have to exit. It seems pretty safe to me.

---

### Post by confused57 on 2006-08-01
If you don't have a Win98SE boot disk, you can get it here:
[http://www.bootdisk.com/](http://www.bootdisk.com/)

Here's a link explaining how to replace(repair) the mbr:

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

