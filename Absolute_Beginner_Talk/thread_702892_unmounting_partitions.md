---
title: "unmounting partitions?"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by Vandorin on 2008-02-20
I want to uninstall ubuntu (just not for me, sorry!) and for some reason i can't unmount the partitons i made with gparted, and the usual, "sudo umount /dev/hda4" without the quotes isn't working for me.

---

### Post by robkeys on 2008-02-20
You could just use the Live CD to delete the ubuntu and swap partitions and then re-size your main partition back to fill the void.

Just boot the Live CD, open a terminal and type: ```
sudo gparted
```

---

### Post by Vandorin on 2008-02-20
yea, i just right clicked and pressed "swap off" and i was able to delete it, so now im left with 10 gb of unallocated space.

---

### Post by robkeys on 2008-02-20
So all better, then? I'm confused.

---

### Post by Vandorin on 2008-02-20
well i don't know how to add the unallocated space back to the original drive i took it from. when i right click on it, there are no options to change it.

---

### Post by robkeys on 2008-02-20
If your using gparted on the Live CD then you should be able to right-click the first partition and resize. If it is mounted then you can right-click, select unmount, and then select resize. After that a little window should pop up with a sider. just drag the partition left or right to fill the void.

---

### Post by Vandorin on 2008-02-20
ok, i did that, but now when i start up my computer i get 

Grub Loading Stage 1.5

Grub loading, please wait...
Error 22


and then it just stays like that and does not load up my windows?

(I had dual boot)

---

### Post by robkeys on 2008-02-20
Press ESC when it says its loading GRUB. it should give you the option of loading windows. You may want to run your windows disk, however to get rid of GRUB.

---

### Post by oedha on 2008-02-20
maybe you should try to use gparted :==> [http://gparted.sourceforge.net](http://gparted.sourceforge.net)
or man fdisk and work with sudo fdisk.....(for expert....i always use gparted)

---

### Post by oedha on 2008-02-20
> **Vandorin said:**
> ok, i did that, but now when i start up my computer i get 

Grub Loading Stage 1.5

Grub loading, please wait...
Error 22


and then it just stays like that and does not load up my windows?

(I had dual boot)

for this case...you need XP installation cd.....
bot with xp cd.......choose recovery mode
login by using administrator password then excecute
fixboot
fixmbr
reboot
your windows will be boot again

if you  still want to arrange your partition....i suggest to use gparted :)

---

### Post by asmoore82 on 2008-02-20
> **Vandorin said:**
> ok, i did that, but now when i start up my computer i get 

Grub Loading Stage 1.5

Grub loading, please wait...
Error 22


and then it just stays like that and does not load up my windows?

(I had dual boot)

the nice dual-boot was provided by the linux side of your setup;
to restore the windows-only bootloader;
you need to boot from a windows CD,
enter into a "Recovery Console" "Command Prompt;"
and run this command:```
fixmbr
```

---

### Post by Vandorin on 2008-02-20
> **asmoore82 said:**
> the nice dual-boot was provided by the linux side of your setup;
to restore the windows-only bootloader;
you need to boot from a windows CD,
enter into a "Recovery Console" "Command Prompt;"
and run this command:```
fixmbr
```

when i type in fixmbr i get the error

'fixmbr' is not recognized as an internal or external command operable program or batch file.

---

### Post by ve9gj on 2008-02-20
> **Vandorin said:**
> when i type in fixmbr i get the error

'fixmbr' is not recognized as an internal or external command operable program or batch file.

What version of windows install CD did you boot with? fixmbr should be in Win2k or XP, not sure about Vista.  typing help should list the recovery commands.  Win98 used fdisk /mbr instead.

---

