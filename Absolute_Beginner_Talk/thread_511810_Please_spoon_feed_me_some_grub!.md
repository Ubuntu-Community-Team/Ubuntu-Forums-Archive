---
title: "Please spoon feed me some grub!"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by Beat Pitt on 2007-07-28
Background: I am a Linux "NOVICE" with a dual-boot XP-Ubuntu set-up on a Dell PC. The configuration was setup by a former coworker who I've lost contact with. After a long hiatus, I logged into the Ubuntu side and ran a bunch of updates. The next time I booted the PC, XP was no longer listed as a boot option.

Where I'm at now: I located the grub file and slopped in some code that I think will restore XP as the default login. I got a message that I don't have rights to update the grub file, but I know that my buddy set me up as a/the admin.

Any advice on how I can:

1) verify where my XP install in housed (I have multiple partitions) and then properly add an XP reference to the grub(I want XP to be the default)

2) save the updated grub

I can track down the former coworker, but that would be poor form. I haven't made much of an effort to keep in touch otherwise.

Thanks in advance.

---

### Post by MQMike on 2007-07-28
Here's two:

How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)
(general GRUB methods for everyday use)

Bigpond, GRUB:   [http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)
(the classic GRUB reference for doing many neat things)

---

### Post by Midahed on 2007-07-28
You probably can't save the file because you aren't root.  If you just navigate to the file and open it via the GUI you'll be doing so as 'yourself', rather than root.

Assuming you're using something like gedit as your editor, you need to open a terminal session and do something like:-

sudo gedit <full path and filename>

in order to be able to edit it as root.

Mike

---

### Post by Beat Pitt on 2007-07-28
I'm going to go off and experiment -- and cut grass :(.

I'll respond later with some follow-up questions or some sincere appreciation.

---

### Post by confused57 on 2007-07-28
The links MQMike gave you are excellent...to determine which partition Windows is on:
```
sudo fdisk -l
```
the -l is a small "L"

Being a Dell your Windows install might be on the 2nd partition (hd0,1).

To edit grub:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

add your Windows entry to the very end of the menu.lst file(after ###END DEBIAN AUTOMAGIC...),
quit & save

There are some example Windows entries in your menu.lst file that would probably work, except modify it to your root partition, e.g. root (hd0,1), or wherever your Windows is located.

---

### Post by MQMike on 2007-07-28
Yes, the boot menu entry for Windows (in /boot/grub/menu.lst file, contained in your Ubuntu), is like

title  Windows or whatever you wish to call it
rootnoverify (hdx, y)
makeactive
chainloader +1

where the (hdx, y) is the hard drive x and the partition y where Windows is located, and that information can come from the sudo fdisk –l that confused57 told you about.
Note:  GRUB counts drives and partitions starting from zero.
Ex:  First hard drive, first partition is (hd0, 0).
Ex:  First hard drive, second partition is (hd0, 1).

---

### Post by Beat Pitt on 2007-07-28
OK. The grass is cut, and thanks to you guys I have learned how to verify which partition Windows is on (3) and I've learned to properly open grub. I've entered the text below and I now see the Windows option at startup, but nothing happens when I select it. Have I left off something important?



## ## End Default Options ##

title		Pick me for Windows
root		(hd0,3)
makeactive
chaniloader +1

title		Ubuntu...

---

### Post by MQMike on 2007-07-28
Is (hd0, 3) correct?  You said (3) Windows.  What's on (hd0, 0) then?

(Also, long shot:  In updating Ubuntu, I wonder if somehow the new UUIDs didn't get into the picture in a naughty way.)

---

### Post by confused57 on 2007-07-28
If Windows is on partition #3 then:
```
title Pick me for Windows
root (hd0,2)
makeactive
chainloader +1
```

---

### Post by Beat Pitt on 2007-07-28
I'm still floundering.

Partition 1 is HPFS/NTFS, i.e. my data/files
Partition 2 is Linux
Partition 3 is W95 Fat 32, i.e. XP
Partition 4 is Linux swap

I'v tried (hd0,3) and (hd0,2)
and I've tried root and rootnoverify

I'm at a loss.

---

### Post by Vague on 2007-07-28
You sure XP's not on that NTFS partition?  That'd be my guess.

---

### Post by Beat Pitt on 2007-07-28
If partition 1 is XP, then I need 0,0 in the grub reference. Didn't work.

I'm gonna take a break and watch SNL on E. It's one of my favorite episodes with the plagiarism skit.

---

### Post by confused57 on 2007-07-28
> **Beat Pitt said:**
> If partition 1 is XP, then I need 0,0 in the grub reference. Didn't work.

I'm gonna take a break and watch SNL on E. It's one of my favorite episodes with the plagiarism skit.

It would really be best if you could copy & paste(rather than typing) your Windows entry in grub and the output of:
```
sudo fdisk -l
```

---

### Post by zero244 on 2007-07-28
Watch what your doing with the menu list or you might have to rebuild it.
On my menu list all I have to do is change the default boot number to match which item I want at the top of the list.
Not sure why its not working for you.

---

### Post by alienexplorers on 2007-07-28
Ytry adding the parts of your missing ubuntu boot/grub/menu.lst with the lines of code listed below.  You may need to alter the druve and directory entries.

> ## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-28-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
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
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


---

### Post by Beat Pitt on 2007-07-29
alien,

I pasted in your text and I can get back into windows. The grub page is a mess, but I'll try to clean it up later.

Thanks.

---

### Post by MQMike on 2007-07-29
So you edited /boot/grub/menu.lst using sudo (admin privileges), and you saved the edits (File – Save, File –Exit), and you tried (hd0, 2).  No go.  
Hmmm . . . What happened when you highlight & select the XP entry in the boot menu?  Or, what happens starting when you first turn on the PC?

---

