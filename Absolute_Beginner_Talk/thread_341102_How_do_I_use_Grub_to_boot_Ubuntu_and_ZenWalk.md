---
title: "How do I use Grub to boot Ubuntu and ZenWalk"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by Tweedicus on 2007-01-18
Hi,

I've recently installed Zenwalk Linux OS on my laptop because it's a little easier on my poor eyes for Word Processing.

I booted of a Gparted live cd, repartitioned my HD giving over 5gb to ZenWalk. Everything went smoothly.

I booted up into Edgy just to make sure it was still there. It is my sole OS, I don't have XP.

Then I installed ZenWalk onto the new 5 gb partition, again no problems.

However, I did not install Lilo, the default boot manager with Zenwalk, as recommended not to by ZenWalk. This was so Grub is left on my system as the sole boot manager.

So far so good. Install finished I rebooted expecting to see Grub give me choice like it does when dual booting into XP. 

It didn't it booted straight into Edgy.

I checked Gparted in Edgy and my partitions are set up correctly with ZenWalk on the 5 gb section. 

How do I make my system kick in Grub so I have a choice of which OS to boot into. BTW there's no 'crisis'. Edgy is working just fine and all my data is there.

Thanks.

Tweed.

---

### Post by louieb on 2007-01-18
No problem. It just a matter of adding a ZenWalk entry in Ubuntu's /boot/grub/menu.lst. 
The entry will look a lot like the one for Ubuntu.
Just make a copy of the Ubuntu entry
change root, kernel and initrd to point to ZenWalk. (look in the /boot directory of you ZenWalk installation for kernel and initrd file names).

For more info look at the Dual Boot link in my signature.

---

### Post by Tweedicus on 2007-01-18
Hi,

I use Edgy but also have Zenwalk on a separate partition on the same HD. I put on Zenwalk after Edgy. I've been have problems dual-booting because Grub doesn't see ZenWalk. Edgy works fine, so any alterations I make have to be from within Edgy.

The solution seems to be:

[B]Grub

So, if you want grub to start Zenwalk with a 1280x1024@16bit framebuffer bootsplash use settings like these in boot/grub/grub.conf:

# Zenwalk Linux
title Zenwalk Linux [/boot/vmlinuz + /boot/initrd.splash, /dev/sdb6]
root (hd2,5)
kernel (hd2,5)/boot/vmlinuz root=/dev/sdb6 vga=0x31A video=vesafb:mtrr,ywrap splash=silent
initrd (hd2,5)/boot/initrd.splash[/B]


Could someone please tell me what to do with this as I'm not sure where I have to copy and paste it or what it means.

2.) In the above there is (hd2,5) does this refer to partitions and will I have to alter it on my system. For example, this is my current set up:

/dev/hda1 ext 3 has Ubuntu on
/dev/hda3 ext 3 has ZenWalk
/dev/hda2 is extended and also has within it /dev/hda5 linux-swap.

Thank you,

Tweed.

---

### Post by Tomosaur on 2007-01-18
Yes, you will need to change the hd(2,5) for your system. You appear to have 3 partitions. Grub counts from zero, so partition 1 is 0, 2 is 1, etc etc. Since you have the one hard drive, and zenwalk is on partition 3, you should use hd(0,2)

Ubuntu does not use the grub.conf file, but here's what you'll have to do anyway:

Click Applications > Accessories > Terminal
Type:
```

gksudo gedit /boot/grub/menu.lst

```
Type in your password in the box which shows up, then a text editor with the correct file will open. Scroll to the bottom, and paste this in:
```

# Zenwalk Linux
title Zenwalk Linux
root (hd0,2)
kernel (hd0,2)/boot/vmlinuz root=/dev/hda3 vga=0x31A video=vesafb:mtrr,ywrap splash=silent
initrd (hd0,2)/boot/initrd.splash

```

Save and exit. Next time you reboot, you should be able to boot into zenwalk. If it doesn't work, come back here and we'll see what we can do :)

---

### Post by Tweedicus on 2007-01-18
Thank you for getting back to me.

Could you just walk me through your instructions a little. I didn't really understand some of the terms: i.e. how do I enter into Ubuntu's /boot/grub/menu.lst.

I tried gksudo nautilus then entered /boot/grup/menu.lst

but got could not display item is not a folder.

Thanks

---

### Post by jvc26 on 2007-01-18
Thats because the command is:
```

gksudo gedit /boot/grub/menu.lst

```

Its the config file for the GRUB Bootloader its not a folder. As tomosaur instructed you, go to that file, scroll to the bottom and paste in:
```

# Zenwalk Linux
title Zenwalk Linux
root (hd0,2)
kernel (hd0,2)/boot/vmlinuz root=/dev/hda3 vga=0x31A video=vesafb:mtrr,ywrap splash=silent
initrd (hd0,2)/boot/initrd.splash

```

That should work now :)
Il

---

### Post by Tomosaur on 2007-01-18
No, you need to click Applications, then Accessories, then Terminal. Once the terminal appears, you need to type into that:
```

gksudo gedit /boot/grub/menu.lst

```

---

### Post by Tweedicus on 2007-01-18
Sorry our posts clashed and went out at the same time before I saw Thomasaurs.

Anyway thanks guys. I've just rebooted, which is why I wasn't answered, and ZenWalk has appeared on the menu, and I can boot into it.

Cheers,

Tweed.

---

### Post by Tweedicus on 2007-01-18
BTW is there anything in that code which alters the size of the splash screen as it's all over the place at the moment, and I can't see everything I'm meant to see. It's not aligned on my monitor correctly.

Thanks.

---

### Post by Tomosaur on 2007-01-18
Yes that code does specify some splash dimensions. Try replacing the stuff you pasted in before with this:
```

# Zenwalk Linux
title Zenwalk Linux
root (hd0,2)
kernel (hd0,2)/boot/vmlinuz root=/dev/hda3 ro quiet splash
initrd (hd0,2)/boot/initrd.splash

```

---

### Post by Tweedicus on 2007-01-18
Thank you again Tomosaur. The instructions worked like a dream. I'm now up and running.

You're to be commended on the quality of your instructions. They were pitched at the right level for someone who is still learning.

Thanks.

Tweed

---

