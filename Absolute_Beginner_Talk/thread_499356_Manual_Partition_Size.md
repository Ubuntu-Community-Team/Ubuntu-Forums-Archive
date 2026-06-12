---
title: "Manual Partition Size"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by digital006 on 2007-07-12
I'm trying to get round the Error 18 problem by manually sorting partitions out, what size and type partitions do I need when I go to set them up manually in the install wizard?

At first I tried to create a ext3 and swap but it said I need to set a home one how do I do this? How do I tell ubuntu what each partition should do e.g. Partition 1 is root, Partition 2 is home, Partition 3 is swap?

Also bear in mind that once installed I can't actually get into Ubuntu because of error 18 so altering partitions isn't possible.

Cheers
Mike

---

### Post by Inxsible on 2007-07-12
> **digital006 said:**
> I'm trying to get round the Error 18 problem by manually sorting partitions out, what size and type partitions do I need when I go to set them up manually in the install wizard?

At first I tried to create a ext3 and swap but it said I need to set a home one how do I do this? How do I tell ubuntu what each partition should do e.g. Partition 1 is root, Partition 2 is home, Partition 3 is swap?

Also bear in mind that once installed I can't actually get into Ubuntu because of error 18 so altering partitions isn't possible.

Cheers
Mike
You can tell ubuntu what each partition should do by giving those partitions a mount point. if the mount point is / then the entire OS will be installed in that partition. A mount point of /home will install the home folder in that partition. Selecting swap as mount point will create a swap drive.

---

### Post by bodhi.zazen on 2007-07-12
You solve an error 18 by making a boot partition.

So ... Set up your partitions before you install Ubuntu. (you can do this with the Ubuntu CD using gparted or using the gparted Live CD)

You need :

/boot

/swap

/

1. boot. Make this ext2 size = 512 Mb . Make the boot partition the first partition on the drive.

2. Swap . Size = RAM X2, max 1 Gb, or if you have a laptop **AND** RAM > 1 Gb **AND** you want to use hibernation, swap = RAM

3. / = root partition. Minimal size = 5 Gb, but 15-20 would be nice.

Then run the ubuntu installer, choose manual partitioning,  select each partition and mount all those partitions at /boot /swap and / respectively

> Error 18

Error 18: Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB on others.). In more practical terms this means the BIOS is unable to start executing the kernel because the kernel is not located within the block it can access at boot up time.

This can be circumvented by creating a boot partition at the beginning of the disk that is completely within the first 1023 cylinders of the harddrive. This partition will contain the kernel. 

If you set the /boot partition at the beginning of the drive Ubuntu will do the rest automatically.

If you dual boot windows , keep windows as the second partition.

Location of /swap and / do not matter too much.

---

### Post by digital006 on 2007-07-12
Thanks bodhi

Just a few more questions:

The first partition is ext2 with the flag set to boot

What type is the second and third drive (so far the second is linux-swap) and what type of flags should I use.

When this is setup, what options do I choose when it comes to installing it when partitioning, if its manual where do I go from there?

Cheers

---

### Post by digital006 on 2007-07-12
I just tried creating just the boot partition and reinstalled, it still didn't work.

That was my 3rd install and probably my last until I can find a way of actually booting into the thing.

---

### Post by digital006 on 2007-07-12
BUMP, still need help

---

### Post by bodhi.zazen on 2007-07-12
The boot flags are not used by Linux so you do not need to set or worry about them.

1. As long as the ext2 /boot partition is first, the order of the other partitions does not matter (but you will need to understand how Linux and Grub number partitions to set the correct partitions in the commands below).

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)


2. OK, now install Ubuntu. DO NOT mount the /boot partition (we will set that manually) Install grub into the / (root) ubuntu partition NOT THE MASTER BOOT PARTITION AND NOT THE /boot PARTITION.

Again you do not need to mount the boot partition this time (we are going to do a manual setup since it seems the automatic setup failed).


3. OK now, still on the live cd, enter this in the terminal,

```
sudo grub
```

You will get a grub prompt :

grub >

At the grub prompt, type (this sets up the boot partition and MBR):

```
root (hd0,0)
setup (hd0,0)
setup (hd0)
```

quit grub (type quit)


4. Still on the live CD, mount and edit boot.lst (on the boot partition):

```
sudo mount /dev/hda1 /mnt
sudo gedit /mnt/boot/grub/menu.lst
```

Note : that last command may be sudo gedit /mnt/grub/menu.lst (I am not sure how grub will set up the partition but I'd bet on /mnt/boot/grub/menu.lst)

Now edit your entries for Ubuntu to :

> Title Ubuntu ... # do not edit this line
root (0,x) # do not edit this line, I do not know your partitions scheme, thus the x
chainloader +1
boot

You may remove any other entries you have here for Ubuntu (you will not need them)


5. Remove (comment out by adding a "#" at the beginning without the " ") and reference to hda1 in /etc/fstab (you should not have one, but just checking it did not get set automatically)

```
sudo umount /mnt
sudo mount /dev/hdax /mnt # hdax = the ubuntu root partition
sudo gedit /mnt/etc/fstab
```

Add a # in the front of any line with /dev/hda1

Like this :> #/dev/hda1 ......


6. Now re-boot (and obviously remove the live CD). You will see two grub screens, select Ubuntu both times ;)

If it is working you can boot to Ubuntu and edit /boot/grub/menu.lst and change the settings so it directly boots ubuntu without showing the second screen.

For Grub options see here : [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm) (see "hidden menu", setting the default OS, and reducing the timeout. I suggest a time out of 2 seconds in case you need it to select the recovery mode or a different kernel).

---

### Post by digital006 on 2007-07-13
Thanks again for the information.

So the first partition for /boot is ext2
the second partition for / is ext3 (from the Partitioning Basics Thread)
the third partition for /swap is ???? (could be linux-swap?)

Also in the terminal commands when referring to hda and hd0 are you assuming that I'm trying to install Ubuntu onto my primary drive? I'm trying to install it to a second hard drive running as slave, so would it be hdb and hd1 instead?

Also when installing using manual partitioning it always says that I can't continue because there is no root partition selected, how do I proceed?

---

### Post by digital006 on 2007-07-13
Ok so I've just created three partitions using gparted:

/dev/hdb1 ext2 (for /boot) 512mb
/dev/hdb2 ext3 (for /) 20gb
/dev/hdb3 linux-swap (for /swap) 2gb

I have 158gb unallocated for /home later

I'm on the prepare disk space screen, I'm selecting Manual.

It's telling me that "No root file system is defined, please correct this from the partitioning menu." Does it mean gparted? If so where? all the partitions *should* be correct. I can't continue without knowing how to set hdb2 as /. I'm getting so fustrated by this, I hope someone can help soon. I'll leave my main computer at this screen until I get help.

---

### Post by digital006 on 2007-07-13
Problem solved I think. Still need an answer about the hda/hdb hd0/hd1 though
.

---

### Post by digital006 on 2007-07-13
Managed to get up to setup (hd0,0) it throws an error about not being able to mount a drive.

Also when i looked in the menu.lst I didn't have an option for Ubuntu just Linux, I changed where it points to and messed it up so just going to change that now.

---

### Post by bodhi.zazen on 2007-07-13
Yes, sorry about the partitioning confusion.

Primary drive = Linux /dev/hda = GRUB (hd0)

Secondary drive = Linux /dev/hdb = GRUB (hd1)

And on ;)

Glad you got it sorted out, now you are an expert on GRUB and boot partitions :lolflag:

Let me know if you have further questions.

---

### Post by dan171717 on 2007-07-13
are u dual booting if not use the guided install method an use the whole drive 

btw i dual boot and my win partion is hda2 and is a /boot and it all works

---

### Post by digital006 on 2007-07-13
> **bodhi.zazen said:**
> Yes, sorry about the partitioning confusion.

Primary drive = Linux /dev/hda = GRUB (hd0)

Secondary drive = Linux /dev/hdb = GRUB (hd1)

And on ;)

Glad you got it sorted out, now you are an expert on GRUB and boot partitions :lolflag:

Let me know if you have further questions.

Hmm well it's not fully working, so where you specified hd0 i should use hd1? 

Also did you see my post about not getting setup (hd0,0)?

---

### Post by digital006 on 2007-07-13
AAAAAARRRRRRGGGGGGGHHHHHH I reinstalled after my last post and managed to follow the instructions up to the fstab bit when I used gedit it brought up a blank file. I restarted anyway and now I get Error 16!

WTF!!! This is my 5th install and I'm getting tired fo reinstalling everything just for it to mess up.

---

### Post by bodhi.zazen on 2007-07-13
> **dan171717 said:**
> are u dual booting if not use the guided install method an use the whole drive 

btw i dual boot and my win partion is hda2 and is a /boot and it all works

I know it is hard to come into the middle of a thread and your input is appreciated.

Basically:[list=number][*] digital006's BIOS will not boot the ubuntu partition (grub error 18) and...[*] automatic installation of a /boot failed.[/list]

So I am trying to walk him through a manual set up ;)

> **digital006 said:**
> Hmm well it's not fully working, so where you specified hd0 i should use hd1? 

Also did you see my post about not getting setup (hd0,0)?

Yep. read and understand the partitions schemes of both Linux and GRUB

Then follow my guide and plug in the appropriate partitions for each step.

If you do not understand Linux partitioning (/dev/hda ; /dev/hdb) and grub (hd0 ; hd0,1) partitioning terminology ... STOP READ ASK FIRST, otherwise you may wipe the wrong partition.

If you did not try to set up /boot automatically because you did not understand the terminology, repeat an attempt at automatic installation/configuration as dan171717 suggests.

---

### Post by digital006 on 2007-07-13
My setup

1st HDD 200g with Windows XP installed (PRIMARY)
2nd HDD 200g (SLAVE)

2nd HDD is set up as the following:

1st Partition = /boot (ext2)
2nd Partition = / (ext3)
3rd Partition = swap (linux-swap)

On install manual partition is fine. It then goes on to install. When I get the bhodi's instructions on what syntax to enter I changed it to the following:

sudo grub

root (hd1,0)
setup (hd1,0)
setup (hd1,0)

sudo mount /dev/hdb1 /mnt
sudo gedit /mnt/grub/menu.lst (/boot didn't work)

Next i found the following:

Title Ubuntu ... # do not edit this line
root (0,x) # do not edit this line, I do not know your partitions scheme, thus the x
chainloader +1
boot

Added the correct chainloader and boot, however the "x" might be pointing to the wrong drive. This entry had other stuff after but left it.

sudo umount /mnt
sudo mount /dev/hdb1 /mnt
sudo gedit /mnt/etc/fstab (this brought up an emty file in gedit)

Restarted to see if it would work and I get error 16 in grub after stage 1.5

I'm having real issues understanding where abouts I need to point certain partitions.

---

