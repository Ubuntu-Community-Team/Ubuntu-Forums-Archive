---
title: "Having some trouble with  the GRUB Bootloader"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by Captain Jack on 2007-12-28
Okay, so I am having some trouble getting the GRUB bootloader to work with a second hard drive I have installed on my system. I have the Mac Operating system Tiger on a completely different hard drive than what I have Ubuntu on. I got into the menu.lst file and I don't know what to put in for root. I keep guessing things like hda1 or sda1 but it is not working for me. Any ideas?

---

### Post by mejy on 2007-12-28
Is this an intel mac or a PPC mac?  Also, why do you need to edit this by hand?  Regardless, if you're sure everything else is right the root should be in the format
```
(hd1,0)
```
"1" is the zero based index of the harddisk, and "0" is the zero based index of the partition.
If you post the output of "diskutil list" in tiger and the contents of your menu.lst configuration I may be able to give you more help.

---

### Post by Captain Jack on 2007-12-29
> **mejy said:**
> Is this an intel mac or a PPC mac?  Also, why do you need to edit this by hand?  Regardless, if you're sure everything else is right the root should be in the format
```
(hd1,0)
```
"1" is the zero based index of the harddisk, and "0" is the zero based index of the partition.
If you post the output of "diskutil list" in tiger and the contents of your menu.lst configuration I may be able to give you more help.

This would be an "other" mac if you catch my drift. I am not aware of another way to edit the GRUB bootloader. I will post the output of diskutil list and the contents of my menu.lst config tonight. Thanks for your help!

---

