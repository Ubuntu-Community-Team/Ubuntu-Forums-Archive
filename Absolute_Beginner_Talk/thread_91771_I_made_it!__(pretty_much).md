---
title: "I made it!  (pretty much)"
date: 2005-11-18
forum: Absolute Beginner Talk
---

### Post by TeeAhr1 on 2005-11-18
I'm partitioned, installed, and running!  The installation found all my hardware pretty much flawlessly, and I'm thrilled.  Two problems (besides the fact that I totally don't know what I'm doing):

1. I'm having issues with my wifi.  It's enabled, I can ping out.  But that's all.  Whenever I try to connect anywhere it hangs on "connecting to such-and-so..." (except the Mozilla page in the toolbar link, for some reason).  Can anyone explain this?

2. I set up an "extra" FAT32 partition to use for shared data between Windows and Ubuntu.  I used [this]("http://users.bigpond.net.au/hermanzone/p3.htm") howto, which was excellent.  I now have a shiny new 35GB partition, I can see it with fdisk as hda5, and I can see it in windows as G:.  It's there.  Now how in the screaming hell do I mount it?

That's my beef, but that's all, as far as I can tell everything else works perfectly out of the box.  Have I mentioned how happy I am with that?

Seriously, if anyone has some insight, I'd appreciate any help.

---

### Post by MichaelM on 2005-11-18
1. No idea, sorry.

2. Try this (from System > Help > Ubuntu 5.10 Starter Guide):
> How do I mount Windows partitions (FAT) on boot-up, and allow all users to read/write?

    Assuming that /dev/hda1 is the location of the Windows partition (FAT) and the local mount folder is: /media/windows

       1.
          Read How do I check disk space and view the partition table?

       2.
			sudo mkdir /media/windows 
			sudo cp /etc/fstab /etc/fstab_backup 
			sudo gedit /etc/fstab

       3.
          Append the following line at the end of file

			/dev/hda1 /media/windows vfat umask=000 0 0

       4.
          Save the edited file (sample/fstab_automountfat)

       5.
          Read How do I remount /etc/fstab without rebooting?
Of course, you would change /dev/hda1 to /dev/hda5, and you can call your mount folder pretty much anything you want (/media/windows isn't what I use).
For mounting from the command line, you would do```
sudo mount -t vfat /dev/hda5 (whatever your mount folder is)
```

---

### Post by ad noiseam on 2005-11-18
[QUOTE=TeeAhr1]2. I set up an "extra" FAT32 partition to use for shared data between Windows and Ubuntu.  I used [this]("http://users.bigpond.net.au/hermanzone/p3.htm") howto, which was excellent.  I now have a shiny new 35GB partition, I can see it with fdisk as hda5, and I can see it in windows as G:.  It's there.  Now how in the screaming hell do I mount it?[/QUOTE]

Try to type in a terminal:

```

sudo mkdir /media/whateveryouwanttocallit
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab

```

then add at the end:
```

/dev/hda5       /media/whateveryouwanttocallit vfat    iocharset=utf8,umask=000   0       0

```

Then you might want to go to:
Applications -> System Tools -> Configuration Editor


and check the option to see the drives on your dektop.

Good luck.

Nicolas

---

