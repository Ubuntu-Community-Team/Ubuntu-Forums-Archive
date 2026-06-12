---
title: "Ubuntu 7 on Dell L400 a no go? Please help..."
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by s0ulreaver on 2007-04-25
Can't make Ubuntu 7 work on this laptop:
Latitude L400
256 MB RAM
10 GB HDD
ATI Rage Mobility P/M AGP 2x - 4MB

The memory test doesn't give any errors.
WinXP works fine.

Ubuntu 6.06 worked fine. I had the same issues I'm having now with Ubuntu 6.10
Booting from the Live CD, when the Gnome GUI should come up it goes into some sort of standby.
I tried installing with the alternate CD, the process finished ok but after restart it doesn't load the Gnome GUI.
I even tried reconfiguring the xserver to use the vesa driver but with no luck.
At some point I think I saw a brief message saying something like 'Your system cannot enter standby mode.
I have the latest BIOS available from Dell.

What can I try next? Please help.

---

### Post by jmagsho on 2007-04-25
So you don't see any errors, and I presume when it boots up it drops you at a terminal prompt for a login?

What happens if you login and type 'startx'

---

### Post by keithpeter on 2007-04-26
> **s0ulreaver said:**
> Can't make Ubuntu 7 work on this laptop:
Latitude L400
256 MB RAM
10 GB HDD
ATI Rage Mobility P/M AGP 2x - 4MB

The memory test doesn't give any errors.
WinXP works fine.

.

Hello

I can't help right now other than by saying that my L400, with a 20Gb hard drive, did manage to run Xubuntu 7.04 from the beta ISO. There were error messages when installing, and, like you, Xubuntu 6.06.1 works fine and installs after XP and resizes the partition nicely. See post below

[http://ubuntuforums.org/showthread.php?p=2387311#post2387311](http://ubuntuforums.org/showthread.php?p=2387311#post2387311)

I'll boot the release  live disc over the weekend and see if that runs without those 'stanza' messages. Oddly, with the particular CD-ROM drive I have for this laptop [ the laptop uses an external bootable CD drive via a docking station or cable] I was never able to boot from the alternate CD-ROM.

Nice little machines are they not?

---

### Post by panchito on 2007-05-05
Hi, I also have a Dell Latitude L400. It was working ok with Dapper but I had problems with Edgy and now Feisty. On my side, I have no problems to boot the alternate CD. The main problem with this laptop is that it goes into standby mode automatically. The solution for that is either to use BIOS A03 or to add the following boot parameter: acpi_sleep=s5_bios.

I'm doing several test right now so I will let you know about the result. You might wont to have a look on this thread: [http://ubuntuforums.org/showthread.php?t=83504&highlight=latitude+l400](http://ubuntuforums.org/showthread.php?t=83504&highlight=latitude+l400)

User walopower claims it works out of the box but I have serious doubts about that. What I'm trying to achieve now is to make speedstep and cpu frequency scaling to work. I will try a fresh install. If somebody have information about what I'm looking, please post. I already found some information like modprobing the modules like this:

speedstep-lib relaxed_check=1
speedstep-smi smi_port=0xb2 smi_cmd=0x82 smi_sig=1 

Modprobing like this used to work with Edgy but I had problems with governors. In Feisty, I can't load speedstep-smi.

Thanks!

---

### Post by mikeylikesit on 2008-01-16
i have a dell l400 running xubuntu 7.10 very nicely, everything works great expect for the battery management, (it drops from 50-0) but it might be a bad battery, also the ram is maxed out at 256 ;-( but i did a netinstall on mine, the card is a 3com and is supported,so that may be your best bet.

---

### Post by alanmzifa on 2008-01-25
Net Install here too. Ubuntu won't work on it, Ubuntu 7.10 needs 320Mb RAM apparently so it freezes in the install with errors and can't proceed beyond a certain stage.

Xubuntu 7.10 will install however.

---

