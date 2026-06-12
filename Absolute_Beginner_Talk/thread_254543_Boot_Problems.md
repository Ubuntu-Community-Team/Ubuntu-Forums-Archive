---
title: "Boot Problems"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by shoot2kill on 2006-09-10
during boot up, i get the usual grub menu:
```

Ubuntu, Kernal 2.6.15-26-368
Ubuntu, Kernal 2.6.15-26-368 Recovery
Ubuntu, Kernal 2.6.15-25-368
Ubuntu, Kernal 2.6.15-25-368 Recovery
Ubuntu, Kernal 2.6.15-23-368
Ubuntu, Kernal 2.6.15-23-368 Recovery
Other O/S
Microsoft Windows XP Pro
```

but before today, i never had the 26-386 kernal, and now which ever ubuntu i select, i get the message

```

Error 17: Cannot Mount Selected Partition
Press any key to continue
```

when i press any key, i get the grub menu again... 

i can only boot to XP...

any help for this problem would be grateful...

---

### Post by orb9220 on 2006-09-10
[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)

---

### Post by anaconda on 2006-09-10
It sounds that you have downloaded updates and updated your kernel.

And whenever kernel is updated your grub-entries are also updated automatically..

I had the same problem whenever I updated a new kernel. Automatic detection of grub-entries just didn't work, so after each kernel-update ubuntu stopped booting and I got the same error 17..

To correct your problem you can boot with the liveCD (or if you have ext3-drivers for windows you can also boot to windows..)and manually edit the /boot/grub/menu.lst -file so that the ubuntu-partition is again correct..

Here is an example ubuntu-entry from (my) menu.lst -file:

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,0)
kernel          /vmlinuz-2.6.15-26-386 root=/dev/sda1 ro quiet splash
initrd          /initrd.img-2.6.15-26-386
savedefault
boot

the thing you propably have wrong is the (hd0,0) -part. (sometimes also the root=/dev/sda1 can be wrong..) (hd0,0) means the first partitin of your first hard-disk and (hd1,2) would mean the third partition of your second hard-disk ....

you have to change the (hd0,0) to correctly match your hardware setup.

eg. if you know that your ubuntu is on your first (or only hd) and it is in the third partition then you would have to change the (hd0,0) to (hd0,2)
and the root=/dev/sda1 should be root=/dev/sda3 (if you have ide drive then it would be root=/dev/hda3 . Usually the letters are correct, so you only have to change the number---)

After you get it to work it is a good idea to backup your menu.lst -file, or print it to paper..

---

### Post by anaconda on 2006-09-10
before editing your menu.lst it is also possible to boot to (your) ubuntu by pressing 'e' in grub, and edit the lines from there.. By doing this you can boot ubuntu, but the changes are not saved..

And to get grub automatically working after kernel-updates i had to edit these lines in the menu.lst -file

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

I think I had the groot -line reading like this:
# groot=(hd1,0)
when in reality my hd(0,0) was the first hd, from where booting is started.
And the line is really left commented. kernel update reads the commented line when it updates grub.

But now I dont update kernels wery often, because it breaks VMWare, and some other things..

---

### Post by shoot2kill on 2006-09-10
ok, thanks guys.. i will try that now

---

