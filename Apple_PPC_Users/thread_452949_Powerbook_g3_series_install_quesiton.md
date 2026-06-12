---
title: "Powerbook g3 series install quesiton"
date: 2007-05-23
forum: Apple PPC Users
---

### Post by richaoj on 2007-05-23
hello, i am new to the world of mac.  i bought an old powerbook g3 for 50 bucks from a friend of mine, pooped in a hard drive, and installed os 9.  i have bootx on the system, and it seems to work fine in loading the kernel.  i am trying to intall fiesty ppc version on this machine.

however, at some point in loading the linux kernel, the following error message pops up:

<code>
check root=bootarg cat/proc/cmdline
or missing modules cat /proc/modules ls/del
Alert! does not exist! dropping to a shell

BusyBox v1.1.3 (debian) built in shell

</code

can anyone help?

---

### Post by richaoj on 2007-05-24
allright, i finally got the kernel to load and can get into the installer.  however, i get to the partitioning state and the partitioner cannot write to the disk!
it just keeps on coming back up again!?

could this be a problem with the firmware on the harddrive?
seagate 40G volume
now trying ubuntu-6.06 Alternate CD PPC
Mac Powerbook G3

---

### Post by Tommy on 2007-06-01
> **richaoj said:**
> allright, i finally got the kernel to load and can get into the installer.  however, i get to the partitioning state and the partitioner cannot write to the disk!
it just keeps on coming back up again!?

could this be a problem with the firmware on the harddrive?
seagate 40G volume
now trying ubuntu-6.06 Alternate CD PPC
Mac Powerbook G3

I have a PowerBook G3 Series -- also known as a Wallstreet II or PDQ. For this situation it won't matter but as you resolve specific problems you'll want to specify exactly which model you have.

Unfortunately, as Ubuntu has progressed, it's harder and harder to install on Oldworld Macs, and they haven't been supported by Ubuntu for a long time. Look for other threads in this forum... and a page on the wiki. As I find some relevant ones I'll try to link them here.

I don't mean to discourage you -- you have made good progress! -- it's just that the going can be tough. On my machine I'm still running Dapper 6.06 (upgraded from 4.10, I think) because it works fine and I know there are some additional issues installing 6.10 and 7.04.

edit: First look at [https://help.ubuntu.com/community/Installation/OldWorldMacs](https://help.ubuntu.com/community/Installation/OldWorldMacs) but that info seems outdated. As  you learn maybe you could add to it.

Once you get the install done, the other information at [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ) may be helpful...

HOWEVER there are some unfortunate bugs that affect all G3 systems for the past year or so. Multimedia software, mostly -- it will fail because the underlying code doesn't know how to deal with a G3 (versus G4 or G5) processor. Some of those may be fixed in Feisty 7.04 but I haven't heard (and I'm still two releases behind that).

another edit: Search the forums for "oldworld" -- there are lots of threads! I haven't been here much lately and there are others here. Maybe we need a separate oldworld forum?

Here's one for example: [http://ubuntuforums.org/showthread.php?t=446370](http://ubuntuforums.org/showthread.php?t=446370)

---

### Post by richaoj on 2007-06-02
Success!  I have finally succeeded!!!!!  I have even now gotten Wifi working with Orinoco silver pcmcia card!  the only thing left is the dang battery, and properly configuring the ATI rage mobility card for best rendering!

---

### Post by Tommy on 2007-06-05
> **richaoj said:**
> Success!  I have finally succeeded!!!!!  I have even now gotten Wifi working with Orinoco silver pcmcia card!  the only thing left is the dang battery, and properly configuring the ATI rage mobility card for best rendering!
That is great news! Were you able to get Feisty installed, or did you have to downgrade to Dapper?

Also, I won't necessarily be able to help, but do you mean a software problem with the battery, or a dead battery? My Wallstreet has a dead PRAM battery and I have to reset the computer every time I turn it on (Control-Shift-Command-Power or something-- whatever it says under the port door under the hinge). Sadly the PRAM battery is deep inside requiring complete disassembly to replace, so I haven't bothered. The main power battery died a few years ago (after quite a few years of faithful service) and I haven't bothered to replace it either, though both batteries are still available from various sources.

---

### Post by gvigorus on 2007-09-19
> **richaoj said:**
> Success!  I have finally succeeded!!!!!  I have even now gotten Wifi working with Orinoco silver pcmcia card!  the only thing left is the dang battery, and properly configuring the ATI rage mobility card for best rendering!

Hi. I realize this is an old post, but will you describe how you got your Wavelan Silver to work under Feisty PPC? I'm struggling with it. Thanks

---

