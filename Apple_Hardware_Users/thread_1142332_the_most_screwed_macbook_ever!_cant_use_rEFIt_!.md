---
title: "the most screwed macbook ever! cant use rEFIt !"
date: 2009-04-29
forum: Apple Hardware Users
---

### Post by 1nfinitel00p on 2009-04-29
hi everyone, I've been reading for a whole MONTH about my issue and been trying different methods to repair my booting problems.

Precondition: Macbook Unibody (late 2008 ) used bootcamp to install ubuntu 8.10,
"No bootable device found -- insert boot disk and press any key" was my problem, I installed ubuntu and I noticed my Macintosh HD was still there so I backed up all my information into an external hd.

anyway I still wasnt able to boot back into mac osx! so what i've tried:

I already used, the startup cmds  C , ALT, zapped the nvram, open firmware etc. etc. 
I totally erased and formated my Macintosh HD with the Gparted live cd, used a lot of commands to try to fix my hd like sudo fdisk and stuff like that. changed the flags to assign macintosh hd as my default boot disk but no luck, I have the doubt that if i already erased the whole hd and formated does it still working? 

I also tried with the rEFIt live cd which seems to be the fix for many people with the "same" problem. 

but that problem seems to be something about a "flash folder" and some kinda problem with the tux logo... anyway.... my problem is almost the same except for one thing

when I use the ALT key I won't get the ? interrogation mark what I get is a login screen asking for a password, a blue/gray login screen with a lock.. I HAVENT READ ANYTHING ABOUT THIS SCREEN IN THE WHOLE INTERNET...believe me i've reading and reading for about a month a nothing :S  any help will be very appreaciated...

something else... I already tried with the mac installation cd and of course used the C key and ALT startup keys.

Personally I believe that this is going to be fixed either bypassing that login screen ( it is not my root password or mac password of course I already tried) or using terminal commands, editing the grub and that way enter the rEFIt (this one seems good) , or editing the grub to enter into the mac instalation cd and install mac os again !! w00t! but I dont know, Im here for your help you can ask me if you have any doubts thanks.

SEE WHOLE VERSION FOR A PICTURE OF THE MB SCREEN

---

### Post by Doncr on 2009-04-29
Doesn't look exactly the same ... but fairly close.

[http://support.apple.com/kb/HT1352](http://support.apple.com/kb/HT1352)

---

### Post by 1nfinitel00p on 2009-04-30
Wow, very close! The picture of the lock is different :S so it says that I need to have physical access to inside the computer in order to reset that passwd, it also says that using the instalation dvd I can reset but there is the problem that i cant boot from the dvd :/ is there any way to edit the grub and tell the grub that I want to boot from the dvd when it is inside? 

Ps.- thanks a lot for the link!

---

### Post by kittshuldrunlinux on 2009-04-30
did you ever set a open firmware password.
if you didnt some body must of set one when you wernt looking

---

### Post by 1nfinitel00p on 2009-04-30
> **kittshuldrunlinux said:**
> did you ever set a open firmware password.
if you didnt some body must of set one when you wernt looking

the only way that could be possible, is if somebody did it via SSH.

I always locked my mac with the normal account password, but this kind of password login screen is different than the one of the apple.support page :S that's the very weird part of all of this.

I need to know how to edit the grub menu and add the option to boot (B) from the installation dvd...  OR.. open my mac and reset the open firmware password, idk how to do that either

---

### Post by cyberdork33 on 2009-04-30
> **1nfinitel00p said:**
> the only way that could be possible, is if somebody did it via SSH.

I always locked my mac with the normal account password, but this kind of password login screen is different than the one of the apple.support page :S that's the very weird part of all of this.

I need to know how to edit the grub menu and add the option to boot (B) from the installation dvd...  OR.. open my mac and reset the open firmware password, idk how to do that either
I'm confused... how are you editting the grub config if you can't boot?

---

### Post by 1nfinitel00p on 2009-04-30
> **cyberdork33 said:**
> I'm confused... how are you editting the grub config if you can't boot?

well, I can only boot the ubuntu 8.10 cd and grub live cd because at the beggining I was trying to make a partition with bootcamp. now I can access the whole ubuntu 8.10 os and grub live cd, only that, and when I install ubuntu completely and I removed the ubuntu cd, I inserted the mac installation cd ubuntu detects it as "WindowsSupport" probably because by default bootcamp has windows as your only choice to partitionate your hd.

well the point is if i can edit the grub and tell the grub that I want to boot from the mac cd I found this page.

[http://www.insanelymac.com/forum/lofiversion/index.php/t3622.html](http://www.insanelymac.com/forum/lofiversion/index.php/t3622.html)

title                        OSX 86
root                       (hd0,0)
rootnoverify         +1

but this configuration wont work for cd's .

Probably is not possible to boot from a CD on grub :S

---

### Post by 1nfinitel00p on 2009-05-01
This thing is tempting me....

[http://macosx.com/forums/archive/t-270395.html](http://macosx.com/forums/archive/t-270395.html)


Add/remove my macbook's amount of RAM then kill the pram 3 times and the open firmware password will be gone!

seems a little complicated, my unibody macbook has 4gb ddr3 what if I change it with ddr2? from a white macbook?

---

### Post by 1nfinitel00p on 2009-05-01
ZOMG!!!!! I finally did it! its almost working again, I removed 2gb of ram and zapped the pram and OMG! When I heard the mac beep" it was like the angels singing goddamit :D ! 

right now I'm repairing my hd to be recognizable because it is not recognizing it as a volume but i dont really care thats fixable, everythings is fixable compaired to thissss damn problem .


thank u a loot people, all of your post were very useful

:D  I'm not gonna sleeeeep know loool.

---

