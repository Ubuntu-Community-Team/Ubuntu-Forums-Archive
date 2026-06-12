---
title: "partition labels. (hd0,0) etc"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by Dodelijk on 2008-01-11
Hello, 

Could somebody point out the syntax for labeling partitions for grub? 
for example what do the two zeros mean in (hd0,0). 
I have a disk with an extended partition and inside this i have a two partitions. 
How would i refer to the first of these partitions? Would it be (hd1,0)?

Thanks...

---

### Post by stump138 on 2008-01-11
hd(x,y) where x=hard drive # and y=partition

so in your case the the drives would be hd(0,0) and hd(0,1)

---

### Post by PeterJS on 2008-01-11
Grub numbering goes like this: The first number refers to the physical disk so (hd0) is the first physical disk. The second number is the partition number, so (hd0,0) is the first partition of the first disk. Now for the extended partitions with out knowing the exact layout I can't give you exact numbers, but the extended partition does count in the numbering so your first logical partition couldn't be any lower than hd(0,2).

Furthermore the numbering on the partitions isn't just a matter of counting them up, but is based on their numbering in the partition table, for example I have 4 partitions numbered (in order) 0,2,5, and 4 (yeah I kinda messed that part of the install up, but it works!). 0 is a physical partition that has windows on it, 2 is a physical partition that contains 5&4. 5 is the logical partition that has / on it, and 4 is the logical partition that has swap on it.

But don't worry most cases are far easier to work with. To get a good graphical look at your disks you can use gparted, but know that a translates to 0, b > 1, etc, for the hard drive number, and for the partition number gparted starts counting at 1 instead of 0, so you need to subtract 1 to get the number you're looking for.

---

### Post by Dodelijk on 2008-01-11
Hello Thanks fr the replies.

Here's how my disk is laid out in gparted:

/dev/hda1 ext3 
/dev/hda3 swap
/dev/hda2 extended 
      /dev/hda5 ntfs    -  windows
unallocated 

so in this case would the windows partition be labeled hd0,4 ? 

and would the corresponding grub entry be 

title Windows XP. 
root hd0,4

or do i need to add something else? 

thanks..

---

### Post by PeterJS on 2008-01-11
Getting close. You need parenthasis for your hd entry > (hd0,4).

and you're missing a couple elements
```

map (hd0,4) (hd0,0)
map (hd0,0) (hd0,4)
makeactive
chainloader	+1

```
Windows get's really upset when it's not on (hd0,0) so we need to swap those around before booting it, and the makeactive and chainload are what pass the actual control off to ntldr.

---

### Post by Drakkor on 2008-01-11
My grub menu is like this:
title		Windows XP Home
root		(hd0,1)
makeactive
chainloader	+1      

 :)

---

### Post by Dodelijk on 2008-01-11
Hello, 


Thanks for the help. Unfortunately it didn't work. 

When i selected windows from the grub menu it threw "Error 12: Invalid device requested"

What to do?

BTW this is what i am using :

title 		Windows XP. Fr
root 		(hd0,4)
map (hd0,4) (hd0,0)
map (hd0,0) (hd0,4)
makeactive
chainloader	+1


Do i need to remove the second 'map' line. It seems to do the reverse of the former line...

---

### Post by Drakkor on 2008-01-11
I would try it like mine above,with the exeption of root (hd0,1) make it (hd0,4)
and get rid of the map lines

---

### Post by Dodelijk on 2008-01-11
Hello, 

Sorry Drakkor  i didn't mention it. I did try your example and and I got the "Error 12" message aswell. 

It's really irritating now. Is'nt it anything to do with the extended partition? I'm not sure how that would affect it though

Another thing that's a bit weird is that when grub loads it tells me to press Esc if i want to see the manu otherwise it boots Ubuntu giving 
me only 3 seconds to press Esc. I'm not sure if this can be changed 

cheers.

---

### Post by Drakkor on 2008-01-11
If you have the XP disk, I would boot from it,then go into the recovery mode and type in
```
fixmbr
```
which will of course wipe out grub,then boot from the Ubuntu live cd and reinstall grub,which should then detect your windows partition

---

### Post by Dodelijk on 2008-01-11
Good idea. 

I'll have a go in a bit. Thanks

---

