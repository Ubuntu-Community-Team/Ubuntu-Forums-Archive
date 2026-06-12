---
title: "dont know what is going on"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by zeto34 on 2007-11-18
I got ubuntu running fine but how do i get back to windows xp? I read some other peoples questions and they all seem to be able to pick ubuntu or windows when they boot their computer. i have not seen anything that lets me choose. the dell logo pops up and then the screen is black for about 2-3 minutes and then i get the ubuntu login screen.

---

### Post by oilchangeguy on 2007-11-18
> **zeto34 said:**
> I got ubuntu running fine but how do i get back to windows xp? I read some other peoples questions and they all seem to be able to pick ubuntu or windows when they boot their computer. i have not seen anything that lets me choose. the dell logo pops up and then the screen is black for about 2-3 minutes and then i get the ubuntu login screen.

when you installed ubuntu, did you pick the option to use the entire drive? if so, xp is gone.

---

### Post by llamakc on 2007-11-18
Right after boot, hit the escape key. You should get the Grub boot menu. Choose Windows.

---

### Post by zeto34 on 2007-11-18
when you installed ubuntu, did you pick the option to use the entire drive?

i dont remember i just clicked the install button on the live CD and then restarted when it told me to. 

Right after boot, hit the escape key. You should get the Grub boot menu. Choose Windows. 

i hit the escape key and it came up with three diffrent things that all said ubuntu. does this mean that windows is gone? and if so what about my pictures and music is that gone too?

---

### Post by oilchangeguy on 2007-11-18
> **zeto34 said:**
> when you installed ubuntu, did you pick the option to use the entire drive?

i dont remember i just clicked the install button on the live CD and then restarted when it told me to. 

Right after boot, hit the escape key. You should get the Grub boot menu. Choose Windows. 

i hit the escape key and it came up with three diffrent things that all said ubuntu. does this mean that windows is gone? and if so what about my pictures and music is that gone too?

it would seem so. this is why you must backup your data BEFORE you attempt anything like this.

---

### Post by RockTonic3 on 2007-11-18
sounds like it's gone unfortunately (or maybe fortunately?).  If you want to have a dual boot you have to repartition your drive  during installation.  I believe it gives you an option to use the whole disk or partition manually.  It is always important to read through the steps!  I usually prefer to have one ntfs partition for windows system files, one small (10 gig) ext3 for linux, then a fat32 for shared music / document files since fat32 is read/write accessible by both windows and linux.  

to be sure, go to places > computer and see if there are more drives listed than just 'filesystem'  if it's only filesystem, see how large it is by right clicking and checking properties.  if the total size is about the size of your drive, windows is gone

good luck

---

### Post by teryowen on 2007-11-18
When in ubuntu do the following:

go and edit the /boot/grub/menu.lst file

find the line that says:
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu


and add a # infront of the 3rd line so it looks like this
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

this will display the grub file

as for the splash screen 
go and edit /etc/usplash.conf
to your resolution
mine looks like this
```
# Usplash configuration file
xres=1024
yres=768
```
change it to your computers resolution

Now execute this command
update-initramfs -u

---

