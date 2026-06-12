---
title: "Finding files on USB HD after Edgy buffoonery?!"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by kweejibo on 2006-11-16
Hello,

I did what some other fools have and didn't RTFM re: the upgrade to Edgy. I ended up with a broken Dapper system and can't seem to fix the thing. 

I did a clean install of Edgy (following the instructions-- thanks!) on another HD and put the old one in an external USB housing. It shows up under "Places" but all I see on the drive are "grub" and "lost+found" and a bunch of "Config..." "Memtest..." "VMLinuz..." and other files. I tried looking for hidden files, but that didn't help. Is there a way to get to the "home" folder to see if I can retrieve some of the stuff on that drive?

Thanks,
Josh

---

### Post by joshsherman on 2006-11-17
Please clarify for me, the drive in the USB housing is the same drive you installed Ubuntu to?

-j

---

### Post by steve.horsley on 2006-11-17
Sorry, but it looks like your old disk is scrambled. You should see something like this lot on a root partition:
> steve@Dingly:~$ ll /mnt/hda6
total 30
drwxr-xr-x   2 root root  2584 2006-10-07 22:31 bin
drwxr-xr-x   3 root root   528 2006-10-29 11:27 boot
lrwxrwxrwx   1 root root    11 2006-05-05 18:03 cdrom -> media/cdrom
drwxr-xr-x   5 root root 11352 2006-04-27 04:21 dev
drwxr-xr-x 111 root root  5984 2006-11-01 22:02 etc
drwxr-xr-x   2 root root    48 2006-06-27 10:33 home
drwxr-xr-x   2 root root    48 2006-04-27 04:15 initrd
lrwxrwxrwx   1 root root    29 2006-09-20 08:18 initrd.img -> boot/initrd.img-2.6.15-27-686
lrwxrwxrwx   1 root root    29 2006-07-12 08:31 initrd.img.old -> boot/initrd.img-2.6.15-26-686
drwxr-xr-x  19 root root  4512 2006-06-03 21:36 lib
drwxr-xr-x   9 root root   240 2006-10-19 09:50 media
drwxr-xr-x   5 root root   120 2006-08-01 11:43 mnt
drwxr-xr-x   7 root root   208 2006-10-12 08:18 opt
drwxr-xr-x   2 root root    48 2006-03-27 11:38 proc
drwxr-xr-x  28 root root  1432 2006-11-01 21:44 root
drwxr-xr-x   2 root root  6056 2006-09-20 08:18 sbin
drwxr-xr-x   2 root root    48 2006-04-27 04:15 srv
drwxr-xr-x   2 root root    48 2006-04-12 15:31 sys
drwxrwxrwx   2 root root    48 2006-10-05 13:20 tftpboot
drwxrwxrwt   9 root root   368 2006-11-01 22:02 tmp
drwxr-xr-x  11 root root   288 2006-05-11 10:27 usr
drwxr-xr-x  14 root root   336 2006-04-27 04:27 var
lrwxrwxrwx   1 root root    26 2006-09-20 08:18 vmlinuz -> boot/vmlinuz-2.6.15-27-686
lrwxrwxrwx   1 root root    26 2006-07-12 08:31 vmlinuz.old -> boot/vmlinuz-2.6.15-26-686



---

### Post by kweejibo on 2006-11-18
> **joshsherman said:**
> Please clarify for me, the drive in the USB housing is the same drive you installed Ubuntu to?

-j

The drive in the USB housing has the original drive with corrupted Dapper on it. It shows up nicely as "USB /root" on the desktop. I've got another drive in the bay of the laptop with a clean install of Edgy.

I just can't figure out how to get to the files on the Dapper drive. When I try to boot it (installed in the bay), messages about the display libraries being missing (or something like that, X?) and it goes to a command line. I can tool around in the various directories from there, but I can't seem to get there when it's in the USB housing. 

Josh Brehm

---

### Post by CatKiller on 2006-11-18
> **kweejibo said:**
> It shows up under "Places" but all I see on the drive are "grub" and "lost+found" and a bunch of "Config..." "Memtest..." "VMLinuz..." and other files. I tried looking for hidden files, but that didn't help. Is there a way to get to the "home" folder to see if I can retrieve some of the stuff on that drive?

When you installed Ubuntu on the drive that is now in the enclosure, did you make a seperate **/boot** partition? If so, that's what you're looking at. My /boot directory looks like this:

> iain@weatherwax:~$ ls /boot
abi-2.6.15-26-k7     grub                     System.map-2.6.15-26-k7
abi-2.6.15-27-k7     initrd.img-2.6.15-26-k7  System.map-2.6.15-27-k7
config-2.6.15-26-k7  initrd.img-2.6.15-27-k7  vmlinuz-2.6.15-26-k7
config-2.6.15-27-k7  memtest86+.bin           vmlinuz-2.6.15-27-k7


You may well need to mount one of the other partitions to find the one that was your **/** partition.

---

### Post by kweejibo on 2006-11-18
I guess I'm not explaining this very clearly. 

I have a clean install of Edgy in the laptop hd bay right now as I type this. I works fine. Love it. Happy. Happy. Happy. Missing some files from the old install of Dapper that I broke by not following directions I didn't read. Slightly sad.

If I plug the old drive (separate unit-- not the one that's running right now in the laptop upon which I'm typing) with the corrupted Dapper install on it into an external USB housing, I can then plug that into the corresponding USB port on the laptop. The old drive (with the corrupted version of Dapper on it) will show up as USB /boot on the desktop or in /media as the same. 

When I try to list the contents of the drive, I can't seem to see what's there. Should I try somehow renaming it or maybe unmounting and remounting it? This is basically a problem of file manipulation ignorance, I think.

Thanks,
Josh

---

