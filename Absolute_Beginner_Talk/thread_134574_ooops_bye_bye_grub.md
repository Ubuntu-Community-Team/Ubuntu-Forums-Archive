---
title: "ooops bye bye grub"
date: 2006-02-22
forum: Absolute Beginner Talk
---

### Post by ninjasmith on 2006-02-22
right whilst trying to piss around with partitioning I seem to have deleted my boot partition.

I was using gparted and tried to format a partition it din't work.  thought I would reboot into windows and see if the partiition was still there.  it was but was unrecognised.  in a moment of madness I deleted it and tried to format from windows. it wouldn't let me format as fat32 so I tried to reboot into linux.

however it now just gives a grub error

screen shows

grub loading please wait.....
error 17

so I think I have screwed up the boot sector.

I also have two windows partitions on here.  from what I can guess I have a few options in increasing order of pain

1) download and burn ubuntu live cd, use this to recreate a boot sector with grub on it, edit so I can reboot ubuntu and windoze
2) reinstall ubuntu and then edit grub to see my windoze partitions so I can dual boot again
3) format whole drive and rebuild everything (won't lose data as its on another partition... but still a bad option

can anyone point me to a guide to do optoin 1)

thanks in advance

---

### Post by Herman on 2006-02-22
Okay, (just me again), here:
[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows")
Those are the official Ubuntu Wiki methods to re-install GRUB, I think they are very good. There is another way with the installer CD, but not so many use it nowadays. See how you go with those ones, one of them should suit you.
:D (Herman)

---

### Post by az on 2006-02-22
[QUOTE=ninjasmith]

1) download and burn ubuntu live cd, use this to recreate a boot sector with grub on it, edit so I can reboot ubuntu and windoze
[/QUOTE]
The install cd is fine.  Just boot into it, go to the second console (CTRL-ALT-F2) chroot into your ubuntu partition and install grub

Example, using hda5:

mkdir /mnt
mount /dev/hda5 /mnt
chroot /mnt
grub-install /dev/hda

---

### Post by ninjasmith on 2006-02-23
righto first of all m laptop cd burner has gone kaput so only have installation cd.

can sucessfuly get to the resuce pont when it gives me a choice of all the partitions I have.  I am farilty sure that linux was on partition 3 but when I try and chose this one I get a cannot access ( or maybe cannot mount ) error.

when I chose partition 2 I get to the next part but then I cannot mount the partition to /mnt.  I tried

/mount /dev/hda2 /mnt


also
/mount /dev/hda3 /mnt
/mount /dev/hda5 /mnt
/mount /dev/hda1 /mnt
/mount /dev/sda3 /mnt
/mount /dev/sda2 /mnt
/mount /dev/sda5 /mnt


nothing works, gives me a no such file or direcotry error (and I know the /mntdir exists as I can cd into it) I am thinking that I might have damaged my linux partition when messing around with it in windows.

anyone got any ideas?

shall I just try and rebuild linux from scratch?  if I do so will I still be able to boot to my two windows partitions?

please help a confused linux noob.....

---

### Post by Iowan on 2006-02-23
Maybe its just a typo, but the command is **mount /dev/hda5 /mnt**...
not **/mount /dev/hda5 /mnt**.

---

### Post by ninjasmith on 2006-02-23
yeah it was just a typo I was typing 

mount /dev.....

---

### Post by az on 2006-02-23
Well, if you are using the rescue option, you are already chrooted into your linux partition.  Just do the grub-install from there.....


I just skip to the CTRL-ALT-F2 because I am impatient....

---

### Post by ninjasmith on 2006-02-23
[QUOTE=azz]Well, if you are using the rescue option, you are already chrooted into your linux partition.  Just do the grub-install from there.....


I just skip to the CTRL-ALT-F2 because I am impatient....[/QUOTE]

hmmm ok I see so you are saying that just typing

grub-install /dev/hda should do it? or should it be grub-install /dev/hdaX

will try tonight when I'm home.  I have a feeling there was some problem with this along the lines of the directory did not exist.  and when I did an ls on the /dev directory I got hundreds of directories but I couldn't see any hda or sda directories

p.s. I think I need to use sda not hda on my machine becuase this was the only way I managed to mount my windows partition previously (maybe its because they are sata drives?)

---

### Post by Jewden on 2006-02-23
I had the same problem some week ago. I have sata disks and reinstalling grub didnt work for me (the ubuntu wiki way)

I solved the problem by installing another ubuntu on another partition. But there has got to be an easier way.

---

### Post by ninjasmith on 2006-02-23
[QUOTE=Jewden]I had the same problem some week ago. I have sata disks and reinstalling grub didnt work for me (the ubuntu wiki way)

I solved the problem by installing another ubuntu on another partition. But there has got to be an easier way.[/QUOTE]

well I am tending to reinstalling as for me it will be easier (i.e. have sucessfully done it once)

did you overwrite the partition that had linux on it previously when you did the reinstall?

anyone else know an easier way?

---

