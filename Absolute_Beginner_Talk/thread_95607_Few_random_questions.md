---
title: "Few random questions"
date: 2005-11-26
forum: Absolute Beginner Talk
---

### Post by Glass Casket on 2005-11-26
I've been wondering about a few things for a very long time:

1. Does Linux have to reboot 10000 times when installing new software?

2. Is there a hardware compatibility list?

3. What is the difference between the 4-5 different Ubuntu's?

Thanks.

---

### Post by Qrk on 2005-11-26
1) No. You need to reboot after kernel upgrades only.
2) No, not an official one. Try a live CD to make sure your hardware works before installing. If some things don't work automatically, its usually not too bad to get them to.
3) The difference between Xubuntu, Kubuntu and Ubuntu is the GUI, thats it. 5.10 is the current version.

---

### Post by 23meg on 2005-11-26
Check this link out for Ubuntu hardware support:

[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

---

### Post by Glass Casket on 2005-11-27
Thank you.

Edit: You must be kidding me. I checked if it supported my graphics card (ATI X300) and my printer (Brother HL-2040) and it dosen't!

---

### Post by Glass Casket on 2005-11-27
Also, which version is more suitable for a Linux n00b?

---

### Post by 23meg on 2005-11-27
Of Ubuntu? The latest stable version is Breezy (5.10) so it's most likely what you should be using.

---

### Post by Gustav on 2005-11-27
[QUOTE=Glass Casket]Thank you.

Edit: You must be kidding me. I checked if it supported my graphics card (ATI X300) and my printer (Brother HL-2040) and it dosen't![/QUOTE]
That it is not in the list does not mean that it isn't supported! It just means that no-one that have the hardware have tested it and added it to the list.

The lists are not complete and your best shot is to look at similar hardware that hopefully exists on the lists.

---

### Post by aysiu on 2005-11-27
Brother HL-2040 is not, in fact, supported.
My Brother HL-1240 is, though.
My wife has the HL-2040, and, as I recall, it's fairly new.
I did spot a driver for HL-2060.

---

### Post by Glass Casket on 2005-11-27
[QUOTE=aysiu]Brother HL-2040 is not, in fact, supported.
My Brother HL-1240 is, though.
My wife has the HL-2040, and, as I recall, it's fairly new.
I did spot a driver for HL-2060.[/QUOTE]

Yeah, it is fairly new. I'll probaply have to wait.

On their site it says that it only supports Redhat, Mandriva (Mandrake), SuSE, Debian and FedoraCore.

Another reason why i'll have to keep Windows. Also, when you're logged into Linux, is there a way to open a window or something with XP in it. So if I want to print, I don't have to log off Linux, and log into Windows?

---

### Post by astronerd on 2005-11-27
[QUOTE=Glass Casket]
Edit: You must be kidding me. I checked if it supported my graphics card (ATI X300) and my printer (Brother HL-2040) and it dosen't![/QUOTE]


I have an ATI X300 on my comp that works fine, so its supported.

---

### Post by aysiu on 2005-11-27
[QUOTE=Glass Casket]Also, when you're logged into Linux, is there a way to open a window or something with XP in it. So if I want to print, I don't have to log off Linux, and log into Windows?[/QUOTE] VMWare? By the way, I just did a quick Google search for *brother hl-2040 linux* and the first result was a support page on the Brother website with a link to [the .deb driver for the HL-2040 printer](http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/brhl2040lpr_1.1.2-3_i386.deb). Download that to your desktop and open a terminal and type in ```
cd Desktop
sudo dpkg -i brhl2040lpr_1.1.2-3_i386.deb
``` Any luck?

---

### Post by ssam on 2005-11-27
[QUOTE=Glass Casket]Another reason why i'll have to keep Windows. Also, when you're logged into Linux, is there a way to open a window or something with XP in it. So if I want to print, I don't have to log off Linux, and log into Windows?[/QUOTE]

there are a few programs like that, qemu, boch and vmware, though i am not sure if you could get access to the printer from with in them.

---

### Post by Glass Casket on 2005-11-29
I haven't actually isntalled it yet. I am waiting to order an external hardrive.

Another question, is I order an external hardrive. Will I be able to partition it and install Linux on it? If so, can I pick any external drive?

Thanks

Mike

---

### Post by Glass Casket on 2005-11-30
Funny, because I pick the one that the live CD suggests, even though it's not the one for my printer. And it worked!

Also, do you download Kubuntu? Or do you install Ubuntu and download KDE?

---

### Post by solarcontrol on 2005-12-01
Either - though I imagine there is some advantage to  getting  Kubuntu.

---

### Post by Glass Casket on 2005-12-03
Thank you all

---

