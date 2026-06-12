---
title: "Request: A Tutorial On Multibooting Linuxes."
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by brjoon1021 on 2006-08-30
There are and are anticipated to be a lot of converts from Windows and maybe even Mac. I am a Windows user trying to make the switch. I am trying to settle on a distribution by multibooting. Unfortunately, I have found that there is not one really good tutorial that I can find on the web to this end. I have  printed several, they are all lacking in one way or another. A good tutorial would be really helpful and cut down on the posts in the in the installation section of these forums and others.

Perhaps someone here would write one?

From trying to install eight distributions over the last 5 days or so, I know what we converts need to have covered. First, lets assume that Windows is on the Hard Drive first  and, because Ubuntu is the best distro, it will serve as the first Linux installed after windows and we boot with GRUB.

This was my case and it was after this that the torture began. THE NEXT Linux is where the problems start, in other words.

The next Linux will, in my experience, overwrite the bootloader of Ubuntu 2/3 of the time. Much of the other third is taken up by a lame “install bootloader in partition” option that does not result in a bootable new distrubution either, but it at least does not torch the Ubuntu bootloader. For reasons I can't imagine Mepis and SUSE worked OK and their bootloaders were picked up by Ubuntu's GRUB  with a simple "sudo update-grub' from an Ubuntu console. Four other distros did not boot with Ubuntu's GRUB even though I chose the same option in their bootloaders on install. I know that "chainloading" is involved from here but not much else... Another distro overwrote Ubuntu's GRUB with its Lilo without even asking! Argh..

The issues to be covered in a tips sheet or tutorial are:

1.How to get the original bootloader back and how to make both the original distro and the new distro bootable by it. This probably varies for Lilo and GRUB - an important point to cover.
2.This entails: how to get TO GRUB or Lilo of original distro after it has been overwritten and is now not booting. Of course, what to do with the original distro's GRUB or Lilo file once the appropriate file has been located (Lilo or GRUB text files) is also essential Remember, the following means nothing to us, it may as well be cut and pasted from the Rosetta Stone (actually from a post in this case):
 
“timeout 10
color black/cyan yellow/cyan
shade 1
viewport 3 2 77 26
splashimage (hd0,1)/boot/grub/mdv-grub_splash.xpm.gz
default 0

title WindowsXP
root (hd0,0)
chainloader +1

title Linux
kernel (hd0,1)/boot/vmlinuz-i686-up-4GB root=/dev/hda2 ro splash=silent vga=791
initrd (hd0,1)/boot/initrd-i686-up-4GB.img

title MiniMe93
kernel (hd0,6)/boot/vmlinuz-i686-up-4GB root=/dev/hda7 ro splash=silent vga=791
initrd (hd0,6)/boot/initrd-i686-up-4GB.img

title Vector
kernel (hd0,7)/boot/vmlinuz root=/dev/hda8 ro vga=791

title Zenwalk
kernel (hd0,8)/boot/vmlinuz-2.6.17.6 root=/dev/hda9 ro vga=791

title Suse
kernel (hd0,9)/boot/vmlinuz root=/dev/hda10 ro vga=791
initrd (hd0,9)/boot/initrd

title Mepis
kernel (hd0,10)/boot/vmlinuz-2.6.15-26-686 root=/dev/hda11 ro nomce quiet vga=791

title Etch
root  (hd0,11)
kernel /boot/vmlinuz-2.6.16-2-686 root=/dev/hda12 ro vga=791
initrd /boot/initrd.img-2.6.16-2-686
savedefault[/color][/color]"     


----------- . Yet, we new converts have to figure out where to find this info, which lines are useful and how to put them into the config files of an OS that won't even boot at this point.        **** scenario: I have just had a Ubuntu overwrite PCLinuxOS' Lilo, now, PCLInuxOS won't boot but Ubuntu and Windows will boot by Ubuntu's GRUB. How do I add PCLInuxOS boot info to Ubuntu's GRUB now that it(PCLinixOS) won't boot ? Or, If I decide that I like PCLInuxOS' Lilo, how do I add Ubuntu to it once I have wiped out Ubuntu's GRUB with "redo-lilo"? This must be what the inner rings of hell feel like. I reinstalled distros at least a dozen times and could not succesfully get out of the treadmill.  Obviously, I need to fix the PCLinuxOS Lilo, but I don't know how to get to it, PCLinuxOS won't boot and even if it does I have no idea how to add all of the lines above to PCLinuxOS' Lilo so that Ubuntu will boot. I would need to do so because “redo-Lilo” will destroy the Ubuntu's bootloader. I was stuck in this cycle all weekend long. It was awful. I will bet that almost all of the converts from Windows or Mac would be in the same boat as me. ***************   THIS SCENARIO IS NOT GIVEN FOR SYMPATHY OR TO COMPLAIN BUT TO POINT OUT WHERE THE PROBLEMS FOR NEWBIES LIE. I DO want to learn but I don't have hours upon hours to read scattered tips all over the major forums and websites. No one should have to. I did search many forums and found tricks to get into the config files of unbootable distros with a liveCD, how to "redo-lilo" , how to 'sudo update-grub'. But, it was too much time, the information was too scattered and I am certain that anyone I know trying out Linux would get into the same mess or worse if they were to multiboot; most of them just use Linux as  live CD.... I eventually got Windows, Ubuntu, PCLinuxOS, Mepis and SUSE to boot. ANYTHING added after that really borked Ubuntu (something about superblock: "--rebuild-sb" every time Ubuntu would stall its boot). I ended up deleting all of the partitions except windows and PCLInuxOS and making 15 even sized partitions. where I will start again when I feel safe to do so.

So, How about it... someone throw us a bone please. A good tutorial will find its way all over the internet. Think of it as your contribution to getting people away from the windows platform. The best I have seen so far are at BrunoLinux and Distrowatch but they both skip major steps. They will say, "now just add:  some lines of the what-looks-like-gibberish-above to the Lilo or GRUB" then, "run Lilo or GRUB..." Well, we do not even know where lines 2 and 3 of the following can even be found:

"Title Linux
kernel (hd0,1)/boot/vmlinuz-i686-up-4GB root=/dev/hda2 ro splash=silent vga=791
initrd (hd0,1)/boot/initrd-i686-up-4GB.img" 

Knowing what these lines mean, how to find them in a un-bootable distro's configuration files seems to be essential for multibooting because nothing seems to go as planned.

Thanks for your patient reading of this long post  (If someone writes such a tutorial, please delete this post, it is only a request for a tutorial)

B.

---

### Post by bodhi.zazen on 2006-08-30
I would be willing to write one.

Do you need more then this? If so what?
[http://www.linuxjournal.com/article/4622](http://www.linuxjournal.com/article/4622)

Some of your problem is not that grub is over-written but that /boot/grub/menu.lst is over-written.

There are several solutions, save a back up of menu.lst, a /boot partition, or editing menu.lst manually.

> timeout 10
color black/cyan yellow/cyan
shade 1
viewport 3 2 77 26
splashimage (hd0,1)/boot/grub/mdv-grub_splash.xpm.gz
default 0

title WindowsXP
root (hd0,0)
chainloader +1

title Linux
kernel (hd0,1)/boot/vmlinuz-i686-up-4GB root=/dev/hda2 ro splash=silent vga=791
initrd (hd0,1)/boot/initrd-i686-up-4GB.img

BRIEF summary of what this means:

timeout = # seconds to wait to boot default OS
color= color of grub menu
splash image= picture during boot
default=0. This is the default OS. Numbering starts with 0 so 0 boots the first OS on the list. 1 boots the second ....
root= This is the partition to boot. Grub starts with 0.
 Linux hda1 = GRUB (hd0,0)
 Linux hda4= GRUB (hd0,3)
 Linux hdb1= GRUB (hd1,0)
kernel kernel to boot AKA "vmlinuz-x.y.z"
ro= mount kernel read only. This is default.
splash=quiet= less messages during boot. Enable this to see boot errors.
vga= default screen resolution.
initrd = Loads to RAM to mount devices assisting the kernel to boot. AKA "initrd-x.y.z". Not always needed.
Chainloader- Passes booting process on to the partion to boot. Used primarily with windows and BSD, can be used with Linux.



Otherwise give me some time.

---

### Post by whizbaby on 2006-08-30
Or simply copy your win-stuff above this entry in menu.lst:

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below


I think by adjusting the menu.lst's of your different systems you could manage it that only stuff related to that system is changed (yes, means moving to grub with oslinuxpc-thingy (dunnodat))

Seems quite easy, huh?

---

### Post by brjoon1021 on 2006-08-30
Thanks for responding. I am at work so I will have to wait until I get home to take a look at that Linux Journal article, but I think that I have it printed out. It is a bit dense, I think, for people new to Linux that are still getting used to Home, Root, /dev/, etc...

to bodhi.zazen,
 if you would be willing to write something that a sharp 10 year old could follow, yeah sure, pleeeaaaase write it. It is the skipped (assumed-prior-knowlege-steps that are left out of some of the tips sheets) What would be incredibly helpful would be something that reads or works like a flow chart, "multibooting for idiots":

Step one: install second Linux: If Second linux install over-writes MBR you have two choices:

A. you want your old bootloader back, do this...

B. you are fine with the new bootloader, but your previous distro won't boot because its Lilo or GRUB was torched, do this... especially, tips like, "drop your Knoppix/Mepis, etc... livecd in, do this... to get into the unbootable OS's bootloader files... do this to the files.. they will need to be copied to here... like this... the lines with "vmlinuz or... are the ones you will need..."
 
C. You tried to install the second distro's bootloader in its root partition, you made that selection in the installation tool, but it did not seem to work, the OS won't boot, do this... find the lines "x,y,z" in the config file of... copy write down or copy these lines because you will have to add them, just so to...
-- There are actually only a few eventualities for every possible move. You know, second distro behaves nicely (keep it or replace with first disto's) or it over-writes the MBR. IF it over-wrote, then you have two choices...
that kind of thing.

Also, which one, Lilo or GRUB is better or easier for a project like this, especially, which one do you think is better for a multiboot project that will span over more than one hard disk?

I noticed that PCLinuxOS has in its control center the ability to add a distro to its bootloader. It asks for name and has a space to put "image" in. This may be a ton of handholding, I just don't know what the "image" is. If it sounds like a really easy way to go, I will use PCLinuxOS GRUB and add distros to it once I figure out what it is asking for.

Thanks,

B

---

### Post by bodhi.zazen on 2006-08-30
As you can see GRUB is dense. I have very little experience with lilo.

I can only tell you how I do it, and I will freely admit I am no GRUB expert. THIS IS A HACK AT BEST.

Some would use a /boot partition. With multiple OS I do not like this as much because I can not always recall which vmlinux-x.y.z goes with each distro.

Make a "data" partition somewhere and save a copy of /boot/grub/menu.lst.

When you install a new distro it will give you a choice- Save grub to to your root partition (Not the MBR). If you are given a lilo option, just set up to up your root partition. This should give you a /boot directory within your new install partition with vmlinux.x.y.z and, if needed, initrd.x.y.z as well.

Whichever OS you used to set-up the MBR is "master". Update that /bot/grub/menu.lst.

Example:

1. Say you have 2 HD, first with windows, 2nd with multiple 15 GB partitions for multiple Linux.

2. Install windows on the first disk.

3. Install Ubuntu on first partition of second disk. When you install Ubuntu set up GRUB on BOTH the Ubuntu partition and then the MBR (use the back arrows). You should now be able to boot either Windows or Ubuntu.

4. Now install Zenwalk in to second drive, second partition. Zenwalk uses lilo. Set lilo for Zenwalk partition, not MBR. Boot Ubuntu -> Mount Zenwalk root partition -> look in /Zenwalk_root/boot for name of vmlinuz and initrd. Edit (add) an entry in UBUNTU /boot/grub/menu.lst for Zenwalk.
```
root (hd1,1)
kernel=/boot/vmlinuz-x.y.z root=/dev/hdb2 ro splash=silent vga=791
initrd=/boot/initrd-x.y.z.img
```
When you re-boot you will be able to boot to windows, Ubuntu, Zenwalk.

Keep going.

If a distro overwrites your MRB, no worries.

1. Make a grub floppy -> Boot to floppy -> Boot Ubuntu
```
grub> root(hd1,0)
grub> kernel=/boot/ubuntu_kernel (Hint type vmlinuz and use tab completion)
grub> initrd=/boot/ubuntu_initrd
grub> boot
```
grub> indicates the grub prompt (do not type)

2. Add your new distro to Ubuntu /boot/grub/menu.lst as above (like Zenwalk).

3. Re-install GRUB to the MBR from ubuntu.
In a terminal type;
```
sudo grub
```
At the GRUB prompt type:
```
grub> root (hd1,0) # Ubuntu root partition in grub speak
grub> setup (hd0)
grub> quit
```

4. Now you should be able to boot windows, ubuntu, zenwalk, and bad distro that trashed you MBR.

You will need to edit your Ubuntu /boot/grub/menu.lst every time you update a kernel. Some distros create a symbolic link to "vmlinux" to vmlinuz.x.y.z. These disro's use "vmlinuz" in the grub menu rather then "vmlinuz.x.y.z".

Last:
```
cp /boot/grub/menu.lst /data_partition/backup_directory/grub
```

Do not fear the command line, once you learn it you will be at home in any Linux distro and not dependent on a GUI for configuration.

---

### Post by brjoon1021 on 2006-08-31
Yeah, I think that you are right about the command line. Do you know of a tight command line tutorial or list, or however someone goes from not knowing to being pretty proficient with the command line?

Thanks for your help!

B.

---

### Post by bodhi.zazen on 2006-08-31
> **brjoon1021 said:**
> Yeah, I think that you are right about the command line. Do you know of a tight command line tutorial or list, or however someone goes from not knowing to being pretty proficient with the command line?

Thanks for your help!

B.
[http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

