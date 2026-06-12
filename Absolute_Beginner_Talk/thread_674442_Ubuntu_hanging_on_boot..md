---
title: "Ubuntu hanging on boot."
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by TomLS on 2008-01-21
Right, evening all! It's my first real venture into Linux (after a breif and disasterous Mandriva release a few months ago) because I really hate Windows (but not as much as Macs)!

Ok, so when I first tried to install it it got to 94% and the same old story - grub cannot be installed. Tried 3 times with various lines of code in the command box none of which worked at all, until I eventually came to the easiest slution - install with ext2 file format instead of ext3 - and grub installed to (hd0) first time.
Great!

However, I go to load Ubuntu (kernel 2.6.22-14-generic) and I get about 8 or 9 lines flash on the screen for about half a second showing this:

"cannot allocate resource region 'x' of the bridge" where 'x' is any number between 1-9, but it's too fast to read.
It then black-screens until I hold the power button.

It won't run in safe mode either - it just gets as far as a disk check, restarts, then runs through the loading sequence and hangs with the flashing cursor. I can type what I like but nowt happens!


Any Ideas people?!

A bit of info about my system:
Acer Aspire 5672 Laptop,
Dual core 1.66Ghz processor,
2Gb RAM,
120Gb HDD, 4Gb FAT32 for OEM windows install (hidden), 55Gb FAT32 for windows XP partition (still running fine by the way), 55Gb ext2 for Ubuntu, 1Gb for swap file, in that order.
ATI 1400x graphics card.

If the result is going to need to be typing in code, treat me like a moron, you'll need to tell me where to type it!
Being a wizz with windows is a different kettle of fish!


Any info appreciated.
Tom.

---

### Post by spiderbatdad on 2008-01-21
not sure, but seems like there is a pci issue. when you say you tried various commands, I'm not sure what you mean. Have you tried interupting the boot sequence at grub by pressing f6? then delete the end of the boot parameter line up to and including "ro --quiet splash" and add the parameters "noapic nolapic" without quotes. If you press f1 after f6 you can view other options and f6 again shows more parameters. press esc to get back to boot sequence. Never tried this with ext2 though.

---

### Post by dstew on 2008-01-21
I agree with spiderbatdat. Sounds like an interrupt controller issue. The kernel boot parameters **noapic nolapic** should be tried.

---

### Post by TomLS on 2008-01-22
The various commands I referred to were when I was trying to get grub installed, now that done.

I don't know about f6, but I've edited the kernel line by pushing 'e' at grub, and 'e' to select the kernel, deleted "ro quiet splash" (mine has no dashes as yours does spiderbatdad) and input "noapic nolapic" but it just does the same as before.

As I've seen the screen flash a few more times, I can confirm all the error lines contain "PCI" and that all numbers (I labelled 'x' in last thread) are 7, 8, or 9.

It still black screens!

Tom.

---

### Post by dstew on 2008-01-22
You will probably have to look at the system logs to see what is happening. When your boot sequence gets stuck, try ctrl-alt-F1 to see if you can get a command prompt. If you can, look at the kernel log:```
cat /var/log/kern.log
```and see what the last messages are. There are other logs in the /var/log directory also. Most of the logs overlap some. The command **dmesg** will print the most recent system messages.

If you cannot get a command line on your installed Ubuntu, boot a LiveCD, open a terminal, and mount your hard disk Ubuntu root partition onto your LiveCD file system. Assuming your Ubuntu partition is /dev/hda1 the commands would be:```
sudo mkdir /mnt/hard_disk
sudo mount -t ext3 /dev/hda1 /mnt/hard_disk
```Then, to look at the kern.log file with cat:```
cat /mnt/hard_disk/var/log/kern.log
```

---

### Post by TomLS on 2008-01-23
Thanks for the input dstew.
I tried getting a command prompt when it crashes, and pushing ctrl+alt+f1 does make a load of script run, but I can't type anything when it finishes, it just freezes, so I loaded from the CD, and entered the terminal.
The line "sudo mkdir /mnt/hard_disk" doesn't appear to do anything.
The second line always returns that "/dev/hda1 cannot be found" or something similar. My Ubuntu is loaded on the 3rd of the 4 partitions on the single drive in the laptop. Does the numbering start and 0? and does the "dev" apply to the partition?
Also my drive is ext2 formatted no ext3 as it wouldn't work!

If so the line for my laptop would be:

"sudo mount -t ext2 /dev2/hda0 /mnt/hard_disk"  (if drive numbering starts at 0)

or:

"sudo mount -t ext2 /dev3/hda1 /mnt/hard_disk" (if drive numbering begins at 1)

However neither of these work. I've also tried different logical combinations that I can't remember!

See... I said I was a bit of a numpty :(

Tom.

---

### Post by mister_pink on 2008-01-23
It would be /dev/hda2 in your case - it starts at 0 and theres the windows partions! If that doesnt work try /dev/sda2

Edit: Whoops, cant count

---

### Post by dstew on 2008-01-23
To see how the system is naming the partitions, do **sudo fdisk -l** from the command line.

---

