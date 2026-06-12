---
title: "dualboot ubuntu and xp doent work"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by waxfactor2nd on 2006-09-30
this is from the post: [http://ubuntuforums.org/showthread.php?t=268837](http://ubuntuforums.org/showthread.php?t=268837) but i was a dead end so i want help...

hi ive never used linux before, but everyone have to start at one point. ive chosen ubuntu to try, but i want to dual boot with windows xp. ive done as ive been guided, first installed windows xp on hdd 0 partition 1, then ive taken ubuntu and taken use the largest continuous free space and installed it. there where no problems. but when i now reboot my computer,it says grub loader 1.5
grub loading
grub error 22

before i can choose windows or linux.. now i dont know what i shall do.. can someone help me. im trying to install ubuntu 6.06lts for pc, and i have a amd atlhon 64 3700+, a8n-sli premium, 2gb ram, and two 250gb spinpoints (sata) (both linux and windows have to go on the first one.)

how shall i do??

ive tried as they say in the link to write:
sudo mkdir /mnt/ubuntu
sudo mount /dev/sda? /mnt/ubuntu
but that i didnt understand but i didnt work after i wrote it...

when i write the command gksudo gedit /boot/grub/menu.lst it gives me this error: (gedit:8005): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
ubuntu@ubuntu:~$
 and opens an empty gedit document.
when i write sudo fdisk -l i can see that where windows is its called: /dev/sda1
and linux is a /dev/sda2. but i dont know what i shall use this info for. so i havnt done anything with it / i guessed that there should stand the same thing as in the gedit doc but it didnt.. 

then bulldog says With this info you can alter GRUB [menu.lst] to correct the problems there seem to be. but i dont know what the word alter means but i gues it is change. but i dont know what to write into the menu.lst. so thats a dead end to..

and then he says if im in a live session (i gues that is when im using a livd cd / and that i am because the other thing doent work.) i can write sudo grub / then it says that it is probbing. but after a while i blinks as he says grub> and i can now write the next line wich is find /boot/grub/stage1 then i get (hd0,1) and he says i have to use that in the next line so i do (but later he says something about that i have a sata hdd and then it aint hd but sd or something like that. but it said hd) well i write root (hd0,1) and it works with no problem ( i tried with sd insted of hd but then i got error 23). then he says i have to write setup (hd0) so that i do and it dont say any problem. (i also tried to write hd0.1 and sda2 there but then i get an error. then he tells me to write quit to stop the grub>. and it does. but now i still get the f****** grub error22. wtf is wrong??

or here is what the error says::

 Originally Posted by waxfactor2nd
when i write find /boot/grub/stage1 i get (hd0,1) not sd, when i write root (sd0,1) i get error 23> error while parsing number...
if i write root (hd0.1) it sais filesystem type is ext2fs, paartition type 0x83
.then i write setup (sd0) it says eroor 23. but if i say hd0 it says: Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 15 sectors are embedded.
succeeded
Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.



anyone who can help me???

---

### Post by confused57 on 2006-09-30
If you decide to restore your Windows mbr, see this link:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Basically, you boot with the Windows install cd(not a recovery cd) and press "R" for recovery mode, then enter **fixmbr**, as suggested in the link.  If you don't have a Windows install cd, there's also a method described in the same link, using the Win98 SE bootdisk.

---

### Post by nthdegree on 2006-09-30
*My advice may be inappropriate for dealing with your problem, I find it harder to interpret what you are saying than Python does my programming.  It would be nice if you could make your post easier to read since I really do find it hard to understand.*

Open up a terminal, then type the following:

sudo nano /boot/grub/menu.lst

Then type your password (don't panic if it looks like nothing is typing, you don't even see *s) then press enter.

You can then edit your GRUB configuration to allow for a multiboot here's an example:

title Windows XP
rootnoverify (hd0,0)
chainloader +1
boot

Assuming your XP install is on the 1st partition of the 1st hard disk, my example would work - you will have to adapt it to suit your PC.

You will need to be inside Ubuntu for my above instructions to work, so you'll need to probably reinstall Ubuntu if you aren't experienced with chrooting into the Ubuntu system from a Live CD in order to change the menu.lst and fix GRUB.

---

