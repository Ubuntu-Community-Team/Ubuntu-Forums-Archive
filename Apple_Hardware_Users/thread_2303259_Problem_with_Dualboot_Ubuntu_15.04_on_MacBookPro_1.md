---
title: "Problem with Dualboot Ubuntu 15.04 on MacBookPro 11,1"
date: 2015-11-17
forum: Apple Hardware Users
---

### Post by matthaeus2 on 2015-11-17
Hi everybody,
I used the installation tutorial of [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation) to install Ubuntu as dual boot.
In order to fix the out of sync partition tables I applied the instructions of the following post: [http://ubuntuforums.org/showthread.php?t=1810275&page=19&p=11215214#post11215214](http://ubuntuforums.org/showthread.php?t=1810275&page=19&p=11215214#post11215214).
However I still cannot boot Ubuntu and rEFIt gives me the same error:[INDENT][COLOR=#333333][FONT=Ubuntu]"GPT partition of type 'Unknown' found, will not touch this disk"

[/FONT][/COLOR][/INDENT]
[COLOR=#333333][FONT=Ubuntu]My partition table:
[/FONT][/COLOR]```
[FONT=Menlo]Number  Start (sector)    End (sector)  Size       Code  Name[/FONT]
[FONT=Menlo]   1              40          409639   200.0 MiB   EF00  EFI System Partition[/FONT]
[FONT=Menlo]   2          409640       898884247   428.4 GiB   AF00  Macintosh HD[/FONT]
[FONT=Menlo]   3       898884248       900153783   619.9 MiB   AB00  Recovery HD[/FONT]
[FONT=Menlo]   4       900155392       902252543   1024.0 MiB  8200  [/FONT]
[FONT=Menlo]   5       902252544       977104106   35.7 GiB    8300 
[/FONT]
```[COLOR=#333333]

[FONT=Ubuntu]Has anyone an idea?[/FONT]

[/COLOR]Edit1: I just saw that the referred guide was last edited on2013-12-14. I will try a newer tutorial.


Edit2: I tried fixing the problem with live gparted, but I still get the same error.
[IMG]http://s24.postimg.org/nqp7cq1ol/Screen_Shot_2015_11_18_at_09_02_17.png[/IMG]

---

### Post by matthaeus2 on 2015-11-18
I found the solution:
gptsync using GParted live didn't work. So I at first I formatted the volume for Ubuntu as hfs+. Afterwards I run the command  
```
gptsync /dev/sda
```
to successfully sync the partition table.
When I installed Ubuntu 15.04 I formatted the hfs+ volume to ext4 and it all worked out.

---

