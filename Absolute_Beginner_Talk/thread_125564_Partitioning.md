---
title: "Partitioning"
date: 2006-02-04
forum: Absolute Beginner Talk
---

### Post by lgmdaniel on 2006-02-04
So how do a remove a partition and then expand the current one?
Plus I would also like to increase my swap file.

---

### Post by ctt1wbw on 2006-02-04
GParted or QTparted might do the job...  I think...

---

### Post by lgmdaniel on 2006-02-04
They all work just fine.. but I can't edit the current ext3 partition and move/resize. How would I go about doing this?

---

### Post by jimrz on 2006-02-04
GParted will not work on your current OS partition, but if you use the 'live cd' (loads only in RAM) then you will be able to use GParted on the partitions installed on your hd

---

### Post by lgmdaniel on 2006-02-04
I did think about this.. but does not GParted have to be installed? Will this work with the Live CD?

---

### Post by Greg2 on 2006-02-04
[QUOTE=lgmdaniel]I did think about this.. but does not GParted have to be installed? Will this work with the Live CD?[/QUOTE]
GParted will work from the live CD without installing.

---

### Post by taurus on 2006-02-04
If it's on the LiveCD, then you can run it directly from the CD.  No need to install anything...

---

### Post by lgmdaniel on 2006-02-06
you are correct, but anoyingly it won't let me move the partition. Strange.
I was thinking about using the copy partition option but then how would I get the system to boot off the right partition?

---

### Post by lgmdaniel on 2006-02-07
bump.. anyone?

---

### Post by munga_bill on 2006-02-07
[/QUOTE]So how do a remove a partition and then expand the current one?
 Plus I would also like to increase my swap file.> 
[QUOTE]GParted will work from the live CD without installing.
> you are correct, but anoyingly it won't let me move the partition. Strange.
 I was thinking about using the copy partition option but then how would I get the system to boot off the right partition?
You can just copy the partition and paste it to an equal sized or larger free space on the disk, and then if you do that it will probably have a different partition number. Then I think you have to edit /etc/fstab on maybe re-install grub.

If you want to do it without changing you partition numbers, check this thread for a neat way to do things.[http://ubuntuforums.org/showthread.php?t=125644]("http://ubuntuforums.org/showthread.php?t=125644")

---

### Post by cotcot on 2006-02-07
You could try with parted (command line). There is a good GNU Parted manual with examples to show some limitations : [http://www.gnu.org/software/parted/manual/](http://www.gnu.org/software/parted/manual/)

---

### Post by lgmdaniel on 2006-02-07
[QUOTE=munga_bill][/QUOTE]So how do a remove a partition and then expand the current one?
 Plus I would also like to increase my swap file.> 


You can just copy the partition and paste it to an equal sized or larger free space on the disk, and then if you do that it will probably have a different partition number. Then I think you have to edit /etc/fstab on maybe re-install grub.

If you want to do it without changing you partition numbers, check this thread for a neat way to do things.[http://ubuntuforums.org/showthread.php?t=125644]("http://ubuntuforums.org/showthread.php?t=125644")

I'll give it a go.. but it does look rather mental.. I think I'll wait till I move the windows partition on to another drive.

---

### Post by lgmdaniel on 2006-02-07
[QUOTE=cotcot]You could try with parted (command line). There is a good GNU Parted manual with examples to show some limitations : [http://www.gnu.org/software/parted/manual/](http://www.gnu.org/software/parted/manual/)[/QUOTE]

I'll also give this a try..

---

### Post by pelle.k on 2006-02-07
You do know, you have to >>unmount<< the partition you are trying to edit right?

---

### Post by lgmdaniel on 2006-02-07
[QUOTE=pelle.k]You do know, you have to >>unmount<< the partition you are trying to edit right?[/QUOTE]

yep.. thats why I'm booting off the live CD. I'm trying to get around the problem of not being able to move the partition. Though I think parted should fix that, so once my windows partition is gone to the other disk then I'll be giving it a go. (after a backup)

---

