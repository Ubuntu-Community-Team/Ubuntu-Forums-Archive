---
title: "Grub/boot issue"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by nick24 on 2007-02-26
Hi there 

I finally installed LInux on  a secondary hard drive- like /dev/sdb. Right now windows and linux run like charm. Except for a slight  inconvenience. You see I chose to install Grub in the same HD where I installed Linux thinking Grub will let me choose which OS to boot to and it does, but when I try to run windows it tells me NTLDR not found :).  Well I understand that since NTLDR only excists in /sda.  Right now if I want to boot in to windows I have to go in to BIOS and change the prority everythime and that sucks lol. Is there anyway I can boot both OS'es and  stlill keep NTLDR and GRUB separate. I really appreciate some help here. Thanks

---

### Post by netkid91 on 2007-02-26
You have every right to be confused.  Can you open you grub configuration file (/boot/grub/menu.lst) and find the section that describes your windows boot procedure and post it here (if you can't figure it out post the whole file).

---

### Post by nick24 on 2007-02-26
Thankyou for your reply 

Here is the whole boot menu list 

timeout 10
color black/cyan yellow/cyan
shade 1
viewport 3 2 77 22
splashimage (hd0,5)/boot/grub/splash.xpm.gz
default 0

title linux
kernel (hd0,5)/boot/vmlinuz root=/dev/sdb6  resume=/dev/sdb5 splash=silent vga=788
initrd (hd0,5)/boot/initrd.img

title linux-nonfb
kernel (hd0,5)/boot/vmlinuz root=/dev/sdb6  resume=/dev/sdb5
initrd (hd0,5)/boot/initrd.img

title failsafe
kernel (hd0,5)/boot/vmlinuz root=/dev/sdb6  failsafe resume=/dev/sdb5
initrd (hd0,5)/boot/initrd.img

title windows
root (hd1,0)
map (0x81) (0x80)
map (0x80) (0x81)
makeactive
chainloader +1

title windows1
root (hd1,1)
map (0x81) (0x80)
map (0x80) (0x81)
makeactive
chainloader +1

title windows2
root (hd0,0)
makeactive
chainloader +1

---

### Post by netkid91 on 2007-02-26
Try booting into Windows2, I think it might be an issue with GRUB mapping your first drive when it doesn't need to.

---

### Post by nick24 on 2007-02-26
Thanks for your instant reply 

I will try that and I will let you know if it works

---

### Post by nick24 on 2007-02-26
Hey there 

I am still getting the same error - this time it is "NTLDR is missing press CTRL+ALT+DEL to restart" 

hhhmmm I dont know what else to do :) Thanks for you attempt to help me thogh

---

### Post by netkid91 on 2007-02-26
What partition is Windows installed on?  /sda[what?]
Post the output of fdisk -l please.

---

### Post by nick24 on 2007-02-26
and how I do I that in linux ???

---

### Post by netkid91 on 2007-02-26
Do what?  Edit the file?
sudo gedit /boot/menu/menu.lst
Output of fdisk -l?
fdisk -l, copy the stuff from the terminal

---

### Post by KIFIKA on 2007-02-26
> **nick24 said:**
> Hey there 

I am still getting the same error - this time it is "NTLDR is missing press CTRL+ALT+DEL to restart" 

hhhmmm I dont know what else to do :) Thanks for you attempt to help me thogh


Hey, what you need to do is run your window's install disk in repair mode, just boot from it and follow instructions and it should reinstall NTLDR.. from what i noticed, this occured to me (when i was using windows) whenever i kept shutting off my computer, without letting windows "properly" shut down.

best regards,

KIFIKA

---

### Post by nick24 on 2007-02-26
Hi there 

Sorry I took so long, still too new to linux lol anyway Windows is installed in dev/sda/2

---

### Post by nick24 on 2007-02-26
Thankyou for you help 

I dont have Windows installation disk since my I have OEM version, thanyou though. I apperciate all you guys. I guess I will keep linuxing for now, I dont need windows that much anyway lol thanks

---

### Post by netkid91 on 2007-02-26
K, undo what I said on the Windows entry (restore hd0,1) and remove the map commands.  it ought to work then.

---

