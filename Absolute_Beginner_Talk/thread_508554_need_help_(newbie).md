---
title: "need help (newbie)"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by sp1nter on 2007-07-24
I havent 't been able to find what im looking for when I search for it so ...whenever I hit ctrl-alt-f1 the font is extremely large and i can only read about half the screen. Dont know what to do at this point. Any advice would be greatly appreciated.

---

### Post by sp1nter on 2007-07-24
Oh and I am using feisty with intel i915 card

---

### Post by sp1nter on 2007-07-24
bump ^^

---

### Post by dca on 2007-07-24
I have Intel 945 in my laptop which required the i915resolution package from the repos to get my normal resolution....

---

### Post by sp1nter on 2007-07-24
nope still not working

---

### Post by sp1nter on 2007-07-24
oh and btw the resolution on my desktop is fine

---

### Post by Foxmike on 2007-07-24
You can try the following in order to use vga resolution in framebuffer (terminal):
```
sudo gedit /boot/grub/menu.lst
```
then you find the line that specifies the kernel to use by GRUB, and you add
```
vga=792
```
at the end of this line.  Reboot.  That should do the trick!:)

---

### Post by Majorix on 2007-07-24
How do you mean ctrl+alt+f1? Doesn't it drop you into the terminal? :confused:

---

### Post by sp1nter on 2007-07-24
> **Majorix said:**
> How do you mean ctrl+alt+f1? Doesn't it drop you into the terminal? :confused:

yup and its all warped like zoomed in ... I wish i could screen shot it

---

### Post by sp1nter on 2007-07-24
still not working though

---

### Post by sp1nter on 2007-07-24
> **Foxmike said:**
> You can try the following in order to use vga resolution in framebuffer (terminal):
```
sudo gedit /boot/grub/menu.lst
```
then you find the line that specifies the kernel to use by GRUB, and you add
```
vga=792
```
at the end of this line.  Reboot.  That should do the trick!:)

is this what it should look like 

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d4c303e8-d26e-4278-befa-0a33175282f3 ro quiet splash vga=792
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d4c303e8-d26e-4278-befa-0a33175282f3 ro single vga=792
initrd		/boot/initrd.img-2.6.20-16-generic

---

### Post by Foxmike on 2007-07-24
Actally, you can drop the "vga=792" on the second one (recovery mode), it is not necessary.  But yes, this is how it should look like.

---

### Post by sp1nter on 2007-07-24
what im getting when I restart now is 

undefined mode number then 
video adapter VESA VGA

and then it list a bunch of options for me to pick form but i dont know what pick

---

### Post by Foxmike on 2007-07-24
Ok so then you should remove that vga option.  Out of curiosity, what is your video card?

---

### Post by sp1nter on 2007-07-24
intel 82865G so i believe it should be i810 under dpkg 

i think

---

### Post by sp1nter on 2007-07-24
lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
01:01.0 Communication controller: Conexant HSF 56k Data/Fax Modem
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

---

### Post by Foxmike on 2007-07-24
OK.  What is your preffered resolution? vga=792 stants for 1024x768x24.  I'll do a little research on the other options to check the other resolution settings.  Since then you should just remove that option and keep going with 640x480 resolution.  You can also check arout to find vesa framebuffer resolutions, I'll check tonight.

---

### Post by sp1nter on 2007-07-25
right now I have it set to 1024x768

---

### Post by sp1nter on 2007-07-25
whenever i boot into recovery I don' know whats going on still...it's getting annoying. Also when I boot normally I have a black screen and also when I shutdown. 

I also didnt have this problem in dapper

---

### Post by sp1nter on 2007-07-25
any one else have sugestions

---

### Post by sp1nter on 2007-07-27
guess not
:(

---

