---
title: "Running Ubuntu and Windows"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by hotbrainz on 2006-05-12
I am quite new to Ubuntu. I would very much like to give it a proper tryout. Is there a way of installing Ubuntu with Windows. I mean installing in seperate drives and thing...
i dont wanna use the live version because i want to use Ubuntu in a full fledged manner for a month or so before i make a switch from windows to Ubuntu, hopefully !

Please provide some thoughts on this..

Thanks in advance

---

### Post by glotz on 2006-05-12
Good idea, here's one guide [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by SkyNet2029 on 2006-05-12
Sadly, it is possible to keep windows alive whilst having Ubuntu installed on your machine as well. When going through the setup process, one of the final stages is the installationi of a boot manager program, such as Lilo or Grub. If all goes well, (it usually does) your windows partition(s), and any other OS's you have installed already will be detected by the Debian-Installer. At this point, you will be given a choice as to which boot loader you would prefer to be installed, or an option to not install a boot-loader. 

A word of caution here, though; I have had Grub fail miserably on a dual-boot Xp/Ubuntu setup, and have also had Lilo do the same, thanks to not having paid attention to my drive jumper settings. Once I had that figured out all was good again, but that's dependent on your particular setup, the easiest being two separate drives. I currently use Grub as a personal choice, even though Windows is no longer on my computer.

That having been said, the documentation on dual-boot and even Tri-boot setups is fairly straight-forward, although one of the better sites for this IMHO is this one : [http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")  .

---

### Post by mostwanted on 2006-05-12
The quick and painless way:

Back up your files, reinstall Windows, but make sure you don't fill up your drives with Windows partitions e.g. leave some free space for Ubuntu.

Then install Ubuntu. There's is an option to install it to the largest block of free space, but if you're comfortable with it, you can also edit the partition table yourself (not as hard as it sounds). Your Windows partition will be automatically detected and set up with the bootloader that Ubuntu uses.

Then you have yourself a dual-boot system! :)

---

### Post by hotbrainz on 2006-05-12
thanks a ton. I will chew on that page in a bit.

Cheers

---

### Post by easyease on 2006-05-12
my advice is create four seperate partitions. one for windows and software that will only work on windows, one for ubuntu as a root filesystem, one nice big partition formated to fat32 for all the nice stuff you will be downloading( you will be able to access these files from both windows and ubuntu later), and finally a logical swap partition.  it works for me. how big is your hd?

---

