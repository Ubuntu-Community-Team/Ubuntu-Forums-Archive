---
title: "Grub!!"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by thecat23 on 2006-03-28
Hi
  can anyone plz tell me where and how can i config the grub file as i can't boot into fedora4 after installing ubuntu? thanks!

---

### Post by erniewinner on 2006-03-28
hi,

i can't personally but... wouldn't it have been nice to boot the cd and have the option to reinstall grub. i'm using dapper flight 5 and it was the first thing i looked for. shame it's missing from the menu! surely it can't be that hard to do?:rolleyes:

---

### Post by frup on 2006-03-28
yeah i have had big problems with grub... im using lilo now. i still like grub though... i tried making grub install from floopy but i got a read error.

what i dont like about grub:
(note i've only just started using lilo so i dont know what problems i have with that :P)
if you get an error you cant just fix it (with out live CD)
when i have more than 2 HDD installed it doesnt seem to work.
on some of my machines it locates a partition but cant boot them :S

ack

---

### Post by wjp.reg on 2006-03-28
[QUOTE=thecat23]Hi
  can anyone plz tell me where and how can i config the grub file as i can't boot into fedora4 after installing ubuntu? thanks![/QUOTE]

google "reinstall grub ubuntu" found this answer.
[http://www.ubuntuforums.org/showthread.php?t=24113]("http://www.ubuntuforums.org/showthread.php?t=24113")

---

### Post by belikralj on 2006-03-28
Hi. I must appoligise to the other users that posted and to the user that started the thread, for just skim reading, but it's late and I need to go soon. I my self have just a few hours ago installed a dual boot system with Ubuntu and Fedora core 3 for the first time (first dual boot setup ever). So my knowledge/experience is limited to my situation. This is what I did.

 I did it by installing the fedora boot loader aka GRUB (I know you know). and following the instructions on this link:  [http://enterprise.linux.com/article.pl?sid=04/12/23/2033238&tid=129&tid=47](http://enterprise.linux.com/article.pl?sid=04/12/23/2033238&tid=129&tid=47)

though modifying it slightly to my own configuration.

Short version:
(this is if you installed Ubuntu's boot loader and wana dual boot red hat, if the other way around reverse)

1. mount Red Hat to Ubuntu floppy temporarily using "sudo mount /dev/hdXZ /media/floppy" where X is a character (a,b,c,d) indicating on which IDE your hard disk is connected (a for IDE primary master, b for IDE primary slave and so on)

2. from the mounted drive's \boot directory copy these files, System.mapXXXXX, vmlinuzXXXXXX, initrdXXXXXX where X's indicate your kernel number which should not concern you yet, but do make a note of them.

3. open the file menu.lst from the directory \boot\grub using root priviledges. You can do this by using the command (in the X window terminal) "sudo gedit \boot\grub\menu.lst", if you do not use sudo you wount be able to save the changes.

4. edit the file by adding the following to the end of all the other simmilar entries:

title "whatever you want to call your new distro"
        root (hd1,0)
        kernel /boot/vmlinuz"Your Kernel Number" "root=LABEL=/"
        initrd /boot/initrd"Your Kernel Number".img

where the 1 again represents the mount point of the hard drive (0 - primary master, 1 - primary slave, 2, secondary master ... and so on) in this case primary slave; and the 0 represents the logical partition you wish to use in this case the first partition on the drive. 

with the "root=LABEL=/" I do not understand it my self yet, but my one for Ubuntu (my other dual boot machine is down and appart for the moment) says "root=/dev/hdb2 ro quiet splash" so I assume it would work provided you change the "/hdb2" part to the hard drive and partition you are using. 

I hope you understand the above and find use of it. If you need more halp feel free to e-mail me but remember that I am a newb my self and I only did it once. using fedora's boot loader. the method should be the same though

my e-mail is [email]belikralj@yahoo.com.au[/email]

good night  :KS   :KS

---

### Post by belikralj on 2006-03-28
I forgot to say that Z in 1st step is the partition on which Red Hat is on (0 for partition 1 and 1 for partition 2...)

---

