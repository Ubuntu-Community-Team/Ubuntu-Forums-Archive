---
title: "really slow startup"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by default00 on 2008-03-22
ubuntu loads considerably slower than windows and im wondering if it was because of how i installed it. I reinstalled windows and ubuntu following the directions from this website: [http://howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty](http://howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty)

are there any options in ubuntu which i can make it start up faster or did i install it wrong? my windows partition is roughly 28 gb and ubuntu is 27gb.

---

### Post by manishtech on 2008-03-22
Does fsck run when you start ubuntu??

paste the contents of the file /etc/fstab

---

### Post by jan quark on 2008-03-22
try this suggestion
[http://ubuntuforums.org/showthread.php?t=580903&highlight=werd](http://ubuntuforums.org/showthread.php?t=580903&highlight=werd)
just a wild guess but might work

---

### Post by StOoZ on 2008-03-22
how much RAM do you have?

---

### Post by default00 on 2008-03-22
my fstab file shows...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=7611c18a-fb0b-45ea-bb0f-390a4b84da6a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=4C2053932053833E /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=151ffa6d-174e-36b4-de21-e76e1787847b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

the weird startup method wouldnt work either, when i tried to save the document it said that i didnt have permission. 

i have 1gb of ram.

---

### Post by dankdank on 2008-03-22
Do you get a ubuntu loading bar when you load grub? or just a black screen then straight to login?

---

### Post by jan quark on 2008-03-22
to edit the menu.lst file you have to have superuser access
run

```
gksudo gedit /boot/grub/menu.lst
```
now you can save the file
put a # in front of the quiet so you comment it out

---

### Post by default00 on 2008-03-22
i tried that weird method with taking out the "queit" in the menu.lst file and that didnt improve the time. I do get the ubuntu loading bar when i load. my windows time and my ubuntu time are just about the same now though...roughly 50-55 seconds. is this about right or is my ubuntu still running slow? i thought it was supposed to load much faster than windows.

---

### Post by manishtech on 2008-03-23
> **default00 said:**
> my fstab file shows...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=7611c18a-fb0b-45ea-bb0f-390a4b84da6a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=4C2053932053833E /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=151ffa6d-174e-36b4-de21-e76e1787847b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

the weird startup method wouldnt work either, when i tried to save the document it said that i didnt have permission. 

i have 1gb of ram.

Try changing the lines as
[COLOR=Red] UUID=7611c18a-fb0b-45ea-bb0f-390a4b84da6a /               ext3    defaults,errors=remount-ro 0 0[/COLOR]
AND
[COLOR=Red] UUID=4C2053932053833E /media/sda1     ntfs    defaults,umask=007,gid=46 0 0
[COLOR=Black]To edit this file type in the terminal
gksudo gedit /etc/fstab 

and change the contents



And one more point, I always thought that [COLOR=Red]quiet[/COLOR] was to make the verbose mode off while booting linux. And [COLOR=Red]splash[/COLOR] was to bring the splash screen of booting. I dont think these two should have any effect on boot time. IMHO [COLOR=Red]ro[/COLOR] should be making any differences.
[/COLOR][/COLOR]

---

### Post by default00 on 2008-03-23
nah that didnt change anything really...im still booting at about 55 seconds. should this boot time be faster?

i dont think i mentioned before that im booting on a laptop. looking around it seems that laptops boot slower than desktops?
is there still someway i can improve my bootime?

---

