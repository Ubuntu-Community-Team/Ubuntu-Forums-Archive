---
title: "puppy on hard drive"
date: 2013-08-08
forum: Any Other OS
---

### Post by d-vineet on 2013-08-08
I wish to install puppy linux on hard drive instead of booting everytime from USB or CD (I don't want to run it from RAM).    
Is the installation procedure very cumbersome?  
Has anyone tried installing it on hard drive? If so, kindly share the do's & don'ts.  
Secondly, whether it is possible to use the ubuntu repositories for puppy?  
Can WINE be installed on puppy?  

Thanks,  

Vineet

---

### Post by sudodus on 2013-08-08
I boot Puppy Wary 5.3 from its iso file with persistence. It is managed via the following menuentry in
[B][FONT=courier new]
/etc/grub.d/40_custom[/FONT][/B]

```
[COLOR=#696969]#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.[/COLOR]

menuentry "Puppy Linux 5.3 frugal in [COLOR=#ff0000]/media/multimed-2/wary5.3frugal[/COLOR]" --class gnu-linux --class gnu --class os {
        insmod part_msdos
        insmod ext2
        set root='([COLOR=#ff0000]/dev/sda,msdos2[/COLOR])'
        search --no-floppy --fs-uuid --set=root [COLOR=#ff0000]d3f3f4a3-3d6e-4e4f-8e1a-c2f0de792f90[/COLOR]
        linux [COLOR=#ff0000]/wary5.3frugal[/COLOR]/vmlinuz pmedia=atahd psubdir=[COLOR=#ff0000]wary5.3frugal[/COLOR]
        initrd [COLOR=#ff0000]/wary5.3frugal[/COLOR]/initrd.gz
}
```

***Adjust it to fit your hard disk drive*** and its partition table and file systems. Run ```
sudo update-grub
``` to make the menuentry appear in **[FONT=courier new]/boot/grub/grub.cfg[/FONT]** and be active at next boot.

I have no reply to the other questions.

---

### Post by d-vineet on 2013-08-08
Thanks for your reply.
So I need to put > linux /wary5.3frugal/vmlinuz pmedia=**"NAME OF MY HARD DRIVE"** psubdir=wary5.3frugal  

Is that correct? What other modifications are required in the code given by you? I am new to Linux.
Appreciate if you can post a code snippet with dummy values (where I need to put in the correct values)


Thanks again,
Vineet

---

### Post by sudodus on 2013-08-08
I made the part of the code [COLOR=#ff0000]***red***[/COLOR], that you should probably adjust to fit your hard disk drive. The first change is only decorative (what is shown in the grub menu), but the other changes are important and should indicate where you have your Puppy and its persistent file.

You may have to change something else depending on the version of Puppy. This works for Puppy Wary 5.3.

pmedia is rather ***type of media*** (not name of hard drive). I don't think you need to change that. The drive and partition IDs are stored in the variable [FONT=courier new]**root**[/FONT].

---

### Post by slw210 on 2013-08-08
An install is pretty straight forward on Puppy, just select install and answer the questions. 

Which Puppy?

[**Hard Puppy**]("http://puppylinux.org/wikka/InstallationFullHDD") and [**Puppy on Hard Drive**]("http://www.puppylinux.com/hard-puppy.htm")

[**Wine on Puppy**]("http://murga-linux.com/puppy/viewtopic.php?t=53675&start=405")

---

### Post by Frogs Hair on 2013-08-08
***Moved to O/OS Distro Support***

---

### Post by d-vineet on 2013-08-10
Thanks all for your replies.
Let me try it out.

--- Vineet

---

