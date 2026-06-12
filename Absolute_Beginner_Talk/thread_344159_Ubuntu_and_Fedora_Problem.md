---
title: "Ubuntu and Fedora Problem"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by Tweedicus on 2007-01-22
Hi,

I have Ubuntu Edgy as my sole OS, it works great. Then my wife, seeing how much I was enjoying Linux, went out and bought me a special edition of a Linux magazine with Fedora 6 attached.

So I became overconfident and installed it.

Here's what I did and the problem.

I booted onto a gparted cd and partioned my HD.

I had Ubuntu on /dev/hda1 ext 3 

/dev/hda2 is extended and also has within it /dev/hda5 linux-swap

/dev/hda3 ext3 was free.

Onto this free partition I put Fedora 6. 

It installed fine onto the correct partition. I installed Grub from Fedora, and it recognised Ubuntu.

The computer boots fine into Fedora, and gives the option to boot into Ubuntu.

However, when I try to boot into Ubuntu I get the following message:

rootnoverifly (hd0,0)
chainloader +1

Error 13: Invalid or unsupported executable format

Press any key to continue.

When I press any key it goes back to the grub menu.

I feel sure it's a grub problem. I know Ubuntu is there and it wasn't wipped.

Tweed.

---

### Post by po0f on 2007-01-22
Tweedicus,

Reboot your computer.  When it gets to the GRUB menu, highlight the Ubuntu entry and press 'e'.  Scroll down to the "rootnoverify (hd0,0)" line and hit 'e' again.  Change it to "root (hd0,0)", pressing enter when you have completed the changes.  Change the "chainloader +1" line to read "kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash".  (You'll have to look at the menu to figure out how to add a line, IIRC it's 'o')  Add three lines that read "initrd /boot/initrd.img-2.6.17-10-generic", "quiet", and "boot".  Press 'b' to boot it.

If the above worked, you'll have to edit FC's GRUB menu.lst to reflect the changes.

HTH

---

### Post by Tweedicus on 2007-01-22
> **po0f said:**
> Tweedicus,
Change the "chainloader +1" line to read "kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash".  (You'll have to look at the menu to figure out how to add a line, IIRC it's 'o')  Add three lines that read "initrd /boot/initrd.img-2.6.17-10-generic", "quiet", and "boot".  Press 'b' to boot it.

If the above worked, you'll have to edit FC's GRUB menu.lst to reflect the changes.

HTH

Thank you, I've done the first part (changed root). Could you just break down the second part. I didn't really understand from the brackets onwards.

---

### Post by Tweedicus on 2007-01-22
I think I understand you now.

I did all what you said and I get the message:

root (hd0,0)
Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash

Error 15: File not found

Press any key

---

### Post by po0f on 2007-01-22
> **Tweedicus said:**
> Thank you, I've done the first part (changed root). Could you just break down the second part. I didn't really understand from the brackets onwards.

Tweedicus,

After edditing the "chainloader +1" line to "kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash", hit enter.  While that line is still highlighted, press 'o' to insert another line.  Put "nitrd /boot/initrd.img-2.6.17-10-generic" into it and hit enter.  While that line is highlighted, hit 'o' again to insert another line, "quiet".  Repeat the process one more time, entering "boot" as the last line line ([reference](http://www.gnu.org/software/grub/manual/html_node/Menu-entry-editor.html#Menu-entry-editor)).  When you have made all the changes, you should be able to press 'b' to boot.

---

### Post by po0f on 2007-01-22
Tweedicus,

Ok, change the "kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash" line to read "kernel (hd0,0)/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash" and the "initrd /boot/initrd.img-2.6.17-10-generic" line to read "initrd (hd0,0)/boot/initrd.img-2.6.17-10-generic".

---

### Post by Tweedicus on 2007-01-22
I made this change and got:


root (hd0,0)
Filesystem type is ext2fs, partition type 0x83
kernel (hd0,0)/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash

Error 15: File not found

Press any key

---

### Post by po0f on 2007-01-22
Tweedicus,

I guess you're just going to have to boot into FC to troubleshoot it from there.  When you get it booted, mount /dev/hda1 and look at the contents of its /boot directory.  I'm wondering why it isn't finding the kernel.

---

### Post by Tweedicus on 2007-01-22
I know this is a really basic thing, but how do I mount a disk?

---

### Post by po0f on 2007-01-22
Tweedicus,

From a terminal:
```
[FONT="Courier New"]$ sudo mkdir /mnt/hda1
$ sudo mount -t ext3 /dev/hda1 /mnt/hda1
$ ls /mnt/hda1/boot
$ sudo umount /mnt/hda1[/FONT]
```

I forget if FC require you to use `sudo` to do the above, but it shouldn't hurt if it doesn't.

---

### Post by Tweedicus on 2007-01-22
This is what I got:

abi-2.6.15-26-386   grub    System.map-2.6.15-27-386
abi-2.6.15-27-386   initrd.img-2.6.15-26-386      System.map-2.6.17-10-386
abi-2.6.15-10-386   initrd.img-2.6.15-27-386      vmlinuz-2.6.15-26-386
config-2.6.15-26-386     initrd.img-2.6.17-10-386   vmlinuz-2.6.15-27-386
config-2.6.15-27-386    memtest86+.bin        vmlinuz-2.6.17-10-386
config-2.6.17-10-386     System.map-2.6.15-26-386

---

### Post by Tweedicus on 2007-01-22
Thanks for trying to help.

After no luck here, someone who runs Edgy and FC6 helped me out on the FC forum.

The thread is here:

[http://forums.fedoraforum.org/forum/showthread.php?p=729557#post729557](http://forums.fedoraforum.org/forum/showthread.php?p=729557#post729557)

Just in case anyone else tries to dual boot Edgy and FC6 and runs into the same problem.

Cheers,

Tweed

---

### Post by po0f on 2007-01-22
Tweedicus,

I thought you were using the *-generic kernel.  Anyway, glad you got it all figured out.

---

### Post by rccharles on 2007-01-22
> **po0f said:**
> Tweedicus,

 look at the contents of its /boot directory.  


The file you are looking for is:
/boot/grub/menu.lst

Robert

---

### Post by po0f on 2007-01-23
rccharles,

Actually, the *files* I was looking for were the kernel and initrd files.

---

### Post by Pobega on 2007-01-23
What Linux magazine did your wife buy you? Linux Format by chance? I have a one year subscription to that magazine, last month they had a Fedora Core 6 DVD and this month it was Edgy/Fedora Core 6.

Just wondering.

---

