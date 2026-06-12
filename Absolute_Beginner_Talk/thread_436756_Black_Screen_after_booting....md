---
title: "Black Screen after booting..."
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by Dre521 on 2007-05-08
A pleasant day everyone. I'm Andrei from the Philippines. I already managed  to use Ubuntu before but it is my first time to install it on my PC. I installed Ubuntu 7.04 on my old HP Pavilion 7840 PC. My PC has an Nvidia GeForce 2 MX400 PCI video card installed. The problem is that after the boot screen (?) the screen turns black for a long time, as if it has already stalled.

I read somewhere in the forums that 7.04 has some compatibility issues regarding GeForce 2 video cards. As of typing this, my old PC is still running, and it still black.

Here's some of the specs of my Pavilion 7840. I hope this helps figuring out the problem.

Motherboard: Trigem Cognac
Processor: Intel Pentium III 766MHz socket 370 Coppermine
Memory: 2 x 128MB SDRAM PC133
Video Card: Nvidia  GeForce 2 MX400 PCI 64MB

I hope guys and gals can help me regarding my situation. Thank you.

---

### Post by Ozeuss on 2007-05-08
is ubuntu the only OS installed? do you see the grub menu? did you try booting into safe mode?

---

### Post by useResa on 2007-05-08
It could indeed be the setup of your Nvidia card.

What you could try is the following:
When you start your PC a message comes up indicating that you can get the menu if you press ESC. Press ESC so you get the menu.
Next start Ubuntu in recovery mode.
It will stop to allow you to do maintenance (give the password if so asked).
Next change the directory by giving the following command
```
cd /etc/X11
```
Now -- for safety -- copy the xorg.conf file so you have the original one as a backup.
You can do this by issuing the command
```
cp xorg.conf xorg.conf.mybackup
```
Of course you can give the file any name you want the name xorg.conf.mybackup is just a suggestion ;)
Now edit the xorg.conf file (so at least you can startup later and to make sure it is your video driver that is causing the problem), by issuing the command
```
nano xorg.conf
```
Now look for the following text in the file (you can use your page down button to find it)
> Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection
And change nvidia into nv
Next press CTRL and O to save the file (you have to hit Enter to confirm the name of the file) and press CTRL and X to exit.
Now restart your computer by issuing the command```
shutdown -r now
```

If the video driver was the problem you should be able start Ubuntu (although of course not with the full support of your video card yet). But if this works, we can continue from there on.

I hope the explanation is clear and that this will help.

---

### Post by Dre521 on 2007-05-09
Thank you for all the help. I manage to trace the problem and it is in fact, my video card.

useResa, I did not find the
> Section "Device"
Identifier "NVIDIA Corporation NVIDIA Default Card"
Driver "nvidia"
EndSection

in the xorg.conf file. However, instead of finding it, I found this:
> Section "Device"
Identifier "Intel Corporation 82810 CGC [Chipset Graphics Controller]"
Drive "i810"
BusID "PCI:0:1:0"
EndSection

It seems during the installation, my video card was not detected and instead, the built-in video card of my motherboard was the one detected. I changed the entry in the Section "Device" using the one you suggested. However, the problem did not end there. It still has a problem, and it seems Ubuntu still searches for my built-in video card.

I tried to study the file once again and found this on the Section "Screen":
> Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82810 CGC [Chipset Graphics Controller]"

I changed the entry in the Device "Intel Corporation 82810 CGC [Chipset Graphics Controller] to
> Device "NVIDIA Corporation NVIDIA Default Card"

And guess what, it finally worked. Inside Ubuntu, I managed to get the driver installed. Thanks guys for the help. I appreciate it. I hope this will also help the others who have this problem.

Hehehe... now to get that modem working...

Again, thank you. :)

---

### Post by useResa on 2007-05-09
My compliments on how you achieved to resolve this issue.
Well done!!

Maybe you can get even more out of your Nvidia Geforce card, by reading [this post]("http://ubuntuforums.org/showthread.php?t=432056") by tselliot (who really is a guru on Nvidia).

---

