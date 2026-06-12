---
title: "Partition Question"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by CosmicFlux on 2007-12-01
Hi,

OK, I had Linux as a dual-boot with Windows Vista. I now feel confident enough with Linux to switch over to it full-time. I've deleted the Vista partition, and am now left with 60GB of unallocated space. How do I allocate the space Vista used to Linux?  

Also, is there a way I can stop the GRUB loader showing the list of OS's as there is now only Linux?

CosmicFlux

---

### Post by sandysandy on 2007-12-01
> **CosmicFlux said:**
> Hi,

OK, I had Linux as a dual-boot with Windows Vista. I now feel confident enough with Linux to switch over to it full-time. I've deleted the Vista partition, and am now left with 60GB of unallocated space. How do I allocate the space Vista used to Linux?  

Also, is there a way I can stop the GRUB loader showing the list of OS's as there is now only Linux?

CosmicFlux

Post output of [COLOR="Blue"]sudo fdisk -lu[/COLOR]

---

### Post by bumanie on 2007-12-01
Not sure about the second part of your question, but to increase your partition size, download gprated live cd. It has a GUI to follow with slide windows etc. It will be able to increase your partition size by choosing the resize/move option.

---

### Post by CosmicFlux on 2007-12-01
Well, I've got the Partition Editor and I'm logged in as root but the resize/move option is greyed out and there is a padlock icon on all Linux partitions...

---

### Post by jken146 on 2007-12-01
You just need to create a partition in the empty space you got from removing Windows.  Use gparted as root.  You can choose any filesystem you like, but a linux one like ext3 is probably best.  Gparted will format it for you when you apply the changes.  Leave your existing linux partitions alone!

---

### Post by Zzl1xndd on 2007-12-01
Its been a while but I think all you have to do is click on the unallocated and then it should allow you to use the resize option. the ones that are locked is because they the are mounted.

---

### Post by Don1500 on 2007-12-01
> Also, is there a way I can stop the GRUB loader showing the list of OS's as there is now only Linux?


in terminal
```
sudo gedit /boot/grub/menu.lst 
```


First: Set the time out to "0"

[B]## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		0[/B]

Next:
Put your UBUNTU loader option first on the list. (DO NOT COPY THIS!  USE THE LOADER IN YOUR MENU.LST, this is just an example of what to look for.)

[B]title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic Root=UUID=bf265bab-b34f-4822-be35-831132a4e60c ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
[/B]

This will boot Ubuntu after a "0" second time out
You could take the timeout out, but you may want to dual boot again so you can readjust it if you want later.


I would make a copy of the original menu.lst first.....Just in case.

---

### Post by bodhi.zazen on 2007-12-01
1. you can reclaim the unallocated space with gparted, BUT you should do this from a live CD.

Just re-size the ubuntu root partition. You will need a newer version of gparted to do this, either the gutsy version of Ubuntu or download the gparted live CD 

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)
	Download: [Download Gparted](http://easynews.dl.sourceforge.net/sourceforge/gparted/gparted-livecd-0.3.4-8.iso)

=================

As far as you boot menu goes, you need to edit /boot/grub/menu.lst

```
gksu gedit /boot/grub/menu.lst
```

Go ahead and delete the stanzas referring to windows, they look like this ;

> title Windows
make active
chainloader +1
boot

Although the exact syntax will vary. You can delete those lines.

---

### Post by CosmicFlux on 2007-12-01
OK, got it!

Thanx Guys.

Cosmic

---

### Post by meierfra on 2007-12-01
> set the time out to "0"

I wouldn't recommend that. You won't be able to get into recovery mode if you ever need to. Use 

"timeout 1"

---

### Post by Don1500 on 2007-12-01
Ya, I thought of that, That's why I left the timer in, I guess "1" would be better, However, now he knows how to play with menu.lst!

---

