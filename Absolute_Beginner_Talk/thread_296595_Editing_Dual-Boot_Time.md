---
title: "Editing Dual-Boot Time"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by Jim Shunamon on 2006-11-09
First let me start by saying hello to everyone here:) I am new to both Ubuntu and to Linux in general. I have 2 hard drives on my system each with a different version of Windows:p . The first hard drive contains the Kubuntu distribution and the second hard drive contains the Ubuntu Distribution. As a result, I get a boot menu with far more choices on it than I can read in the default 10 seconds that the menu gives me. I have some programming experience, so I am not afraid to go in and change things. I need more than 10 seconds on this menu. Where do I go to change it and how do I co so? Thank you to anyone who can help:) Jim S.

---

### Post by professor_chaos on 2006-11-09
sudo gedit /boot/grub/menu.lst

change the "timeout" to whatever you want

---

### Post by catlett on 2006-11-09
Depending on which version has the copy of grub installed, the command is different.
In Ubuntu it is ```
sudo gedit /boot/grub/menu.lst
```
In kubuntu it is ```
sudo kwrite /boot/grub/menu.lst
```
When the file opens it will have the top portion the same as below. I highlighted the line that holds the value for the seconds the file is open. The standard is timeout 10. Change it to whatever you want. The value is in seconds. Just make sure to save the changes made to the file.
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
[COLOR="Red"]timeout         10[/COLOR]
```

---

### Post by xyz on 2006-11-09
Hi Jim,
Glad to see you here and of course Welcome!!
So you need more than 10 seconds...I mean hell I need more than 10 hours to do anything, so we should be able to help you out here!!In a console/terminal, type:
```
 sudo gedit /boot/grub/menu.lst

```
and look for...someewhere close to the top..."timeout		10"
and change it to whatever seconds you need!! Maybe not 10 hours!!;)

---

### Post by BLTicklemonster on 2006-11-09
You do of course realize that if you boot to an older kernel on either drive, you stand the chance of messing up x via the video card drivers, right?

Best to edit grub to loose all the old kernels by putting them like this:

```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-27-k7
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-k7 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-k7
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-k7 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-k7 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-27-k7
boot

#title		Ubuntu, kernel 2.6.15-27-386
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda3 ro quiet splash
#initrd		/boot/initrd.img-2.6.15-27-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda3 ro single
#initrd		/boot/initrd.img-2.6.15-27-386
#boot
```

You see all the #s? That comments out the lines, so each kernel listed there will be left out when you boot. I'd do that to each hard drive's kernels unless you have a specific reason to boot to old kernels. Besides, if you comment them out like that, you can always go back and remove the #s if you need to boot to one of the older kernels. Makes a neater boot menu, too.

Good luck, and welcome to the fascinating world of "wow, I can do sooo much more in this than I could in that other one".

---

### Post by xyz on 2006-11-09
> "wow, I can do sooo much more in this than I could in that other one".
Nothing to do with the thread but...I just love to read that kind of phrase!!
Ciao ...tante grazie e grazie tante!

---

### Post by BLTicklemonster on 2006-11-09
Good God, you're from Switzerland speaking Italian. My great great grandmother Zuber was from Switzerland, and my great grandmother was from Sicily. 

But other than ciao and grazie, I have no idea what you said, so I'll pass the butter... :cool:



*googled....

	
Siete benvenuti!

---

### Post by xyz on 2006-11-11
> **BLTicklemonster said:**
> Good God, you're from Switzerland speaking Italian. My great great grandmother Zuber was from Switzerland, and my great grandmother was from Sicily. 

But other than ciao and grazie, I have no idea what you said, so I'll pass the butter... :cool:



*googled....

	
Siete benvenuti!
Hi BLTicklemonster,
My Italian is VERY limited but living in a small country where 4 official languages are spoken helps pick up some here and there.However, my grandmother's family came from Napoli and Sicily!!

I must admit something to you: I thought you were from Rome Italia but only now do I realize it's not the same Rome.

---

### Post by Average Joe on 2006-11-11
Why not simply press the arrow down key on your key board when you see the boot menu? This will stop the time out count-down, so you will have all the time in the world to go through all of your boot entries. Pressing enter will start the selected operating system, whenever you want to.

---

### Post by xyz on 2006-11-11
Some folks have complicated problems...
I'm assuming he wants to power on, go pour himself a cup of coffee or something and have his Windows ready when he comes back to his computer...;)

---

