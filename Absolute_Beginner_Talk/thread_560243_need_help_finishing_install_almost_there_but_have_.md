---
title: "need help finishing install almost there but have some mesage"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by johnnyk1978 on 2007-09-26
i get it all install take out cd reboot and shows this

kernel alive
kernal direct mapping tables up to 100000000 8000-d000

in between 100000000 and 8000 there is a symbol i cant find on my keyboard looks almost like @ but not exact

---

### Post by overdrank on 2007-09-26
> **johnnyk1978 said:**
> i get it all install take out cd reboot and shows this

kernel alive
kernal direct mapping tables up to 100000000 8000-d000

in between 100000000 and 8000 there is a symbol i cant find on my keyboard looks almost like @ but not exact

Hi can you give us some specs on your system? And are you installing with the live cd or the alternate cd?

---

### Post by johnnyk1978 on 2007-09-26
specs are dell dimension c521 amd athlonx2  2.ghz 160gb sata harddrive 1224 ram dvd burn drive. and i am using live cd

---

### Post by darc on 2007-09-26
> **johnnyk1978 said:**
> i get it all install take out cd reboot and shows this

kernel alive
kernal direct mapping tables up to 100000000 8000-d000

in between 100000000 and 8000 there is a symbol i cant find on my keyboard looks almost like @ but not exact

I get that same message but it only stays for a couple of seconds before continuing to boot.

I'm assuming your's hangs there?
-darc

---

### Post by johnnyk1978 on 2007-09-26
yes i have givin it at least five min before i reboot

---

### Post by darc on 2007-09-26
Try this:

> 

I'm trying to move back to Linux, so I'm trying Ubuntu 7.04 (Feisty Fawn) for the first time. I got the following and then the system locked up with a blinking cursor in the top left.

Kernel Alive
Kernel direct mapping tables up to 100000000 @ 8000-d000

I bypassed it by hitting F6 for the advanced options line at the installer boot screen, removing the splash option and adding noapic.



Let us know how that goes.
-darc

---

### Post by johnnyk1978 on 2007-09-26
it works from the live cd but i get no f6 option when boot from hard drive when i boot in safe mode everything checks ok but i don't know how to procede when it says johnny@desktop. 
here is the errer i get 100.197433 mp-bios bug:8254 timer not connect to i0-apic
100.377650 kernel panic-not syncing:i0-apict timer doesn't work: try using the "noapic parameter 100.377691

i used the noapic from the live cd and thats how am able to post but can't do the same from hard drive

---

### Post by overdrank on 2007-09-26
> **johnnyk1978 said:**
> it works from the live cd but i get no f6 option when boot from hard drive when i boot in safe mode everything checks ok but i don't know how to procede when it says johnny@desktop. 
here is the errer i get 100.197433 mp-bios bug:8254 timer not connect to i0-apic
100.377650 kernel panic-not syncing:i0-apict timer doesn't work: try using the "noapic parameter 100.377691

i used the noapic from the live cd and thats how am able to post but can't do the same from hard drive

Hi from the hard drive you can hit the escape key when the grub has highlighted the kernel. Then I believe use the arrow keys to highlight the second one in this list. that is the kernel and you can edit it by using the e and then add that command then press b to boot. No as for making this permanent I will have to search and find how to edit the kernel and make it stick. Hope this helps.

---

### Post by darc on 2007-09-26
Do you get the GRUB boot menu when you start your computer up?  Or, does it go straight into booting Ubuntu?

1)  If you get the GRUB menu, hit ESC and find the kernel line, then hit 'E' to edit it, and add noapic at the end.  Then hit whatever key it tells you to save it, then 'B' to boot it.  If this works, then you can edit /boot/grub/menu.lst to make it permanent.

2)  If you don't get the GRUB menu, it's set to auto-boot your kernel and you need to give it a time to wait (or try smashing 'ESC' frantically as soon as the computer passes the POST) which can be done by editing /boot/grub/menu.lst

NOTE:  My steps may not be exact because I'm at work on a windows machine (I know... it sucks!) so I can't try it on my Linux machine and be sure.

-darc

---

### Post by johnnyk1978 on 2007-09-26
that did it now i havent tried to reboot but will it stay or do i have to do something else to make change pemenent

---

### Post by darc on 2007-09-26
You'll have to edit /boot/grub/menu.lst and then I'm almost positive you'll have to reinstall GRUB to the disk again to make sure the change is written to the MBR (or superblock, whatever).  

You can find instructions for doing that (again, after you make the change in /boot/grub/menu.lst) here:
[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html)

Note the weirdness in drive numbers, if you're installing grub on /dev/hda1, you'll need to use the command 'root (hd0,0)'

You can find the right drive location with the following command (in the GRUB shell):
find /boot/grub/stage1

This is all listed in the article I linked you to, but those points can always use some reinforcement as they're a bit weird.

-darc

---

### Post by johnnyk1978 on 2007-09-26
ok that was not the easiest thing i have ever done but done none the less thanks for all your help and pationce it is very much apritiated fogive my spelling

---

### Post by overdrank on 2007-09-26
> **johnnyk1978 said:**
> ok that was not the easiest thing i have ever done but done none the less thanks for all your help and pationce it is very much apritiated fogive my spelling

Glad to here you got it working and good luck and enjoy!!!!!!!!!!! :guitar:

---

### Post by darc on 2007-09-26
Cool.  
The more you know...
:: plays cheesy theme music ::

: )
-darc

---

### Post by kayetech on 2008-01-29
Hi all, I am having the same issue. I tried editing the file and adding noapic to no luck. I am still getting the same error when booting from grub:

Kernel alive
Kernel direct mapping tables up to 100000000 @ 8000-d000

Any thoughts? I tried reinstalling grub, and it came back with no errors. I am using the AMD64 kernel and here is my hardware:

AMD 64 X2 4200+ AM2
2x 1GB Corsair
e-GeForce 7600 GT 256MB GDDR3 PCI-E

All help is appreciated! Thanks!

Kerry

---

