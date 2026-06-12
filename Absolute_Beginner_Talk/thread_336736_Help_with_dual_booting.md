---
title: "Help with dual booting"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by Helgeland on 2007-01-12
I have partitioned my harddrive (320 gb) to have winxp on a 160gb partition ubuntu on the rest <and i made swap and /home partitions> but now when i start up my computer if i dont scroll down to windows xp os my comp. automatically boots into ubuntu... how can i keep windows xp on the top of that list so that it is my default os instead of ubuntu?

---

### Post by netadptr0719 on 2007-01-12
If you go to
/boot/grub/menu.lst
you can change the order of the grub menu when you start up and just put windows up at the top and you're good to go.

---

### Post by tonyr1988 on 2007-01-12
Yup, but note that you'll need superuser privileges to edit menu.lst. Open a Terminal (Applications -> Accessories -> Terminal) and type:

> sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup

It will want your user password. Then type:

> gksudo gedit /boot/grub/menu.lst

It may want your user password again - no worries either way. Then scroll down the file (ignore all the lines beginning with #). You'll notice a list of the items on your grub menu (what shows up when you boot your computer). Feel free to move them around...*but* make sure you move them as entire "blocks," not just the first line. An entire block would be something like this (there will be a blank line before and after it):

> title           Ubuntu, kernel 2.6.17-10-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro quiet splash noapic nolapic ide=nodma
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

Hope it makes sense. If not, the first thing you did (sudo cp...) made a backup of that file, in case something goes wrong.

---

### Post by netadptr0719 on 2007-01-12
Haha, I've never done back-up files, ever, and I have payed the price for it more that enough times. You think I would have figured it out by now rather than passing on my bad habits to others.

---

### Post by tonyr1988 on 2007-01-12
lol, it's always important that when you edit any "system file" to make a backup. Backups of my xorg.conf has saved me numerous times.

If you make a typo, or do something *completely* wrong, you can always go back and restore the backup with (in this case):

> sudo cp /boot/grub/menu.lst.backup /boot/grub/menu.lst

Even if you mess it up to the point that you can't boot into your computer, you can load the Ubuntu LiveCD (or SLAX LiveCD, or Knoppix LiveCD, or DSL LiveCD, etc.) and enter that into the terminal.

---

### Post by Helgeland on 2007-01-12
thanks alot guys, i love these forums- i dont have to wait for answers, and ppl dont make me feel like a retard lol. now i just have to figure out how to install the drivers for my wireless card? any help there... i'm trying to install "gigabyte technology aircruiser g desktop adapter"

---

### Post by logos34 on 2007-01-12
Windows is last for a reason....It is a piece of garbage and belongs at the bottom.  ;-)

Backing up your menu.lst is a good point, but as far as pasting the windows entry ahead of ubuntu goes won't Grub just delete it at the next kernel update ('automagic' feature)? A better way is to find the section 'End Default options' and count (starting with 0 not 1) the number of lines with 'title' until you get to windows, then take that number and look for the line 'default  0' and replace the '0' with your number (it's usually 4).

---

### Post by goTUX! on 2007-01-12
If you did that, wouldnt the number change the next time the kernel updates?

What ive done is written the title of the option that I always want to boot by default

---

### Post by logos34 on 2007-01-12
> If you did that, wouldnt the number change the next time the kernel updates?

No, because grub should comment out the older kernel, in which case it doesn't count (I left that out). 

> Edit: "A better way is to find the section 'End Default options' and count (starting with 0 not 1) the number of lines with 'title' **without a hash '#' mark** until you get to windows..."

---

