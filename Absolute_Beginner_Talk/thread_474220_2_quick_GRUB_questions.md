---
title: "2 quick GRUB questions"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by mynameisbill on 2007-06-14
Firstly, I've already changed it so it boots to XP and not Ubuntu. However, I was wondering whether there was a way to switch how they look on the GRUB menu. Want to make sure I do it right rather then me cutting and pasting them and not being able to boot when I restart lol

Also, I have like 6 or 7 different Ubuntu options on the menu. Is there any way I can remove most of them from the list? Can I just use # and comment them out?

Thanks!

---

### Post by Inxsible on 2007-06-14
> **mynameisbill said:**
> Firstly, I've already changed it so it boots to XP and not Ubuntu. However, I was wondering whether there was a way to switch how they look on the GRUB menu. Want to make sure I do it right rather then me cutting and pasting them and not being able to boot when I restart lol

Also, I have like 6 or 7 different Ubuntu options on the menu. Is there any way I can remove most of them from the list? Can I just use # and comment them out?

Thanks!
could you post your /boot/grub/menu.lst 

```
gksudo gedit /boot/grub/menu.lst
```

You can definitely remove some Ubuntu entries but i would advise you to keep atleast one older and stabler kernel just in case the new one gives you problems.

Post your menu.lst and we can help you out if you want to remove some of those entries.

---

### Post by mynameisbill on 2007-06-14
If at all possible, I'd like to remove the bottom 3 Ubuntus' and the NT/2000/XP. Thanks!

```
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=ca0683bd-9ca3-4fb8-b333-4e7eaf9844c5 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=ca0683bd-9ca3-4fb8-b333-4e7eaf9844c5 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=ca0683bd-9ca3-4fb8-b333-4e7eaf9844c5 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=ca0683bd-9ca3-4fb8-b333-4e7eaf9844c5 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

---

### Post by drs305 on 2007-06-14
The 'safest' way to remove them would be to just comment them out. The ones you mentioned -15, -15 recovery, and memtest are safe to comment out and you can always get them back if you need them. Same with NT.

---

### Post by Inxsible on 2007-06-14
You only have two entries for Ubuntu. The recovery mode is helpful if at all you have problems.

I would recommend against removing the -15 kernel.

But if you still want to uninstall it. Go to Synaptic Package Manager and search for  "kernel 2.6.20-15" without quotes. There will be 3 packages which are installed...remove all 3 and your menu.lst will be updated accordingly.

About your Windows XP/NT/2000.........you should not remove the entry just like that. Its a complete OS there. that partition will be unusable if you remove this entry. If you have no use for it, you can format it and use the space for something else like an extra partition in Linux or in windows.

---

### Post by Inxsible on 2007-06-14
> **drs305 said:**
> The 'safest' way to remove them would be to just comment them out. The ones you mentioned -15, -15 recovery, and memtest are safe to comment out and you can always get them back if you need them. Same with NT.

Commenting them in the menu.lst does NOT remove the kernel. It just doesnt show you on the menu when you try to boot from the grub.

---

### Post by drs305 on 2007-06-14
Inxsible,

Are you saying it would not be good to comment them out either? I don't see the harm in that but I don't have near the experience with ubuntu as with other systems. I uncomment things, leave them that way until the next kernel, then REMOVE them as you mention with synaptic and tidy up menu.lst. Is doing it that way going to give me problems? I just don't like seeing all those menu items during boot...

---

### Post by mynameisbill on 2007-06-14
Yeah, I don't necessarily want them removed. I just want them off GRUB when I boot up so it doesn't look so messy. Commenting them out worked great. Thanks!

Not to be picky, but is there any way I can move XP over Ubuntu so XP is at the top and all the Ubuntu are below it?

---

### Post by Inxsible on 2007-06-14
> **drs305 said:**
> Inxsible,

Are you saying it would not be good to comment them out either? I don't see the harm in that but I don't have near the experience with ubuntu as with other systems. I uncomment things, leave them that way until the next kernel, then REMOVE them as you mention with synaptic and tidy up menu.lst. Is doing it that way going to give me problems? I just don't like seeing all those menu items during boot...

Oh yeah...commenting is definitely not bad at all.  All I wanted to say was that it wont un-install it from your machine.

---

### Post by Inxsible on 2007-06-14
> **mynameisbill said:**
> Yeah, I don't necessarily want them removed. I just want them off GRUB when I boot up so it doesn't look so messy. Commenting them out worked great. Thanks!

Not to be picky, but is there any way I can move XP over Ubuntu so XP is at the top and all the Ubuntu are below it?

Well then you can simply comment them off. Although I dont see the point of commenting the Windows NT/2000/XP since you will not be able to log into it. and if you dont intend to use it,,why not nuke it completely and use the space for Linux.

Sorry...I try to nuke everything Windows (as much as I can) ;)

---

### Post by Inxsible on 2007-06-14
> **mynameisbill said:**
> Yeah, I don't necessarily want them removed. I just want them off GRUB when I boot up so it doesn't look so messy. Commenting them out worked great. Thanks!

Not to be picky, but is there any way I can move XP over Ubuntu so XP is at the top and all the Ubuntu are below it?

Move up XP -- just in the menu.lst or do you want to make XP the default OS which will be highlighted and logged into if no key is pressed ?

---

### Post by drs305 on 2007-06-14
> **mynameisbill said:**
> Not to be picky, but is there any way I can move XP over Ubuntu so XP is at the top and all the Ubuntu are below it?

You can move what you SEE by simply moving the entire section up or down in the order by editing menu.lst (moving the entire section of 4-6 lines normally). You would then change the default BOOT by changing the ' default 0 ' line so that the number equals the one you want to boot. The order you see them doesn't affect which one boots.

The number starts with the first uncommented title being 0. So if the 3rd title was the one you wanted to boot, you would change the line to:   default 2

---

### Post by kittyhawk63 on 2007-06-14
(note: I changed the default line to read Windows XP.)

You can move the lines for Windows XP just above the line where it says ### **BEGIN AUTOMAGIC KERNELS LIST**: Now Windows XP will default to start automatically unless you move to the next line with your down arrow key on the keyboard. My next line says **Feisty Fawn 7.04**.

Below is my entry:

[COLOR=Red] # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title        Windows XP
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

### **BEGIN AUTOMAGIC KERNELS LIST**
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below
[/COLOR]  
(con't)

---

