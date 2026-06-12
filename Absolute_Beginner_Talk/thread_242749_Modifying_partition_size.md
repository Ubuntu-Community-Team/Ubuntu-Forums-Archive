---
title: "Modifying partition size"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by Bungee on 2006-08-24
I've installed Ubuntu on a desktop machine and allowed the installation to automatically create and size the partition. Now I would like to do two things - mostly at the request of those who need the winows partition until I get this install humming along.

1/ How do I resize the Ubuntu partition?

2/ How do I make XP the default on start-up rather than Ubuntu.

If you think that someone asking those sort of questions shouldn't be doing this install, then you are probably right. :oops:

---

### Post by seshomaru samma on 2006-08-24
To resize Ubuntu 
You need a programme called Gparted
Applications -> System Tools -> GParted
it is a graphical tool and pretty easy to understand

after you install Windows it will overwrite your MBR which means you will not be able to access Linux. You will need to reinstall Linux' bootloader called Grub. Please use the search function in the forum to find many posts about how to reinstall grub
Finally to make Windows the defualt OS you will need to edit Grub (after reinstalling it)
in the terminal put :
```
sudo gedit /boot/grub/menu.lst
```
a new documnet will appear
look for a line like this:
```
default=2
```
the number in your Grub file might be different
you will have to change the number
how will you know to which number :
look at the bottom of the document and you will see all the boot options , each boot option begins with the word 'title' , the last option should be windows . count all the options up (the first one counts as zero not one) and change the default number to whatever number windows is.

Edit :sorry , I can see that my explenation is not very clear, if it doesn't make sense I will try to find a better guide for you.

---

### Post by Bungee on 2006-08-24
I should have clarified that XP is already installed on the other partition, I just need to decrease the size of the Ubuntu partition. If I reinstall XP then don't I risk losing everything in that partition as well?

---

### Post by UbuntuKhan on 2006-08-24
1. To resize your already installed Linux partition you need a repartitioning tool like, for example, GParted. You can even use the GParted Live Cd for that. It's easy to use.
2. For this question you can find an answer easy if you use search, but here it is:
Edit the Grub menu list (you can use whatever text editor you like instead of gedit):
"sudo gedit /boot/grub/menu.lst"
In the file that opens you will find a line which is saying:
"..... 
default 0
..."

Now this means that the Grub loader will start by default with the first entry in the list of OS. You have to change that number in order to match Win number in the list. You can do that by counting the entries further down in the Grub file after the line 
"## ## End Default Options ##"
that have this form (remember that the first entry is  0, next one is 1 and so on..):
"
title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda8 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot
"

You have to count in fact the number of words "title" in that file.
Example: For me Win 98 is 8-th entry (counting from 0 of course):

"
## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda8 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda8 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-25-386
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hda8 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hda8 ro single
initrd		/boot/initrd.img-2.6.15-25-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda8 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda8 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows 95/98/Me
root		(hd0,0)
savedefault
makeactive
chainloader	+1"

---

### Post by UbuntuKhan on 2006-08-24
Sorry

---

### Post by UbuntuKhan on 2006-08-24
Sorry for the double post.
If You install Win XP again without reformatting the disk you won't affect the Linux partition because win cannot see it, but you will have to reinstall Grub.

---

