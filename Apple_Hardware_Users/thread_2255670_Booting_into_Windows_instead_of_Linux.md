---
title: "Booting into Windows instead of Linux"
date: 2014-12-06
forum: Apple Hardware Users
---

### Post by jordan19 on 2014-12-06
[FONT=arial]Hello,[/FONT]

[FONT=arial]I'm on a mid 2010 15" MacBook Pro. I have Windows 8, Ubuntu and OS X on installed on my hard drive on different partitions. Everything was working fine until i reinstalled windows 8. Usually what happens is I hold down alt while turning on the MacBook and it opens rEFlt. Then all the OSs would be displayed. Selecting one would then load up grub, where the OSs would all be listed again, then I could make my selection. After reinstalling Windows, Linux wasn't listed on rEFlt. Also, grub won't load after selecting an OS on rEFlt.  So I ran a live disk of Ubuntu and did the boot repair. Now it shows Linux in rEFlt but when I select Linux it loads Windows 8. Also Grub still isn't loading.[/FONT]

[FONT=arial]Any suggestions would be appreciated.[/FONT]

[FONT=arial]Regards,[/FONT]

[FONT=arial]Jordan[/FONT]

[FONT=arial]Sent from my iPad[/FONT]

---

### Post by ibjsb4 on 2014-12-08
I have no knowledge of rEFIt, but when you reinstalled win8 it should of installed its boot loader and took over.

You say boot repair did not work.  Since you had a grub configuration working before, maybe reinstalling grub would work.  I like testing a suggestion before posting, but I have no way to do this one, not a apple user :)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=reinstall+grub&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=reinstall+grub&sa=Search&cof=FORID:9)

---

### Post by este.el.paz on 2014-12-08
> **jordan19 said:**
> [FONT=arial]Hello,[/FONT]

[FONT=arial]I'm on a mid 2010 15" MacBook Pro. I have Windows 8, Ubuntu and OS X on installed on my hard drive on different partitions. Everything was working fine until i reinstalled windows 8. Usually what happens is I hold down alt while turning on the MacBook and it opens rEFlt. Then all the OSs would be displayed. Selecting one would then load up grub, where the OSs would all be listed again, then I could make my selection. After reinstalling Windows, Linux wasn't listed on rEFlt. Also, grub won't load after selecting an OS on rEFlt.  So I ran a live disk of Ubuntu and did the boot repair. Now it shows Linux in rEFlt but when I select Linux it loads Windows 8. Also Grub still isn't loading.[/FONT]

[FONT=arial]Any suggestions would be appreciated.[/FONT]

[FONT=arial]Regards,[/FONT]

[FONT=arial]Jordan[/FONT]


@jordan:  I have the same MBPro . . . set up for triple boot, but 2 OSX's and a linux . . . the suggestion to reinstall rEFIt would be OK if you are running up to 10.7???  If you are after that, somewhere greater than 10.6.8 . . . rEFInd is needed.  If you already have rEFInd, try reading the instructions for "blessing rEFInd" . . . it gets "unblessed" when other systems get upgraded . . . .  

I also recently had this problem with GRUB not booting linux after upgrading OSX and doing the "blessing" . . . tried the various boot repair options . . . you might find the possible threads herein about it . . . .  I wound up "nuking" the Xu 14.04 . . . and did a fresh install of LM17.  Sometimes it's just faster to do a fresh install rather than spending hours trying to fix a problem that "shouldn't be happening, but is . . . ."  General wisdom seems to be OSX in first, then windows, then linux . . . .

e.e.p.

---

### Post by davidchute26 on 2015-01-02
[SIZE=2][FONT=microsoft sans serif]Next time you nuke - install ubuntu and use efi stub loader (ubiquity -b (using option key to select live CD so ESP is mounted). This will remove grub altogether so Windows can't interfere.[/FONT][/SIZE]

---

