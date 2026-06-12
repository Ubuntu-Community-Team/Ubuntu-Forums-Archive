---
title: "Cant install anything"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by slutbit on 2008-01-13
Im a real newbie, some friends has tried to help me over internet but i think theyve given up. I tried to download a torrent program, so i try with Ktorrent from "Add/Remove Application":

"Canonical Ltd. provides technical support and security updates for KTorrent
KTorrent cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type."

so I try from terminal writing:
"apt-get install ktorrent"

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ktorrent"

Two different errors???

then i try with BitTorrent:

But it seems like its already installed but i try writing:
"apt-get install bittorrent"
answer is bittorrent is already the newest version.

so i write "bittorrent":
"bash: bittorrent: command not found"

It continues like this for the most of the programs, luckily not for mozilla so i can at least write this.

---

### Post by taurus on 2008-01-13
Sounds to me like you don't have all the repos available in /etc/apt/sources.list.  I assume you are running Gnome, go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and put a check for all the lines except the last one, Source code and the CDROM at the bottom window.  Close that and then press Refresh.  Now, you can install ktorrent from synaptic or close synaptic first and open Add/Remove again if you wish.

---

### Post by Xavieran on 2008-01-13
It looks like you have installed 32 bit Ubuntu on a 64 bit box...

Could you please post the output of```
lshw -C cpu | grep width
``` and ```
uname -a
```
That way we will be able to definitely see if it's an architecture problem...

---

### Post by m_atif on 2008-01-13
Okay... 
first are you able to install any other package/software? e.g.
sudo apt-get install vlc

vlc is a nice media player. I have just written this thinking you might not have that installed. 

If you cannot and you have the same results, first try

sudo apt-get update
sudo apt-get upgrade

then try to install the software you wish to install

if that does not work, then please type

cat /etc/apt/sources.list

Cheers,

and paste all that lengthy output here.

---

### Post by slutbit on 2008-01-27
Thank you Taurus, seems to work now. succeded installing both vlc and kdevelop.

And Xavieran, i choose to download the:
 * Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)
instead of:
 * 64bit AMD and Intel computers
at ubuntu.com cause i think i have a Intel Celeron M processor 530 1.73

When i write what you gave me it spits:
64 bits
and the other stuff is:
Linux slutbit-raptop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

I really hope i didnt install the wrong version :confused:

---

### Post by Kilz on 2008-01-27
> **slutbit said:**
> Thank you Taurus, seems to work now. succeded installing both vlc and kdevelop.

And Xavieran, i choose to download the:
 * Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)
instead of:
 * 64bit AMD and Intel computers
at ubuntu.com cause i think i have a Intel Celeron M processor 530 1.73

When i write what you gave me it spits:
64 bits
and the other stuff is:
Linux slutbit-raptop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

I really hope i didnt install the wrong version :confused:
[URL="http://www.intel.com/products/processor/celeron_m/index.htm"]
According to Intel[/URL] you have a 64bit processor and could install the 64bit version of Ubuntu. You may want to consider installing it before you put to much work into the 32bit install. Because you cant upgrade from 32 to 64 bit, its a reinstall.

---

