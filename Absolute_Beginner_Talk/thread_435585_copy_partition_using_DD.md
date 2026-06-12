---
title: "copy partition using DD"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by justleen on 2007-05-07
Hey therre. 

I just bought a new laptop, and before i removed the preinstalled windows XP version, i wanted to make sure i woulndt have any unsupported hardware, and that everything worked OK.
So i created a 10 GB partition, and installed ubuntu on that. 
What do you know, everything works fine. 

So, i removed the main windows partition, repartitioned for / /home etc.
Since everything didnt work out of the box - like my widescreen resolution, i dont want to reinstall on the new partitions and reconfigure everything.
so i just want to copy my current install....

so my question...
can i simply do a 
```

dd if=/dev/sda3 of=/dev/sda6 bs=1024k  

```
to copy the whole partionm and afterwards edit the grub menu list to point to the right place?

Any advice would be more then welcome!

---

### Post by ubnewbie2 on 2007-05-07
I'll be interested in your answer too, but also, you might look at using a program called partimage.

---

### Post by justleen on 2007-05-07
at the moment, i just booted of the live cd, mounted my "new" and "old" partition on two directories.
After that, ran a ```
cp -var /oldpart/* /newpart/ 
```
copy the whole partition basicly.

edit fstab in /newpart/etc/ and grub in /newpart/boot/grub

im doing this at the moment, i'll let you know if it works..

---

### Post by justleen on 2007-05-07
right.. that worked. kind off..

what i've done (as said above):
- booted from the Live CD
- created two directories in /media: oldhdd and newhdd
- mounted /dev/sda3 on oldhdd
- mounted /dev/hda5 on newhdd
- copied everything over,-v for verbose output, -a leave permissions etc intact, -r recursivly```
 cp -var /oldhdd/* /newhdd/ 
```
- edit /media/newhdd/etc/fstab, correct the mountpoint for / (was /dev/sda3, must be /dev/sda5)

- edit /media/oldhdd/boot/grub/menu.list, added a new entry New Ubuntu for root(0,4) (copy paste your original one, add it at the bottom, and edit it)

This works. 
BUT!
i cant delete the old partition, since its now still reading the menu.list of this old partition.

How can i solve this? Reinstall grub to point to hda(0,4)?

---

### Post by steve.horsley on 2007-05-07
Well done on your progress so far. Since you now have Ubuntu running with the new root partition, running the command
**sudo grub-install /dev/sda**
should run the grub installer and configure grub to read the **current** /boot/grub/menu.lst which should do the trick. 

One word of warning though - at one point you mention having both sda and hda drives - I hope this is a typo. As far as I know, grub-install still gets confused when the machine has both IDE and SATA drives.

P.S. I would then introduce a small difference between the two menu.lst files, like changing a title or the colours, to prove which one was being used.

---

### Post by ubnewbie2 on 2007-05-07
> **steve.horsley said:**
> Well done on your progress so far. Since you now have Ubuntu running with the new root partition, running the command
**sudo grub-install /dev/sda**
should run the grub installer and configure grub to read the **current** /boot/grub/menu.lst which should do the trick. 

One word of warning though - at one point you mention having both sda and hda drives - I hope this is a typo. As far as I know, grub-install still gets confused when the machine has both IDE and SATA drives.

Don't know about grub-install, but grub itself is working fine here, with 1 IDE and 2 SATA drives.

---

### Post by steve.horsley on 2007-05-07
That's good to hear. But I know that in the past, the grub installer installed grub and configured it to look on the wrong disk for menu.lst. Frexample, if you have hda and sda, which one is drive 0? And what drive number was the other one? I do wonder if this confusion might be why even IDE drives now get called /dev/sd* in Feisty.

---

### Post by justleen on 2007-05-07
Thnx Steve!, i'll give that a go now..

And yes, its a typo.. brand new laptop, so i'm in "my normal pc"-mode, which is hda :)

---

### Post by justleen on 2007-05-07
That worked! great, thnx.

I did make one mistake though, in the menu.list i didnt change the root=UUID=whatever
so, my olddrive would still be root...

after changing that to root=/dev/sda5, rebooting (and selecting my new entry), the / was mounted correctly on sda5.
sudo grub-install /dev/sda to finish off...  Thanks very much for the help!

---

