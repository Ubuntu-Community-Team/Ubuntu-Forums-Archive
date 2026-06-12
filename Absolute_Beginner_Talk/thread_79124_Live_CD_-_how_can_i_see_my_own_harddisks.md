---
title: "Live CD - how can i see my own harddisks?"
date: 2005-10-19
forum: Absolute Beginner Talk
---

### Post by menu on 2005-10-19
Hello
I am very happy that the live CD starts flawlessly on my powermac.

**Now how can i read and write to my own harddisks?**

I can see the disks in the Ubuntu disks manager but all the partitions are listed as inaccessible, clicking "Enable" does nothing.
I have been clicking around and searching the web for some time now but i cannot find any help on this. 
Please point me in the right direction.
thanks, Menu

System:Powermac G4-Latest ubuntu ppc live CD Three internal hard drives mac osX formatted

---

### Post by Jenda on 2005-10-19
Now if it was a PC, I would open a terminal and:
```

sudo mkdir /media/ze-disk-u-want-to-mount
sudo mount /dev/ze-disk-u-want-to-mount /media/ze-disk-u-want-to-mount
```
I can only suppose this would be the same for Powermac. Maybe on a live CD you should do it without the "sudo", because you ase the root user - maybe not.
So try any of the following:
```

sudo mkdir /media/harddrive
sudo mount /dev/hda1 /media/harddrive
```
```

mkdir /media/hda1
mount /dev/hda1 /media/hda1
```

---

### Post by menu on 2005-10-19
thank you for your quick and easy awnser.
I found this page:
[http://jclark.org/weblog/Miscellany/ubuntumount.html](http://jclark.org/weblog/Miscellany/ubuntumount.html)
and allmost stopped because of the page full of instructions and warnings.
your simple instructions where the key to understanding the page for me, thanks.

For other people trying to mount a disk using the ppc live cd:

I found the name of the partition i wanted to write to using the Ubuntu disks manager (drop down menu: system>administration>disks) it was hda3


Found the terminal (drop down menu: applications>acccessories>terminal)
There i typed

 sudo mkdir /mnt/macosxc

gave enter and typed

sudo mount -t hfsplus /dev/hda3 /mnt/macosx

then i found the partition using the file browser in filesystem/mount/macosx/
(drop down menu: applications>acccessories>filebrowser)

It works! Hope i do not mess up my disks now : )

(edit) whooops, it does not work, i cannot write to the disks "You do not have permissions to write to this folder." grr, the search continues.....

---

### Post by ds[de] on 2005-10-19
[QUOTE=menu](edit) whooops, it does not work, i cannot write to the disks "You do not have permissions to write to this folder." grr, the search continues.....[/QUOTE]

I might be wrong but I think harddrives are by default mounted with the ro (read-only) option.

Try 
sudo mount -t hfsplus **-o rw** /dev/hda3 /mnt/macosx

Regards,
ds[de]

---

### Post by Jenda on 2005-10-20
You're welcome. Unfoncho, that is all I can offer.

---

