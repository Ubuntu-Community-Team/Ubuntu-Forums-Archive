---
title: "Creating Apple_bootstrap"
date: 2007-03-19
forum: Apple PPC Users
---

### Post by tryin on 2007-03-19
Hi I'm trying to install Ubuntu on my iMac G5 (Mac OS X 10.4.8 ) but I'm stucked in the Apple_Bootstrap part

I've tried putting on Terminal 
sudo fdisk -l
sudo mac-fdisk -l
without the sudo...
putting first "mount" and then "sudo fdisk -l"
etc...
etc...


All I get it's this:

```
fdisk: illegal option -- l
usage: fdisk [-ieu] [-f mbrboot] [-c cyl -h head -s sect] [-S size] [-r] [-a style] disk
        -i: initialize disk with new MBR
        -u: update MBR code, preserve partition table
        -e: edit MBRs on disk interactively
        -f: specify non-standard MBR template
        -chs: specify disk geometry
        -S: specify disk size
        -r: read partition specs from stdin (implies -i)
        -a: auto-partition with the given style
        -d: dump partition table
        -y: don't ask any questions
        -t: test if disk is partitioned
`disk' is of the form /dev/rdisk0.
auto-partition styles:
  boothfs     8Mb boot plus HFS+ root partition (default)
  bootufs     8Mb boot plus UFS root partition
  hfs         Entire disk as one HFS+ partition
  ufs         Entire disk as one UFS partition
  dos         Entire disk as one DOS partition
  raid        Entire disk as one 0xAC partition
```


So if someone can show me how to use fdisk for dummies it will be great

---

### Post by grazie on 2007-03-19
Looks like you're trying to work from OS X? If you want to install Ubuntu, people generally work from Ubuntu (Desktop or Alternate CDs).

You really need to give a lot more info about what you are doing in trying to achieve your goal for someone to offer advice. If you want partition information on a Mac using Linux (for most PPC distros) use
```
$ sudo mac-fdisk -l
```
The gui application gparted can also be used if it's installed. Only use fdisk or cfdisk on a Mac from Linux if you need to work with MBR (DOS) disks. Gparted handles both types. If you want to mount a device
```
$ sudo mount <device> <mount point>
```
See the manual (man mount) for further information.

---

### Post by tryin on 2007-03-19
I tried "sudo fdisk -l" from mac os x and livecd ubuntu and in both cases it appeared the same thing (the code before).I also tried cfdisk but it told me that my disk couldnt be written only read.

And as for gparted,first it gave me an error about my root files type because it couldnt see what type was my apple map partition,consequence, I had to manually created the swap and the ext3 linux partition.


Thanks for your answer

---

