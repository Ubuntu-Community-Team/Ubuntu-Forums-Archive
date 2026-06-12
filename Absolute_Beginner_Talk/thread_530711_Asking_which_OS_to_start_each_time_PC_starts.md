---
title: "Asking which OS to start each time PC starts?"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by NeptuneUK on 2007-08-20
after a couple of failed installations, each time i start up the PC I get asked which OS to start up ( several linux ones).

How can I get rid of the other ones???


thanks

---

### Post by Shazaam on 2007-08-20
What is your setup? Ubuntu alone or a dual-boot with Windows? Do you have a working Ubuntu installation?
Generally you can edit menu.lst (small L) and comment out the info you dont need.

---

### Post by NeptuneUK on 2007-08-20
Originally it was supposed to be a dual boot but I messed up the windows partition. ( was rly tired at 2am :( )

So I just have the one proper linux boot. So ubuntu is my sole OS :)

I have had the OS on my primary PC for sometime now (rly loved it!:D) so i thought id test run it on the family PC. 



(the installations messed up because the CD was smudged) :(

---

### Post by nitro_n2o on 2007-08-20
as shazaam said you need to edit the menu.lst 
open the file with ur favorite text editor 
```
sudo vim /boot/grub/menu.lst
```
or 
```
gksudo gedit /boot/grub/menu.lst
```
uncomment hiddenmenu or just add it to the file 
you can always get this back by pressing ESC while ur pc is starting up

---

### Post by Shazaam on 2007-08-20
Here is a partial from an old menu.lst, you can see where I commented out other kernels.

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/sda8 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/sda8 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda8 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda8 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

#title		Ubuntu, kernel 2.6.15-26-386
#root		(hd0,7)
#kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda8 ro quiet splash
#initrd		/boot/initrd.img-2.6.15-26-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
#root		(hd0,7)
#kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda8 ro single
#initrd		/boot/initrd.img-2.6.15-26-386

#title		Ubuntu, memtest86+
#root		(hd0,7)
#kernel		/boot/memtest86+.bin 
#boot

---

### Post by NeptuneUK on 2007-08-20
Im not entirely certian what to do! D:

Sorry if i didnt make it clear, im a linux noob.

---

### Post by nitro_n2o on 2007-08-20
alright... 
open up your terminal -- Applications->Accessories->Terminal 
type 
```
gksudo gedit /boot/grub/menu.lst
``` this will let you edit the file with root permissions 
then go to line 23 you'll see #hiddenmenu remove the # so the line will 
```
hiddenmenu
```
if you don't find this at line 23 just somewhere in the beginning of the file 
don't forget to save
then open the terminal again and type 
```
sudo update-grub
```

good luck

---

### Post by dRock1286 on 2007-08-20
Can you do this to change the order the OS's appear in the GRUB menu as well? ...that way my XP os is listed first and will auto boot if let to time out...?

---

### Post by dRock1286 on 2007-08-20
can anyone hlep me here?

---

### Post by Kilz on 2007-08-20
> **dRock1286 said:**
> can anyone hlep me here?

Yes

---

