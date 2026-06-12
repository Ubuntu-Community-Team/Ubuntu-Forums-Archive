---
title: "GRUB/boot load Question Ubuntu + Windows"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by soapytheclown on 2006-06-05
Hi Everybody!

Well here goes,
i recently changed over from slackware linux (of which i kind of never used - only ever installed due to my brother and dad telling me that linux would be what i would be using at Uni - but installing and hotplug stuff incompatibility was an absolulte nightmare on slackware) and seen as my pc at the time wasnt connected to the net, i just forgot about it

a few days ago i finally got this due to finally getting my pc connected via wireless (Which i still cant get to work :( on ubuntu), and it pretty much works okay BUT, when slackware was installed, it allowed me to load off a floppy, and i kinda liked it like that.

so my question (finally) is there a way to remove grub and stick it onto a floppy easily? 

OR

can someone give me a total idiots guide to reordering the grub so that it highlights my Windows XP Pro first and does the 10seconds selection on that?

---

### Post by Kilz on 2006-06-05
[QUOTE=soapytheclown]Hi Everybody!

Well here goes,
i recently changed over from slackware linux (of which i kind of never used - only ever installed due to my brother and dad telling me that linux would be what i would be using at Uni - but installing and hotplug stuff incompatibility was an absolulte nightmare on slackware) and seen as my pc at the time wasnt connected to the net, i just forgot about it

a few days ago i finally got this due to finally getting my pc connected via wireless (Which i still cant get to work :( on ubuntu), and it pretty much works okay BUT, when slackware was installed, it allowed me to load off a floppy, and i kinda liked it like that.

so my question (finally) is there a way to remove grub and stick it onto a floppy easily? 

OR

can someone give me a total idiots guide to reordering the grub so that it highlights my Windows XP Pro first and does the 10seconds selection on that?[/QUOTE]

Its possible, but if you mess up you can make it so nothing boots. This is not something I personaly would mess with if I was a newbie. 
The list is in a file called menue.lst in /boot/grub. Type
sudo gedit /boot/grub/menu.lst

The file will open. you will see a lot of lines with # in front and finaly come to this line
## ## End Default Options ##

Under is is a bunch of sections The first one is Ubuntu. The last is Windows. Copy everything between 
# This entry automatically added by the Debian installer for a non-linux
and 
chainloader	+1
and paste it under 
## ## End Default Options ##
making sure there is a space under  ## ## End Default Options ## and chainloader	+1, then click save.

---

### Post by %hMa@?b&lt;C on 2006-06-05
edit your menu.lst will fix the pproblem you say.
first backup your grub menu.lst
```
sudo cp /boot/grub/menu.lst /boot/grub/menu_backup.lst
```
now were ready to fix your problem
```
sudo gedit /boot/grub/menu.lst
```
now, carefully make the following changes
change this section
```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
```
to 
```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```
then go to the very bottom, and make your entry that says something about windows above all of the "Ubuntu" ones.

if anything went wrong just replace your menu_backup.lst again

---

### Post by PaulCenji on 2006-06-05
Rather than have him cut and past the grub why not have him simply edit the default number? I have windows set as default for my wife. Just remember that "Numbering starts from 0, and
# the entry number 0 is the default if the command is not used."
And the devider counts for the default.
The best part is that as a newbie if he overshoots the default number it just ignores it and reads it as 0.

Here's my grub lacking the stuff i'm not talking about.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		4

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-23-amd64-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-amd64-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-23-amd64-generic
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

