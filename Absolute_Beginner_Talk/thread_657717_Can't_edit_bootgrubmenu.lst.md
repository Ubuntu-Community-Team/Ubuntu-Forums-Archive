---
title: "Can't edit /boot/grub/menu.lst"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by lionman on 2008-01-03
I am having a problem where the bios of my VAIO is too old, and ubuntu says I need to set acpi=force.  I searched the forums and found that this change belongs in th e/boog/grub/menu.lst file. 

But when I try to edit the file to add the required parameter, I can't save it out. It's read-only. No problem, I told myself. Being a former C programmer under BSD unix, I figured I'd just chmod the offending file and be on my way. But I cant. It says: chmod: changing permissionf of 'menu.lst': operation nto permitted.

So how does one for about editing this file?

---

### Post by Xavieran on 2008-01-03
You need to be sudo to do that...
sudo chmod -youroptions

---

### Post by lionman on 2008-01-03
Ah, my old friend sudo. Don't think I'll ever get used to that.

Thanks!

---

### Post by mikewhatever on 2008-01-03
It is read only because menu.lst is a system file. To open it for editing use the following command, <gksudo gedit /boot/grub/menu.lst>.

I would not recommend Xavieran's advice unless you really know what chmod does.

---

### Post by Xavieran on 2008-01-03
> **lionman said:**
> 
But when I try to edit the file to add the required parameter, I can't save it out. It's read-only. No problem, I told myself. Being a former C programmer under BSD unix, I figured I'd just chmod the offending file and be on my way. But I cant. It says: chmod: changing permissionf of 'menu.lst': operation nto permitted.

He said he wanted to know why chmodding wouldn't work...I was just showing hime that he needed sudo...

---

### Post by ryanVickers on 2008-01-03
> **lionman said:**
> ... belongs in th e/boog/grub/menu.lst file. ...

e /boog/grub? :p /boot/grub/... maybe? anyways, yes, you just need gksudo gedit /boot/grub/menu.lst

---

### Post by mikewhatever on 2008-01-04
> **Xavieran said:**
> He said he wanted to know why chmodding wouldn't work...I was just showing hime that he needed sudo...

I thought the OP wanted to edit his menu.lst. No hard feelings, Xavieran, but chmoding would be a bad way to edit a simple text file.

---

