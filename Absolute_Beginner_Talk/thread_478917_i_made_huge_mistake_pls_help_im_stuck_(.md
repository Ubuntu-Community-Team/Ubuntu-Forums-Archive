---
title: "i made huge mistake pls help im stuck :("
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by violin on 2007-06-19
ok friends, my friend gave this backtrack live cd. To be honest i liked it then i said to myself why not install to hdd. But i didnt realize that it screw my linux swap. Now when i restart the comp it starts backtrack. Help me pls I want my ubuntu back :( I tried to unistall the backtrack nothing happened grub is still same so i figure i should reinstall backtrack again maybe it will turn back normal. Nothing happened it still start backtrack i dont know what to do. should i re install the grub if so how. Im stuck pls help. oh i forgot to tell you my ubuntu is still there but no grub i mean it start backtrack.

---

### Post by jfinkels on 2007-06-19
> **violin said:**
> ok friends, my friend gave this backtrack live cd. To be honest i liked it then i said to myself why not install to hdd. But i didnt realize that it screw my linux swap. Now when i restart the comp it starts backtrack. Help me pls I want my ubuntu back :( I tried to unistall the backtrack nothing happened grub is still same so i figure i should reinstall backtrack again maybe it will turn back normal. Nothing happened it still start backtrack i dont know what to do. should i re install the grub if so how. Im stuck pls help. oh i forgot to tell you my ubuntu is still there but no grub i mean it start backtrack.
Are you in Ubuntu right now, or Backtrack?

Can you post the output of the following command:```
sudo fdisk -l
```and post the output of this command:```
cat /boot/grub/menu.lst
```Do you know which partitions contain which operating systems? How do you know Ubuntu is "still there"?

---

### Post by overdrank on 2007-06-19
> **violin said:**
> ok friends, my friend gave this backtrack live cd. To be honest i liked it then i said to myself why not install to hdd. But i didnt realize that it screw my linux swap. Now when i restart the comp it starts backtrack. Help me pls I want my ubuntu back :( I tried to unistall the backtrack nothing happened grub is still same so i figure i should reinstall backtrack again maybe it will turn back normal. Nothing happened it still start backtrack i dont know what to do. should i re install the grub if so how. Im stuck pls help. oh i forgot to tell you my ubuntu is still there but no grub i mean it start backtrack.

Hi if you follow this thread and reinstall the grub that should help
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Good luck!:popcorn:

---

### Post by violin on 2007-06-19
hi thaks for quick answer


bt ~ # sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           10341       18144    62685630   83  Linux
/dev/sda2   *         192        9920    78144512    7  HPFS/NTFS
/dev/sda3            9921       10340     3373650   82  Linux swap
/dev/sda4           18145       19457    10546672+  83  Linux

Partition table entries are not in disk order


im on backtrack right now


should i open ubuntu with live cd.

---

### Post by violin on 2007-06-19
i know because i open ubuntu with live cd and i checked gnome partiton everything seems normal.

---

### Post by violin on 2007-06-19
should i re install the grub

---

### Post by jfinkels on 2007-06-19
> **violin said:**
> should i re install the grub

You could do that, or you could copy the appropriate entries in your Ubuntu /boot/grub/menu.lst to your Backtrack /boot/grub/menu.lst. Let me know if you need help doing it that way.

---

### Post by violin on 2007-06-19
hi again i open the live cd when i write sudo gedit /boot/grub/menu.lst it gives me empty file. What do u suggest?

---

### Post by dfreer on 2007-06-19
you probably have to mount the filesystem before you do that command.

---

### Post by violin on 2007-06-19
sorry i didnt understand what do you mean what is the command for that.

cheers

---

### Post by dfreer on 2007-06-19
ummm. find out what your partition names are with this command from the live CD:
```
sudo fdisk -l
```
It should list your partitions and hard drives, with names like /dev/hda1 /dev/sdb2 and so on.
From there, you'll need to mount the partition that contains /boot/grub/menu.lst, and you should be able to edit it with the command you were using earlier:
```
sudo gedit /boot/grub/menu.lst
```

---

### Post by violin on 2007-06-19
[PHP] sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           10341       18144    62685630   83  Linux
/dev/sda2   *         192        9920    78144512    7  HPFS/NTFS
/dev/sda3            9921       10340     3373650   82  Linux swap / Solaris
/dev/sda4           18145       19457    10546672+  83  Linux

Partition table entries are not in disk order
[/PHP]
mount
[PHP] mount
unionfs on / type unionfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
[/PHP]

---

### Post by violin on 2007-06-19
/dev/sda1           10341       18144    62685630   83  Linux  that is my ubuntu
/dev/sda3            9921       10340     3373650   82  Linux swap / Solaris  swap

when i write mount /dev/sda1 

it gives me this

[PHP] mount /dev/sda1
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab
[/PHP]

when i do cat /dev/sda1
it gives me this

[PHP]cat /etc/mtab
unionfs / unionfs rw 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.17-10-generic/volatile tmpfs rw 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
[/PHP]

what i doing wrong here

---

### Post by violin on 2007-06-19
i have to bump this sorry

---

### Post by Nekiruhs on 2007-06-19
```
mount -t ext3 /dev/sda1 /media/ubuntu
```
That'll mount it for you at /media/ubuntu
```
gksudo gedit /media/ubuntu/boot/menu.lst
```
Will open the menu.lst, just copy the ubuntu boot stanzas to your backtrack /boot/grub/menu.lst

and please use [ CODE ] [ /CODE ] tags instead of PHP tags (Without the spaces before and after the brackets..

---

### Post by jfinkels on 2007-06-19
To mount a filesystem, first make a mountpoint (an arbitrary directory):```
sudo mkdir /mnt/foobar
```

Now mount it like this:```
sudo mount /dev/sda1 /mnt/foobar
```

You will now be able to browse the files in /mnt/foobar/ and you will find that they are the files that were in you Ubuntu installation. 

To find the entries in the Ubuntu /boot/grub/menu.lst, open it like this:```
gedit /mnt/foobar/boot/grub/menu.lst
```

Scroll to the bottom where there are entries that look like this:```
title [...]
root [...]
kernel [...]
initrd [...]

``` etc. the "[...]" represents text that I have left out for my own convenience, as I am not in Ubuntu right now.

Now, select and copy those entries.

Now make a mountpoint for backtrack and mount it (assuming that you install backtrack to /dev/sda4):```
sudo mkdir /mnt/backtrack
sudo mount /dev/sda4 /mnt/backtrack
```

Open the backtrack menu.lst:```
gksudo gedit /mnt/backtrack/boot/grub/menu.lst
```

Now copy the entries from the Ubuntu menu.lst to the bottom of Backtrack menu.lst. Save the backtrack menu.lst file and reboot. You should see options in GRUB now for UBuntu.

---

### Post by violin on 2007-06-20
ok i followed the instruction but i m stuck in last part 

gksudo gedit /mnt/backtrack/boot/grub/menu.lst => it opens it but i cant save anything it says FILE NOT FOUND. Btw Im on ubuntu Live Cd. Should Do the process on backtrack.

cheers

---

### Post by LaRoza on 2007-06-20
-edit They were quick

---

### Post by violin on 2007-06-20
what do you mean i didnt understand.

---

### Post by violin on 2007-06-20
ok i find it inside backtrack boot there four files map, splash.bmp, splash initrd, vmlinuz. I think i need to edit vmlinuz it gives me no suitable application. Another thing is I just checked the gparted and my linux swap empty. Is there posiblity that i can re install just swap.

cheers

---

### Post by violin on 2007-06-20
no one bump

---

### Post by violin on 2007-06-20
GUys i found the problem for those who wants to this Xp+ubuntu+backtrack do like this.

first install windows (if you have already install it dont touch it)
second install backtrack  
third ubuntu


then to make it work all of it you should add this  

sudo gedit /boot/grub/menu.lst

end of the line add this

title BackTrack
(hd0,3)
kernel /boot/vmlinuz vga=791 root=/dev/hda2 ro
boot

you are good to go .save and restart. thats it thanks everyone.

cheers

---

### Post by jfinkels on 2007-06-20
> **violin said:**
> GUys i found the problem for those who wants to this Xp+ubuntu+backtrack do like this.

first install windows (if you have already install it dont touch it)
second install backtrack  
third ubuntu


then to make it work all of it you should add this  

sudo gedit /boot/grub/menu.lst

end of the line add this

title BackTrack
(hd0,3)
kernel /boot/vmlinuz vga=791 root=/dev/hda2 ro
boot

you are good to go .save and restart. thats it thanks everyone.

cheers

This is in brief what I was trying to explain to you. It is important to note that although you may have multiple partitions (i.e. multiple distribution installations) and therefore multiple /boot/grub/menu.lst files, only ONE of them affects the GRUB on the Master Boot Record. All you needed to do was add an entry (title, root, kernel, initrd, etc.) in the one that actually affects GRUB (which I think was Backtrack in your case, but I'm not sure because your explanations were not very clear).

In the future, be sure to follow the rules of English syntax and please describe your problem clearly and with as much detail as possible!

---

