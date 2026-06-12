---
title: "GRUB How to tidy up bootup menu"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by drifternel on 2006-06-21
I have managed to set default os to win xp (thanks Aysiu!) - the rest of the family thank you.
How can I tidy up the options on the bootup screen (below).
I have what almost apprears as two copies of ubuntu - both boot into the same copy.
I'm presuming that one is because I did the updates as it has a slightly different number?
It would be great not to be confronted with a screen full of text though.
Any solutions folks?

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by glotz on 2006-06-21
comment out the paragraphs you dont like with #, e.g.

#title Ubuntu, kernel 2.6.12-10-386 (recovery mode)
#root (hd1,0)
#kernel /boot/vmlinuz-2.6.12-10-386 root=/dev/hdb1 ro single
#initrd /boot/initrd.img-2.6.12-10-386
#boot

---

### Post by anaconda on 2006-06-21
Yep. I would comment all others out, execpt 
first ubuntu
windows

And if you want recovery mode, you can always select "e" in grub, and add "single" to the options... 

Notice that when you comment entries away, the number of the "windows"-entry changes. That is why I like to keep the default booting OS the first entry, so it is always nro. "0"

---

### Post by bruce89 on 2006-06-21
You could delete the old -9 kernel with synaptic, as it uses 100MB.  Just use synaptic's Installed (local or obselete) view.

---

### Post by mlind on 2006-06-21
on /boot/grub/menu.lst

change
```

# memtest86=**false**

```

Uninstall old kernels or adjust bootsplash to display just 2 different kernels with 
recovery mode for both
```

# howmany=**2**

```

then execute
```

sudo update-grub

```

---

### Post by drifternel on 2006-06-22
Thanks folks
Oh dear...
unfortunately, I acted straight away after the first reply and was obviously over enthusiastic with commenting out entries (not your fault Glotz!!) and now grub doesnt load.
All it did was give me a load of options like unhide, memtest etc etc loads of them.
Nothing seemed to work.
In desperation I did try to reinstall the windows mbr  with a boot disk and now I've got a screen full of 9's! Help.
Question, how can I reinstall/repair grub so it lists everything again?
I am really new to this as you can see.
Thanks

---

### Post by glotz on 2006-06-22
Oops! Did you actually run fixmbr?

(You could have booted using the LiveCD and uncommented the entries)

---

### Post by drifternel on 2006-06-22
No I dont think so...
it was a windows reinstall cd that came with the computer.
Dont think i ran anything as it got to the bit where it wanted to delete the partitions and I turned it off as it was getting late.
Possibly be ok to run the live cd?
Slight problem though, i was running breezy and my live cd is for dapper - will that make a difference?
I never could get dapper to install with the live cd (sound, video, usb problems) so just gave up on it (same problems when trying upgrade breezy to dapper with the upgrade manager) and thought I'd stick with breezy untill I found my feet with Linux a bit.
I'm at work now so will have to give it a go tonight.
Any other advice - while I've got an internet connection today would be appreciated though.
Thanks

---

### Post by glotz on 2006-06-22
Sounds like you're good to go if you made no changes. It doesn't matter which liveCD you've got. Any (distro) will do as you only have to mount the harddisk and edit the textfile.

If you describe your problems and your system setup in more detail, somebody will probably know what to do.

---

### Post by drifternel on 2006-06-22
Will give it a go
thanks

---

### Post by Foxcow on 2006-06-22
Thank you!

---

