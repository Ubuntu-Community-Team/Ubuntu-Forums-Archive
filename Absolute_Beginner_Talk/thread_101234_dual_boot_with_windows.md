---
title: "dual boot with windows"
date: 2005-12-09
forum: Absolute Beginner Talk
---

### Post by SouthAfricanBadger on 2005-12-09
I'm new to Linux and I just installed Ubuntu with my one harddrive with windows and the other with ubuntu. it's just that when i startup, i dont get the boot menu to choose between ubuntu and windows when i load up. i have to disconnect a harddrive everytime i want to change between OS's which is really annoying. how can i get the startup menu going?

---

### Post by earobinson on 2005-12-09
Did you install it with only one HD pluged in?

---

### Post by SouthAfricanBadger on 2005-12-09
[QUOTE=earobinson]Did you install it with only one HD pluged in?[/QUOTE]

yeah I did.

---

### Post by earobinson on 2005-12-09
lol thats the problem, I have no clue how to fix it however sorry... I will look into it but my guess Is you have a reinstall comming your way.

---

### Post by scruffy on 2005-12-09
As your systems booting up, you should see the GRUB boot loader which will say hit "ESC" to access menu. Now depending on how you installed ubuntu will depend on wether you see and wether the option to boot into windows will be there.

Good luck

Scruffy;)

edit 
-------------

sorry just read your post again,  do a reinstall but leave both drives in, then you'll get the option to choose one or the other when all done. Choose which drive to install to carefully though\\:D/

---

### Post by earobinson on 2005-12-09
Scruffy this will not work if post 3 is true, unless im missing something

---

### Post by BatsotO on 2005-12-09
You can choose wich drive you want to boot from bios. I think that would be the simplest thing to do.

---

### Post by scruffy on 2005-12-09
[QUOTE=earobinson]Scruffy this will not work if post 3 is true, unless im missing something[/QUOTE]

Yeh I know I saw that after posting thats why I edited my post as soon as I realised I'd grabbed the wrong end of the stick..doh! 

My edited post just reads to reinstall but leave both drives in, that way the options will be given to install on an individual drive, and finally a dual boot sytem he'll have.

I'll shut up and go away now:-\"

---

### Post by ausm on 2005-12-09
The best way that worked for me was to use two seperate hard drives and install WinXP on the primary partition of the 1st drive and format the logical partition FAT32 so I could use the files in both WinXP and Ubuntu.

The next thing I did was install Ubuntu to the slave drive and when it loads GRUB make sure you select to install it in the MBR.

After it finishes loading and on the next reboot GRUB 1.5 should load and give you the option to boot either Ubuntu or WinXP.

Good Luck,

Ausm

---

### Post by earobinson on 2005-12-09
[QUOTE=BatsotO]You can choose wich drive you want to boot from bios. I think that would be the simplest thing to do.[/QUOTE]
Thats a good idea, but instead of unpluging the drive you will be forced to go into the bios each time.

scruffy did not mean to offend you, your suggestions are still very welcome, im stumped

---

### Post by scruffy on 2005-12-09
no offence taken earobinson, its just nice to be here :cool:

---

### Post by SouthAfricanBadger on 2005-12-09
[QUOTE=scruffy]As your systems booting up, you should see the GRUB boot loader which will say hit "ESC" to access menu. Now depending on how you installed ubuntu will depend on wether you see and wether the option to boot into windows will be there.

Good luck

Scruffy;)

edit 
-------------

sorry just read your post again,  do a reinstall but leave both drives in, then you'll get the option to choose one or the other when all done. Choose which drive to install to carefully though\\:D/[/QUOTE]

Thanks for the input. Yeah, I kinda figured it would be the safest option to unplug one of my HDs without it affecting the other. I don't mind doing a reinstall. Like I said, I'm brand spanking new to Linux, so I have nothing of any importance on it.

So when I put in the install cd, should I use advanced installation or the basic one? will it give me the option to change the drive?

---

### Post by scruffy on 2005-12-09
Hi SouthAfricanBadger,

I used the basic install and followed it through, The installation installs GRUB which is a boot manager where you can select additional operating systems to boot from.

Hope all goes well

Scruffy

---

### Post by SouthAfricanBadger on 2005-12-09
[QUOTE=scruffy]Hi SouthAfricanBadger,

I used the basic install and followed it through, The installation installs GRUB which is a boot manager where you can select additional operating systems to boot from.

Hope all goes well

Scruffy[/QUOTE]

Thanks a lot. I'll try that.

---

### Post by scruffy on 2005-12-09
Your welcome,

Let us know how you get on :D

Scruffy

---

### Post by BatsotO on 2005-12-09
:P I think unplugging need more physical effort and I'm a very lazy person.

I switch my drives over computers I have (actualy properties of the company where work, but I considere they are mine... yes... mine). Sometime I set one another primary-secondary. BIOS let me decide which drive i want to boot. That gave me the dual booting effect i need.

correct me if I'm wrong :

When you set grub for dual booting on one drive, the one without grub wont boot if you disconnect it from drive with grub.

for instance :

your drive A is primary with windows.
your drive B will be Linux
you set the grub or lilo on drive A 
one day you decide to remove drive A
your drive B wont boot that day

am i making any mistake here? I did it only one time like a year ago :P

I still think doing with bios is a lot more simple, and not need any re-instalation.

---

### Post by prizrak on 2005-12-10
Well there is actually another way but I think he already reinstalled so too late :)
For future reference however you SHOULD be able to do```
sudo gedit /boot/grub/menu.lst
```
In there there is something like this ```
title           Ubuntu, kernel 2.6.12-10-686
root            (hd0,0)
kernel          /vmlinuz-2.6.12-10-686 root=/dev/hda3 ro quiet no-splash reboot=h
initrd          /initrd.img-2.6.12-10-686
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-686 (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.12-10-686 root=/dev/hda3 ro single
initrd          /initrd.img-2.6.12-10-686
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /memtest86+.bin
boot

```
Where you could add something like this to ```
 
title               Windows 95/98/NT/2000
root               (hd0,0)
makeactive
chainloader   +1

```
If my memory serves me correctly the root (hdx,x) portion specify which drive and partition the system is on. I have no way of testing this unfortunately as I only run Ubuntu but anyone who wants to test this out is welcome to, shouldn't break anything :)

---

### Post by olieviya on 2005-12-10
Did you create a swap? I'm new here and new to ubuntu but when I installed I created a swap.

---

### Post by BatsotO on 2005-12-11
[QUOTE=olieviya]Did you create a swap? I'm new here and new to ubuntu but when I installed I created a swap.[/QUOTE]
yes. It's default.

---

