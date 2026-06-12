---
title: "Please help! BIG Ubuntu trouble"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by S//P on 2006-06-03
ok so i have 2 hard drives in my computer. i decided to install ubuntu, even though this is my first time experimenting with ubuntu/linux.

what started out well turned into disaster! i ran the cd and tried to install ubuntu on my 2nd hard drive, - i chose the option "completely erase" - it was my slave hard drive. my other one is my windows one.

so now i erased my 2nd hard drive and windows wont even recognise it anymore! i also would like to uninstall ubuntu on this computer, i basically want to get rid of it and make my comp a windows one again!

this is my first time with ubuntu and i dont have much experience with anything like this (well i wouldnt since im only 15 years old!)

someone please help me out
thank you very much in advance
S

---

### Post by aysiu on 2006-06-03
Actually, it sounded like the installation went as planned--Windows on your first hard drive, Ubuntu on your second hard drive.

Windows not recognizing Ubuntu (or any Linux distribution) is normal. That can be remedied, though, with [http://www.fs-driver.org](http://www.fs-driver.org)

If you really are determined to get rid of Ubuntu, though, Google *fixmbr* on the Microsoft website and then go to Control Panel > Administrative Tools > Computer Administration > Disk Administration, find the second hard drive (which should be an "unknown" but "healthy" drive) and just reformat it as NTFS or FAT32.

---

### Post by catlett on 2006-06-03
windows isn't going to recognise ubuntu. windows won't acknowledge a different filesystem,
You can get back to where you were but first you need to be more specific.
Did the install work? Meaning did ubuntu install and now you have a menu when you start your computer and that menu lets you pick ubuntu or windows?
Or did the install not work? Does your computer start and go right into windows?
All you have to do is reformat your second hard drive again and ubuntu will be gone and windows will recognise your other drive.
But right now post back and tell me what happens when you start your computer.

edit: didn't see the above post. you won't have any problems now. aysiu can walk you through anything. just post back exactly whats happening when you start your computer

---

### Post by S//P on 2006-06-03
yeah i think the installation actually went to plan (even though thats not exactly what i wanted.)

i dont actually know whether i want to get rid of ubuntu, i quite like it, and its growing on me now, all i would like is for windows to have full access to both my drives. which seems possible with what aysiu said. (however i am having trouble again installing it i dont know what to put in this dialog - see attachment)

the next thing i need is for ubuntu to stop being the highlighted OS on the boot up screen, some others in my family use my computer sometimes and id rather not complicate things for them, is there anyway to make windows default at the dual boot screen?

 other than these problems im pretty happy with ubuntu and i dont think i want to get rid of it. (my next problem will be the wine emulator - but ill try to figure that one out myself :) )

im sorry if my problems/questions seem stupid or obvious, but ive never really done anything like this before - i just wanted to escape windows!

edit: just to let you know im on windows with a mac theme in the attachment

---

### Post by catlett on 2006-06-03
Your doing it right. In the corner the box that says "none" click on the box and a menu will drop down with available drive letters. Choose a letter and that is it. When you go to "my computer" it will be there next to your C local disk (or whatever windows is titled as)
Now you can double click on it to explore/search just like you do your C drive.
Yes you can change the boot order to windows and you can change the time to 3 seconds so it seem like it goes straight into windows. You will have to be quick to hit a key to stop the sequence but to your family it will look like it is booting right to windows.
Give me a few and I'l get the directions for you.

---

### Post by catlett on 2006-06-03
This is my list just as an example. You can do what you want by changing the "default" number. Grub uses 0 as a place so remember when counting entries. Anyways If I wanted windows as my default I woould have to change "0" at default to "5" (grub uses 0 so windows is my 6th entry but it is labeled 5 in grub)
You can make it boot into windows faster as well by changing the "timeout" value. So change the timeout from "10" to "3" and it will only delay 3 seconds before grub boots to windows.
To get to this menu and to edit it enter this in the terminal ```
sudo gedit /boot/grub/menu.lst
```Make the changes to default and timeout THAT"S IT nothing else. Just delete 0 and put 5 (or whatever your xp is) and delete 10 and put 3.

P.S. default and timeout won't be in red. I did that in the fiorum reply section to make it stand out.```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
[COLOR="Red"]default		0[/COLOR]

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
[COLOR="Red"]timeout		10[/COLOR]

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue
T

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hda7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)


# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-23-686
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/hda7 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-686 (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/hda7 ro single
initrd		/boot/initrd.img-2.6.15-23-686
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda7 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda7 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,6)
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

title          Debian GNU/Linux
rootnoverify   (hd0,8)
chainloader    +1

title          Fedora Core 5
rootnoverify   (hd0,10)
chainloader    +1
```

---

### Post by aysiu on 2006-06-03
[QUOTE=catlett]aysiu can walk you through anything. just post back exactly whats happening when you start your computer[/QUOTE] Actually, catlett, it seems you have things well in hand.

---

### Post by S//P on 2006-06-03
thank you very much guys, im gonna have to learn more about this terminal and stuff, but im just glad that my first tryout of ubuntu hasn't turned out so badly! ubuntu looks like its very customizable)

the help was invaluable and im hoping to ditch windows in a few years time, but until then i am happy with dual booting,

thanks again (and of course if you have more suggestions please keep posting here as i have email notification)

---

### Post by CompShrink on 2006-06-03
Ok, first off the screenshot looks fine. You should be able to access ubuntu as drive D:\ in windows. Note that the other users in your family will be able to also, from what I understand. So maybe mention it to them and ask them to not open it.

As for grub, open a terminal, Applications > Accessories > Terminal,  and type in:

sudo gedit /boot/grub/menu.lst

Read through some of it. It might be a bit scary, but it's a good learning experience. The important thing is the part right after
### END DEBIAN AUTOMAGIC KERNELS LIST

Find that. Then under it, you'll see a bunch of blocks of text for each OS other than ubuntu you have. Find the one for Windows, probably near the very bottom of the file, mine's the very last one. Mine looks like:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc2
title		Windows NT/2000/XP (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

CUT and paste (don't leave a copy behind) that from the bottom, and place it as the last thing before
### BEGIN AUTOMAGIC KERNELS LIST

And reboot, now windows should be automatically booted into after 10 seconds if another option isn't choosen.

EDIT: you could follow what callet said, but I would suggest leaving it at 0 and moving the XP line, because otherwise when you update your kernel, upgrade to the next ubuntu version, etc, the XP line will move down, and you have to change the "default" number. Leave the default at 0, and move Windows up above ### BEGIN AUTOMAGIC KERNELS LIST and you'll have better results.

---

### Post by catlett on 2006-06-03
> I would suggest leaving it at 0 and moving the XP line, because otherwise when you update your kernel, upgrade to the next ubuntu version, etc, the XP line will move down, and you have to change the "default" number. Leave the default at 0, and move Windows up above ### BEGIN AUTOMAGIC KERNELS LIST and you'll have better results.

That is very smart! And correct. If a new kernel installs during an update the menu list will automatically change and add another listing which will move the entries behind ubuntu back a space and change the "5" choice. Very sharp CompShrink, I stand corrected.

---

### Post by S//P on 2006-06-04
ok i tried the ```
 sudo gedit /boot/grub/menu.lst 
``` 
it asks me for my password, i press enter and type it in, (this is my admin password) and it does not accept it, am i doing something wrong?

---

### Post by sailor2001 on 2006-06-04
don't press enter until AFTER you type in password

---

### Post by catlett on 2006-06-04
[QUOTE=S//P]ok i tried the ```
 sudo gedit /boot/grub/menu.lst 
``` 
it asks me for my password, i press enter and type it in, (this is my admin password) and it does not accept it, am i doing something wrong?[/QUOTE]
Did sailors directions work for you? Just to go into more detail. When it asks for a password you will enter your user password. The one you log in with. It won't create text or ***** but it is being entered.THEN press enter  as already stated.
Sudo uses your regular user password. You can create a root (administrative) password but it is not needed when using sudo.
In Ubuntu you do not need another password. You achieve administrative powers by entering sudo before the command and then entering your user password.
IF you made a root (which is possible but not advisable in Ubuntu) password you would type su then press enter. Enter your root password, Press enter. Then you would be at a root terminal. If you are at a root terminal you do not use sudo. So if you are following advice or a how to that says enter sudo and you are at a root terminal you DO NOT enter sudo. You just enter the command after sudo.

---

### Post by S//P on 2006-06-09
im back! sorry for the big delay but....

ok so a few days ago i followed your instructions catlett (i already did them before sailor told me his) everything was working pretty well, but i realised i wasn't using ubuntu at all, especially since it didn't recognise my internet, so i decided to get rid of it for the time being. 

However ... i didn't read aysiu's instructions clearly and proceeded to reformat my second hard drive. mistake.

so i dont need to explain to you what happened next do I? im sure its a common occurence, especially with newbies, GRUB error 17.

i put the ubuntu cd in and tried to re-install it, but it couldnt create a file system for some reason.

now this wouldn't be so bad if i had a recovery disk or something, but windows came preinstalled with my machine when i bought it, and i didnt use the tool provided to make my own disk. thinking "i'll be alright" (trust me i wont make this mistake again!)

so i asked my friend to lend me his recovery CD, i played around with the recovery console with commands such as bootcfg etc...

nothing happened, so then i tried to install ubuntu on my second hard drive again - and luckily it worked!! so now im back on the dual boot system. i changed the default boot line to 5 and the timeout to 4 using sailors instructions :) (i haven't properly understood compshrinks post yet :$ )

so now temporarlily things are fine (and yes i did make a recovery CD - as soon as i got back into windows infact.)

im thinking of uninstalling ubuntu again, i understand that all you have to do is reformat, put in the recovery disk, go into the recovery console and type in "fixmbr"  (but i can't be sure on this) 
but another part of me wants to stay with ubuntu and try and figure it out and learn more. maybe if i get the wireless card working with it, it's just that this experience has scared me a bit.

please reply

sincerely
S//P

---

### Post by catlett on 2006-06-09
Don't reformat until you use fixmbr and it works. You get there by entering "R"   at  the prompt  from windows recovery disk. It will get you to a comand line eventually and you enter ```
fixmbr
``` If that works all you have to do is navigate to the administrative tasks from windows control panel. One of them will be a device manager and a sub-selection will be disk management. This will list all your partititions. Choose Ubuntu's partition and select reformat (choose ntfs) and that is it.
If you ever come back to ubuntu choose to install grub to a floppy diskette. This way windows mbr won't be touched and your computer will start normally until you put the floppy in before startup. When you put the floppy in and start your computer, grub will come up and you can select ubuntu.
You might want to keep trying Ubuntu through the live cd. It won't be as responsive or save any changes you make but you can "stumble about" without changing your hard drive and if you stumble on how to get your wireless card working maybe you'l want to reinstall.
Good luck. And remember, where always here and your always welcome.

---

### Post by S//P on 2006-06-09
Thank you very much catlett! im gonna leave it on my system for now but i think i might uninstall it later on, ive never seen such a great forum community before and maybe ill be a big part of it someday, thanks for all your help !!

S//P

---

