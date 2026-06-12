---
title: "Grub error 5"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by endlessurf on 2008-03-04
My grub disappeared from me awhile back ago and all I could load was windozer.  So for fun I found an Ubuntu Edgy lying around the house and threw that in and decided to see what would happen if I reformatted the swap (all the partitions were there, just no grub).  I reformatted the swap using the edgy cd even though I am running fawn ( why you may ask.....I was bored and lack cable tv).  Needless to say when I rebooted I got an error, "Error 5".

I then threw in my windozer cd and did a fixmbr and i could use windozer again.  I downloaded a fiesty fawn iso and burnt that to a cd and threw it into the computer.  I tried to reformat the swap, but it would not let me.  

So I then did this whole process:  
sudo grub
find /boot/grub/stage1
root (hd?,?)
setup (hd0)
quit

and all the comments at the end of the line confirmed everything loaded correctly.  I shutdown and restart and I get the same error.  Do I need to delete my swap and reformat it or do I have other issues????  Keep in mind when i use windozer fixmbr i can still access windozer.

---

### Post by glennric on 2008-03-04
I am not sure why you are reformatting swap?  It is actually possible to boot ubuntu without any swap, although it is recommended that you have swap.  As to your grub issues, when you run "sudo grub" what do you get back when you do "find /boot/grub/stage1"?

---

### Post by endlessurf on 2008-03-04
something like hd(0,6)

---

### Post by glennric on 2008-03-04
I assume that is what you are typing then instead of the question marks in "root (hd?,?)"?  Just checking.

---

### Post by endlessurf on 2008-03-04
yup

---

### Post by glennric on 2008-03-04
You might try booting a live cd and checking that your linux partitions mount ok and all of the data appears to be there, in particular the boot directory and the file /boot/grub/menu.lst.

---

### Post by glennric on 2008-03-04
By the way, grub error 5 means a partition table is invalid or corrupt.

---

### Post by endlessurf on 2008-03-04
i did that and everything looked ok

---

### Post by glennric on 2008-03-04
You may need to try to use testdisk to recover the partition table on the disk.

---

### Post by endlessurf on 2008-03-04
I'll try that will post in a few

---

### Post by glennric on 2008-03-04
You may have to do a little research to figure out how to use the information testdisk gives you.  I have to go now, but maybe someone else can help you.

---

