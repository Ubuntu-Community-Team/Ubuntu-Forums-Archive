---
title: "dual boot how to with acer rescue disc?"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by japephillips on 2008-02-23
when i uninstaller 7.10 because of overheating and shutdown problems, I found my acer rescue disc which has the xp system on it managed, after a few attempts, to overwrite 7.10 on HD and install. However on reboot it showed a grub error and wouldn't boot. So i used ubuntu 7.04 live cd and installed. This suits me as I wnated linux anyway - however i have had many problems with Ubuntu so if it goes haywire again, i would like to have a boot option of xp as i lost too many hours before while installing and trying to setup Ubuntu.
can anyone suggest the best way to do this?
i am not very clever with tech stuff, but stubborn enough to persist if given a lead
so
dual boot with linux as preference, a few seconds to choose xp if necessary (if I cannot get the power management to work on linux i must use xp to save overheating while i tinker with 7.04)
I MUST be able to install xp via the Acer discs and they demand an overwrite of the HD so i am lost as to how to go about this.
and if i have to go back to xp again to save cooking the laptop, how do i reset the mbr or whatever gives the grub error after instaling acer/xp?

---

### Post by forestpixie on 2008-02-23
Are you saying that you have both ubuntu and xp installed but you only have option for ubuntu when you boot? If that's the case can you post output from these 2

```
sudo fdisk -l
```
```
cat /boot/grub/menu.lst
```

I've just looked at your other threads - you are persistent :)

---

### Post by japephillips on 2008-02-23
aye, persistant and very grumpy! i would rather not have to be persistant!

No, What happened was that after overwriting the hard drive with the recovery disc acer provides, and the only way XP can be reloaded, all the setup worked, including keyboard, timezone as usual in a windows setup, but the first boot failed showing a  grub error 17.
so i assume that there is something written in the original ubuntu install i was overwriting, onto the hard drive, so that it still expected Linux. I guess this is master boot record or something. The only thing i could do was reinstall 7.04 over the xp.
Hopefully that makes sense to you now!

---

### Post by bigken on 2008-02-23
you could try formating the hdd 1st with gparted using your live ubuntu cd or download the gparted live cd then use your restore cd to install windows then linux afterwards

---

### Post by bigken on 2008-02-23
also if you could borrow a xp cd you could use the repair console 
and type 

fixmbr
fixboot 
exit

---

### Post by forestpixie on 2008-02-23
> ..the Acer discs and they demand an overwrite of the HDif the recovery cd is insisting on using the whole drive (never used one so can't comment) let it do it

then use the gparted on the buntu cd to make a partition for buntu to go on - then you should be able to dual boot

if it won't dual boot afterwards but you can get into ubuntu you'll be able to edit grub to get win on there

it might be worth getting a copy of supergrub and gparted, about 60 MB together if you're using dialup which I think you are

[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)
[http://gparted-livecd.tuxfamily.org/download.php](http://gparted-livecd.tuxfamily.org/download.php)

---

### Post by japephillips on 2008-02-23
I cannot understand how 'grub' is left on the hdd at all after a complete overwrite. It shouldn't even be an issue. How does one alter the MBR if that is where it sits, etc ... far too much for me to contemplate as a newbie, especially as acer award combination bios on laptop is very limited in controls.
Thus I have to try these 'round about' methods for something simple.
However, can't see a result in anything suggetsed so far folks!
If I do as Forestpixie suggests I will have the original problem,  - an overwritten Hd with no Linux, and no access at first boot to XP or anything else because of the 'grub 17 error'
Even if I borrow an XP disc
and somehow get the partitions right
wouldn't that grub error still occur?

---

### Post by forestpixie on 2008-02-23
as I said before I've no idea how recovery discs work, I've always had a 'proper' disc as it where, but thinking about it if the recovery disc doesn't actually reformat when it does it's thing grub will perhaps still be there - thus you get the grub error

so 

if you can partition the disc before you start the recovery with a ntfs partition for xp and the ext3 partitions ready for buntu - then the recovery disc - I assume - will only know about the ntfs partition that's there and will ignore the ext3, 

once you're sure that xp is ok carry on with the ubuntu install to the partitions you've already made

---

### Post by japephillips on 2008-02-23
ext3 is a special linux type format eh? i have some googling to do obviously
i think i follow your logic
still need a dual boot option though from grub or whatever starts the thing working
more reading before i do it

---

### Post by Duck2006 on 2008-02-23
You can burn a super grub + gparted + puppy linux disk.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by japephillips on 2008-02-24
thanks ducky, but a 50 meg download is about six hours and a likelihood of failure along the way. i have now got the supergrub which will give me something to play with, and gparted is somewhere on the 7.10 disc if i understood forestpixie. dunno how to Livecd it but might try that
all i wanted was to edit the mbr or uninstall ubuntu in such a way it left a clean mbr (took me a week to find out what a mbr is and what the F*** was going on, this is soooo tedious)
looks like another day or two will be needed to figure this out, sigh
but thanks anyway, all of you

---

