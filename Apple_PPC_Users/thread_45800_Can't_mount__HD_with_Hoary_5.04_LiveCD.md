---
title: "Can't mount  HD with Hoary 5.04 LiveCD"
date: 2005-07-01
forum: Apple PPC Users
---

### Post by Akatum on 2005-07-01
I've just tried Hoary 5.04 PPC Live CD on iMac and iBook with OS9. It worked fine. But I can't see my hard disk (with data). 

At first I tried:  

fdisk /dev/hda  ; with "P" command

and from the results I guessed that I have to do this:

mount /dev/hda9  /mnt/my data

it works, but without any data on that directory.

Well....I'm not a Mac guy but need to recover that data immediately. So if anyone can guide me how to solve this problem pls tell me. Thanks.

---

### Post by colinhayes on 2005-07-03
some things that come to mind:

is this an ext3 formatted drive or an HFS one?  If HFS, can Linux properly read HFS drives?  It seems to me that they wouldn't be able to.

also, /mnt/my data is likely a bad filepath.  you did mkdir, yes? do it with mydata or my_data, unix and linux don't care for spaces too much.

---

### Post by Akatum on 2005-07-03
[QUOTE=colinhayes]some things that come to mind:

is this an ext3 formatted drive or an HFS one?  If HFS, can Linux properly read HFS drives?  It seems to me that they wouldn't be able to.

also, /mnt/my data is likely a bad filepath.  you did mkdir, yes? do it with mydata or my_data, unix and linux don't care for spaces too much.[/QUOTE]

Hi Colinhayes,
                           I did mkdir /mnt/<something> . And when I do   fdisk /dev/hda , after I do mount /dev/hda9  /mnt/<something>, it says that  /dev/hda9  (where my documents are) is "Apple_HFS" type and "HFS" system
                           But when I do "mount", it says:

               /dev/hda9   on   /mnt/<something>  type  ext2 (rw)
                     
                           and inside  /mnt/<something>  there is "lost+found" folder without any document in it.
                           If Linux can't read HFS (I'm also afraid that too), what should I do? I'm gonna try "Niktarix" Linux, as "Knoppix PPC" didn't run on my iMac and "Gentoo PPC" is too complicated for me this time. 
                           BTW thanks for your reply.

---

### Post by pvz on 2005-07-03
Did you try specifying the file type? You could try to mount it with
mount **-t hfs** /dev/hda9 /mnt/<something>

---

