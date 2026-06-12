---
title: "GRUB _ blinking cursor (doesn't boot)"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by imnotryan on 2006-10-24
Sorry if this is in the wrong section, etc.  

I just installed ubuntu on a computer.
To the best of my knowledge, I had it reformat the HD, and it should not contain any partitions for any other OS's.

It worked successfully for about 1 week.  Booted fine.  Networked with my other computers fine.  Everything was A OK.  Perfect.

Today I started it, first and only thing that comes up is "GRUB _" with the cursor blinking.  It doesn't respond to any keyboard commands, you cannot type anything or hit enter.  The computer is completely unresponsive.

I have tried to research this myself for hours now... But all I've gotten is confused.  **Any ideas about why this happened, or what I can do to fix it?**

It does boot from the ubuntu CD and I assume it will allow me to reinstall...  But I just spent a week backing up and transfering files, if I have to do all that over, and could fairly expect this error to happen again, I may need to rethink using linux. :(

---

### Post by jorn on 2006-10-24
Welcome!
I havn't experienced that before, and you have of corse rebootet to see if it's the same. Have you done any changes before this occurred?
Maybe a restore of yor bootloader would do it? 
[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)
Edit: Be very careful with part 4. I don't know if there is an easier way to restore grub.

---

### Post by Blisster on 2006-10-24
I had the same problem, turned out it was a BIOS setting concerning auto-detect and the HDD. I'm sorry I can't be more specific, but I ran into it while installing gentoo on a system, its a GRUB issue and not an ubuntu issue. Something about auto-select or something IIRC. Mess with the settings and see if htat doesn't help.

Sorry I can't be more specific, but hopefully that will be enough to get you on the right track.

---

### Post by anaconda on 2006-10-24
Can you boot to your system (in hd) with liveCD?

if not, then if you boot to LiveCD can you access your hd partitions eg. read data?

If you can then you just need to reinstall grub.

---

### Post by imnotryan on 2006-10-24
The computer boots using LiveCD...

But I cannot access either of my CD drives or the HD using the LiveCD/installation screen ubuntu.  It says it is unable to mount them...

I tried to reinstall hoping it would have an option, as does windows, to overwrite OS files but leave my other data intact.  But Ubuntu wants to reformat my hard drive or split off another partition...

Does this look like a hardware or software failure?

---

### Post by bulldog on 2006-10-24
Just install GRUB again.

If you want to acces your hdd you have to mount them.
```
sudo mkdir /mnt/ubuntu
```
For the mountfolder

```
sudo mount dev/??? /mnt/ubuntu
```
To mount your hdd,??? stands for your partition which you can find with
```
sudo fdisk -l
``` l as in like.

To install GRUB from live session don't mount your partition just boot into the live cd and type the following in your terminal.

When you get to the desktop open a terminal and enter. 


```
sudo grub
```


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands


```
find /boot/grub/stage1
```

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)


```
root (hd?,?)
```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr


```
setup (hd0)
```

Finally exit the grub shell


```
quit
```

That is it. Grub will be installed to the mbr.

---

### Post by jkvv_1973 on 2006-10-24
can the SUPER GRUB DISC help this problem???:evil:

---

