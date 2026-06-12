---
title: "Kernel panic, not 100% sure of the cause"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by skyhopper88 on 2007-02-15
My setup,
hdb1 - extended
hdb8 - boot ~ 30 megs
hdb7 - root  ~ 15 gigs
hdb5 - home ~ 40 gigs
hdb6 - swap ~ 2 gigs

Here are the recent things I've done:

I attempted to compile kiba-dock, and it put files into my boot partition for some reason, telling me it was nearly full (currently .98 megs free). I deleted what I assumed it made and cleared kiba-dock from my system and thought nothing of it. Guess I did make it too small for my own good.

I installed ntfs-3g packages but did no configuring. I attempted to mount my external ntfs drive first and was told it couldn't for some reason (told me to boot into Windows twice or force mount). I opted to boot into Windows twice but when I returned to Ubuntu (any kernel or recovery) I get a kernel panic (unable to mount root fs on unknown block (0,0). By pressing e to edit when grub loads I see that the root is (hd0,7) and my kernel line reads /dev/hdb7. Here is my menu list

```


title		Ubuntu, kernel 2.6.17-50-generic
root		(hd0,7)
kernel		/vmlinuz-2.6.17-50-generic root=/dev/hdb7 ro quiet splash
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-50-generic (recovery mode)
root		(hd0,7)
kernel		/vmlinuz-2.6.17-50-generic root=/dev/hdb7 ro single
boot

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,7)
kernel		/vmlinuz-2.6.17-11-generic root=/dev/hdb7 ro quiet splash
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,7)
kernel		/vmlinuz-2.6.17-11-generic root=/dev/hdb7 ro single
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,7)
kernel		/vmlinuz-2.6.17-10-generic root=/dev/hdb7 ro quiet splash
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,7)
kernel		/vmlinuz-2.6.17-10-generic root=/dev/hdb7 ro single
boot

title		Ubuntu, memtest86+
root		(hd0,7)
kernel		/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

``` 

My Windows is on a master sata with Ubuntu on a slave ide, bios booting from the ide. My linux drives are currently mounted in windows, so I can grab other data if need be.

---

### Post by Tomosaur on 2007-02-15
What is the output of ```

ls /

```
I thought Ubuntu by default put the kernels into /boot?

---

### Post by skyhopper88 on 2007-02-15
It might, I'm not sure. Something may have changed on my list. My kernel config files are located in my boot partition which is hdb8 if I'm not mistaken. Maybe I need to change refereances from hdb7 to hdb8? How do I get to a command line to enter "ls /"?

---

### Post by Tomosaur on 2007-02-15
If you're using Ubuntu:
```
Applications > Accessories > Terminal
```

If you're using Kubuntu:
```

K button > Utilities > Terminal

```

I'm a little fuzzy on the KDE side, since I don't use it, but I think that's right.

Alternatively, just hit Ctrl + Alt + F1 (or any F button up to 6) for a full screen terminal. Hitting Ctrl+Alt+F7 will bring you back to the GUI.

---

### Post by skyhopper88 on 2007-02-15
Changing hdb7 to hdb8 didn't work. Do you mean run that from a LiveCD? I can't get to any kind of gui any other way, nore can I go in to recovery.

---

### Post by Tomosaur on 2007-02-15
Haha sorry, mind went a bit screwy there. In the case of a kernel panic, you can try fixing it through a Live CD (I am currently in the midst of a hellish kernel panic too, something keeps going wrong with a custom kernel and I can't figure out what). However, the method to resolving the issue may be completely different from any other advice. My common method is as follows:

[LIST]
Boot from LiveCD
Open a terminal.
Mount my hard drive (instructions below)
Change the references of vmlinuz, config, and system map to old kernels (instructions below)
See if there's an older menu.lst file (instructions below)
Reboot, and hope for the best!
[/LIST]

To mount your hard drive from a live CD, open a terminal, then type:
```

mkdir ~/my_hd
sudo mount /dev/hdb7 ~/my_hd

```

Then, change directory into the mounted HD folder:
```

cd ~/my_hd

```

Next, alter references to config, system.map and vmlinuz. Your may be different here - all my kernels and config stuff is in /boot, but yours appears to be in the / directory. I'll assume yours are in /, but please check to see whether they're in boot. You need to do a simple check to see whether the files referred to ARE links, rather than actual files. If not, then stop, and post here, otherwise you may mess something up even more. To check:
```

ls -l ./

```
The vmlinuz file should be listed something like this:
```

-r--r--r-- [date] vmlinuz ---> vmlinuz-[version number]

```

The important thing is the little arrow. This signifies a link. If the arrow is present, it's safe to delete the vmlinuz file, since it's not really a file, just a shortcut. DON'T DELETE THE ONE WITH THE VERSION NUMBER!
```

sudo rm ./vmlinuz

```

Now, you need to recreate the link, but with the older, working kernel.
```

sudo ln -s ./vmlinuz-[working kernel version] ./vmlinuz

```
This should create a new vlinuz link with the old kernel version.

You must do the same things with the config and System.map files. Remember to only delete the short named ones though, not the ones with version numbers!

Now that's done, you need to check whether there's an older menu.lst file available:
```

cd ./boot/grub
ls ./menu.lst*

```
This should show any files with menu.lst in their name. If you see any with a character appended on the end (normally it is the tilde character: ~, so the file will be called menu.lst~), then those are backups, and should be safe to use. You can overwrite the broken menu.lst like this:
```

sudo mv ./menu.lst~ ./menu.lst

```
If you can't find a backup, or you're unsure of whether the backup is ok, you should check your menu.lst and basically just fix it so the relevant bits point to the relevant files.

Now, when you reboot, your older menu.lst should be back, and the kernels should boot ok. If they don't, you'll have to boot into a LiveCD again and try something else.

Good luck!

---

### Post by skyhopper88 on 2007-02-15
I have a backup, but it appears to be the same. I'll go into the livecd and try the other things you suggested.

---

### Post by skyhopper88 on 2007-02-15
ubuntu@ubuntu:~/my_hd$ ls /
gives
> bin   cdrom  etc   initrd      lib    mnt  proc  root  srv  tmp  var
boot  dev    home  initrd.img  media  opt  rofs  sbin  sys  usr  vmlinuz

Most of the entries are a dark blue, initrd.img is red on black, vmlinuz is light blue

ls -l ./ gives
> total 128
drwxr-xr-x   2 root root  4096 2007-02-15 14:43 bin
drwxr-xr-x   2 root root  4096 2007-02-15 02:01 boot
lrwxrwxrwx   1 root root    11 2007-02-15 02:01 cdrom -> media/cdrom
drwxr-xr-x   4 root root  4096 2007-02-15 22:49 dev
drwxr-xr-x 117 root root  8192 2007-02-15 22:54 etc
drwxr-xr-x   2 root root  4096 2007-02-15 02:01 home
drwxr-xr-x   2 root root  4096 2006-10-25 13:26 initrd
drwxr-xr-x  17 root root  8192 2007-02-15 14:44 lib
drwxr-xr-x   2 root root 49152 2007-02-15 02:01 lost+found
drwxr-xr-x   3 root root  4096 2007-02-15 22:53 media
drwxr-xr-x   2 root root  4096 2006-10-19 22:49 mnt
drwxr-xr-x   5 root root  4096 2007-02-15 19:41 opt
drwxr-xr-x   2 root root  4096 2006-10-19 22:49 proc
drwxr-xr-x  13 root root  4096 2007-02-15 22:51 root
drwxr-xr-x   2 root root  4096 2007-02-15 22:49 sbin
drwxr-xr-x   2 root root  4096 2006-10-25 13:26 srv
drwxr-xr-x   2 root root  4096 2006-10-10 14:46 sys
drwxrwxrwt  22 root root  4096 2007-02-15 22:54 tmp
drwxr-xr-x  14 root root  4096 2007-02-15 21:13 usr
drwxr-xr-x  15 root root  4096 2006-10-25 13:39 var
lrwxrwxrwx   1 root root    30 2007-02-15 14:52 vmlinuz -> boot/vmlinuz-2.6.17-50-generic
lrwxrwxrwx   1 root root    30 2007-02-15 14:52 vmlinuz.old -> boot/vmlinuz-2.6.17-11-generic


Forgive me, but I'm not sure what do do from here.

---

### Post by skyhopper88 on 2007-02-15
Should I/could I restore vmlinuz.old to vmlinuz? And what do I need to enter to restore the config and system.map files?

---

### Post by Tomosaur on 2007-02-15
Yes, looks like you could rename vmlinuz.old to vmlinuz, that may work. If the 2.6.17-11-generic kernel was the one which worked, you basically just need to make all the linked files (vmlinuz, config, system.map) point to the file for that version. The short filename is just a link, similar to shortcuts in windows. When you install a new kernel, these links get pointed to the new kernel - so if that kernel won't work, you need to go and restore all the links yourself. If you do ls -l in the ~/my_hd/boot folder, you should see more linked files. The '->' signifies a link, with the left hand filename being the 'fake' file, and the right hand filename being the 'real' file.

For your menu.lst, if it's the same file, you'll need to change some things. Near the bit you pasted earlier, you'll see that those references point to the new kernel. You need to change them to point to the older version (the one which worked).

The config and system.map files are both links too, but they'll be pointing to the newer (broken) kernel, so you need to make them point to the config and system.map files of the old, working version.

---

