---
title: "More than one linux ?"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by nick24 on 2007-02-27
Hi there 

I already have Mandriva 2007 installed on my secondary hard drive (/hdb). Now I am trying to install Ubuntu in the same HD. Question is do I have to reinstall Grub everytime I install a new linux distro?  I heard Grub will rewrite itself everytime and that will lead to a serious problem eventually. By the way I intentionally installed Grub on /hdb to keep Windows and my precious Linux separate. And this brings my second question. Is there any way to go around the problem of loading Windows from /hdb (NTLDR is not present in /hdb, it is instead in /hda, without going to BIOS and changing the priorities of HD. Because when I try to load Windows from /hdb using Grub it tells me NTLDR is missing. Thanking you in advane.

---

### Post by waqas_butt0071 on 2007-02-27
if u install new GRUB it will detect and pick all your old OS installed.

---

### Post by ieee488 on 2007-02-27
I once had Ubuntu 5.10, Ubuntu 6.06, OpenSUSE 10.1, and Windows 2000 booting on the same PC. You don't have re-install Grub, but then I have Grub in MBR. What you are doing is different.

---

### Post by milton1 on 2007-02-27
You do not need to reinstall grub. When you install ubuntu, skip the step to install grub. The installer will yell at you a bit, but it will eventually let you skip the step. You can then manually edit /boot/grub/menu.list on your existing distro to include an entry for the new ubuntu install.

---

### Post by nick24 on 2007-02-27
Thankyou very much people. 

I will skip the step then. What about my second question ? any takers :)  Thanking you in advance

---

### Post by actuary286 on 2007-02-27
To boot Windows without going into the BIOS you can install GRUB on the MBR (master boot record) of hda. It will detect all your operating systems and should boot Windows correctly since the NTLDR is available.

If you want to edit the default boot order or any of the menu entries editing /boot/grub/menu.list is the way to go, but make sure to backup menu.list first!

```
sudo cp /boot/grub/menu.list /boot/grub/menu.list-backup
```

This will let you go back to the original settings in case something breaks.

---

### Post by steve.horsley on 2007-02-27
If you use the alternate installer, it can install GRUB to the Ubuntu root partition instead of to the MBR. To do this, when you get to the bit where it asks where to install the bootloader, if you want it on /dev/hdb3 (for example), tell it (hd1,2). Do not use the linux notation even though the help text says you have choice.

Once you have installed GRUB on the root Ubuntu partition, you have to load chainload that partition from another bootloader. Your original GRUB on the MBR will do, using chainloader +1 just the same as with windows. Other bootloaders (on the MBR) could be used instead, as some people prefer. The advantage of this arrangement is that upgrades to Ubuntu will upgrade the GRUB settings to load the new kernel, but on their own partition without mangling your main boot menu. I do this on my PC, and set the second GRUB to a very short timeout - just enough to catch it and enter recovery mode it I need to.

---

### Post by Bachstelze on 2007-02-27
What I personnally do when I run miltiple Linuxes is create a shared /boot partition to all of them. It's a bit more complicated to setup but it allows to boot all of them directly from the same GRUB, without the need for chainloading.

---

### Post by nick24 on 2007-02-27
Thankyou very much 

It a little over my head but I will try to do that (Steve.horsley) . HymnToLife I like your idea , could you please explain how to do that? or post the link or  something . Thankyou :)

---

### Post by Duck2006 on 2007-02-27
> Is there any way to go around the problem of loading Windows from /hdb (NTLDR is not present in /hdb, it is instead in /hda, without going to BIOS and changing the priorities of HD. Because when I try to load Windows from /hdb using Grub it tells me NTLDR is missing. 

By this you mean that your loading from hdb?

If so your have to edit the menu.lst and add this to it.

sudo gedit /boot/grub/menu.lst

title		Windows NT/2000/XP
root		(hd0,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
chainloader	+1

I thing this is what your after.

---

### Post by Bachstelze on 2007-02-27
nick24, In a nutshell, /boot is where all the files needed for booting go (i.e. grub config, kernel images and such), so if each distro has it's own /boot, you will need to boot each one with it's own GRUB, while you put /boot on a different partition and use it for all of them, the GRUB that launches at startup will have everything it needs to boot any of them.

The difficult part is that you'll have to remember the infos (kernel, root partition, possibly initrd) for each distro and you will need to edit the GRUB config accordingly whenever you install a new one since it will possibly overwrite the old config.

---

### Post by nick24 on 2007-02-27
[QUOTE=Duck2006;2221924]By this you mean that your loading from hdb?

Thats exactly what I am mean. I will backup the menu.list and try it. Thankyou vey much

---

### Post by nick24 on 2007-02-27
hhhmm I get the idea, but thats about it since I am beginner I dont want to mess up with that highspeed stuff. I will keep that for future reference and in the meantime I will ask if I need more help. Thankyou so much

---

### Post by steve.horsley on 2007-02-28
> **HymnToLife said:**
> 
The difficult part is that you'll have to remember the infos (kernel, root partition, possibly initrd) for each distro and you will need to edit the GRUB config accordingly whenever you install a new one since it will possibly overwrite the old config.

That's why I choose to chainload all the Linux's but one. They are all welcome to utterly bollox up their own copy of menu.lst and that won't break anything else. I have a small rescue Linux (Breezy, IIRC) that the MBR grub uses, and I manually edited that to give the options of chainloading the other partitions.

Unfortunately, the Feisty installer is high on acid or something, and ther is no way ths installer can do what's needed. I don't actually want to repartition at all, but the installer won't let me skip reformatting partitions that don't actually even exist! And it thinks sda5 is a primary partition! There's no way I'm clicking Yes on that!

---

