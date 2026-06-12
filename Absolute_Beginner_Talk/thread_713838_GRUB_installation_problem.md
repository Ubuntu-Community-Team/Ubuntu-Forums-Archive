---
title: "GRUB installation problem"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by StorM_GmA on 2008-03-03
Hello! I'm new in the forums since I decided to install ubuntu and get some expirience! There were similar threads and I read 'em before I post but I couldn't get the answers I need!

So, here's the problem. I'm running winXP on a 40Gb hdd (I also have an 120Gb hdd as D:\) and decided to install ubuntu while still having winXP. I made the .iso Live CD for the ubuntu, ran it and made the installation several times because I had some issues with the partitions and the space... but finaly I maded and completed the installation. After the reboot, I went straight to the winXP without any question about which OS I want to launch. After google searching I read about GRUB, booted again with Live CD and typed some commands in the terminal (I found the commands in a website), rebooted again and nothing. In another website I read about GParted, so I download that too, made a CD and let the computer boot from that, but after a while the screen went crazy.

So, considering I know absolutely nothing about Linux (however I read a guide in this forums), is there something that I am missing? Everywhere I read that the order is

1. install ubuntu
2. reboot with the Live CD
3. type some things in the terminal to configure GRUB
4. restart without Live CD and the dual boot screen appears

but it doesn't work for me so either I make something wong, or I understood something wrong! Please give me some guidance in as much simpler words as possible!

Thanks alot for your time reading my post!

---

### Post by kesman on 2008-03-03
In the install part the installer asks you if you agree with installing GRUB boot loader to the master boot record (MBR) in the first active partition. You must answer yes to this, after that, it installs the bootloader and you are able to select between the operating systems.
When you start your computer, does it tell you it's loading grub? If so, hit ESC or ENTER to access the menu to select the OS.

---

### Post by StorM_GmA on 2008-03-03
I don't remember such question... I forgot to mention I installed ubuntu 7.10 (if it makes any difference) and there were 7 steps before install where i'm 99,9% there were no question about the GRUB. I haven't noticed and GRUB loading at the start up because screens are going extremely fast but I will make some reboots and try to see if there is anything about GRUB!

Furthermore, I made the partitions from Manual option at the ubuntu installer but I think they are ok (made ext3 boot and swap partitions). Sorry if it's non-sense but I really don't know what information someone might need!

---

### Post by StorM_GmA on 2008-03-03
ok I made several reboots and I saw nothing about GRUB...I was also pressing continiusly the esc and the Enter in case there were a non visible screen but nothing...

---

### Post by kesman on 2008-03-03
You don't need to manually partition your hard drive if there's unpartitioned space. Just use the "use largest empty space" option. Also, read carefully all the messages that are shown during the install process.

---

### Post by Dojan5 on 2008-03-03
To reinstall grub to the boot follow theese steps.
1. Open the terminal in LiveCD
2. Write "sudo grub"
    (You should get a window with grub> instead of user@blah$)
3. Write "find /boot/grub/stage1" (If is answers (hd1,0 or hd1,1 or something like that and it aint on hd0, continue!)
4. Change the active root by typing in "root(hd0,0)
5. To reinstall BRUB to the MBR then write "setup (hd0)"
Voila!
You should now have GRUB installed to the MBR(MBR is like first on the drive i think) and when restarting you should get the GRUB menu and so on... Hope that i could help

Oh yaa.
GParted is probably a short for GNOMEPartition editor, ro meant to sound in tha way.
Can you specify what commands you ran?
And GParted is already on the LiveCD, so theres no need to download that, as long as it isnt in the System>Administration>GParted and that you really need it.
What i think is that (If you have the other CD you burned) in the CD drive (Which might be set as boot before A: and the HDD) it thinks that the CD is a boot cd, but when looking more at it it aint a proper boot cd...
But thats only what i think, im no expert, but when reinstalling GRUB (Which you should do if it is in hd1,0 or hd1,1) i know some stuff..

---

### Post by StorM_GmA on 2008-03-05
Dojan5 I followed your instructions but I faced some problems...

4. Change the active root by typing in "root(hd0,0)

I had to type root (hd0,0) (with a space after the root) in order to work. After that I tried to run the setup (hd0) but it says

Error 17: Cannot mount selected partition

any clues?!

here's what i typed:

grub> find /boot/grub/stage1
 (hd1,3)

grub> root(hd0,0)

Error 27: Unrecognized command

grub> root(hd0,0)

Error 27: Unrecognized command

grub> root (hd0,0)

grub> setup (hd0)

Error 17: Cannot mount selected partition

grub> setup(hd0)

Error 27: Unrecognized command

grub>

---

### Post by StorM_GmA on 2008-03-05
Wow things are running very fast here...half an hour and my post went to 2nd page! Can someone give me any clue to what that error might be or how to fix it?

Thanks!

---

