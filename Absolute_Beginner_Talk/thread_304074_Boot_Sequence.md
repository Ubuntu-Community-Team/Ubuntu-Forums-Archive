---
title: "Boot Sequence"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by djlyx on 2006-11-21
Greetings,

I have two hard drives hooked up to my pc.

One has win xp, the other xubuntu.

Grub automatically put xubuntu as the first os on the boot up screen and windows as last.

Does anyone know how I could change the sequence so that I can put windows first and move xubuntu to second?

Btw, I love xubuntu but other people use my computer and they use windows so I have to put it first on the boot sequence.

Thanks

---

### Post by divague on 2006-11-21
Just edit /boot/grub/menu.lst at the end of the file you'll see the list

---

### Post by Leed on 2006-11-21
Hi djlyx

I had the same problem, be warned when changing the menu.lst file, do one thing wrong and grub won't boot anymore. 

You can edit the menu.lst file with
```
gksu gedit /boot/grub/menu.lst
```

Just copy the bottom Entry from Windows to the top of the List of options, [COLOR="Red"]do not remove the bottom entry of Windows, just to be safe[/COLOR]
like here:
```
## ## End Default Options ##

title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

title		Ubuntu Edgy Eft 6.10
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/evms/hda8 ro splash
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,7)

blablabla...
```

Often Programs do an automatic update on grub (or the command "update-grub"). The problem here is that it rewrites a specific part in grub. In doing this, your top entry for Windows will be removed, leaving only the ubuntu selection options in Grub, that is why you should leave the Windows entry at the bottom. 

If you feel safe with it, you can do as I did by simply removing the Lines beginning with "###" which are placed for the automatic Grub updates, that way ubuntu will no longer be allowed to overwrite your settings... however in case of an update, it will append it automatic "junk" at the bottom of the file... in that case just delete it.... and check on your settings again before rebooting ;)

---

### Post by maximouse on 2006-11-21
If you want the machine to boot windows as a default, you can edit the menu.lst file and change "default 0" to the number your windows entry is. Note that the list starts from 0 not 1 so if you have 5 entries, use "default 4". But this method does also require you to change it to the correct value if more kernels are added.

You can also change it to "default saved" to default to the last booted option. So if you have booted linux, it will reboot into linux, and if in windows it will reboot to windows.

---

### Post by Dasold on 2006-11-21
It's easier than all of this, just edit /boot/grub/menu.lst
**sudo gedit /boot/grub/menu.lst**

then search for the next lines:
```

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

```
now change 0 for the entry number of WinXP (ej: if winxp is the 4th option in your grub menu you must change "default 0" to "default 3" because numbering starts from 0 and not from 1.)

---

### Post by CowzRule on 2006-11-21
I would also add doing the following first
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```
makes a copy of the file for back up

---

### Post by wyldstryker on 2006-11-21
You might wanna check this out as well.  Nice little GUI for editing Grub. :) 

[GrubEd]("http://www.ubuntuforums.org/showthread.php?t=228104")

---

### Post by djlyx on 2006-11-21
The GUI does not seem to work, after asking me for password, nothing happens.

And the command gksu gedit /boot/grub/menu.lst is not recognized.

stumped...

---

### Post by djlyx on 2006-11-21
Oh wait, nevermind

I had to download the texteditor program that uses the command gedit.

I edited the sequence, XP is first on the list.

Everything is good to go!  Thanks!

---

