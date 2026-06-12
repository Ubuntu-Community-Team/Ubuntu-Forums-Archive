---
title: "Strange GRUB mapping problem"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by Hemmer on 2007-11-23
Why is it that my XP partition loads when calling root(hd0,0) when it is installed on the 3rd partition (hd0,2). When i try to run root(hd0,2), it tries to start vista, but hangs on "Starting up..." but thats a different problem. I just want to know why it is starting the wrong partitions? What am i missing here??

```
sudo fdisk -l

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00021c38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13058   104887361    7  HPFS/NTFS [vista install]
/dev/sda2           13059       17298    34057800   83  Linux
/dev/sda3           17299       24309    56315857+   7  HPFS/NTFS [xp install]
/dev/sda4           24310       24792     3879697+   5  Extended
/dev/sda5           24310       24792     3879666   82  Linux swap / Solaris
```

relevant section of menu.lst

```
title		Windows Vista (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Windows XP Gamer Edition (loader)
root		(hd0,2)
makeactive
savedefault
chainloader	+1
```

---

### Post by Pumalite on 2007-11-23
Usually Grub puts both Windows in one subsection. They must be fighting for first place. (Both Windows I mean. This is a Windows problem, not a Grub problem). For MultiBoot:
[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

---

### Post by meierfra on 2007-11-23
Windows puts the booting instructions for all the Windows OS onto the first windows partition.

If you use "root (hd0,0)" do you get an  menu to choose between "Vista" and  "Windows XP"?

Did you install XP after Vista's?  Usually it  is best to install Vista after XP.

---

### Post by mahiyar on 2007-11-24
For two windows system on the same disk you have to use "hide", "unhide" command something like this

 title     Microsoft Windows 95
[FONT=Bitstream Vera Sans Mono]     hide      (hd0,1)[/FONT]
[FONT=Bitstream Vera Sans Mono]     unhide    (hd0,0)
[/FONT]root      (hd0,0)
                                                                            savedefault
                                        makeactive
                                        chainloader +1

                                        title      Microsoft Windows 98SE
[FONT=Bitstream Vera Sans Mono]     unhide     (hd0,1)[/FONT]
[FONT=Bitstream Vera Sans Mono]     hide       (hd0,0)
                                              [/FONT]root       (hd0,1)
                                                                            savedefault
                                        makeactive
                                        chainloader +1

---

