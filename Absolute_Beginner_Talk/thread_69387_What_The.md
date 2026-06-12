---
title: "What The?"
date: 2005-09-26
forum: Absolute Beginner Talk
---

### Post by jose1986 on 2005-09-26
I just got my cd going and I get nowhere practically with it? It says "install base or default." I can choose either one, it goes through the part right after you hit enter and I get a black screen. I was thinking that ubuntu is just not compatible with my laptop? What should I do?
Please help, I am sick of windows and want to get ubuntu up and running.

---

### Post by Jussi Kukkonen on 2005-09-26
> I was thinking that ubuntu is just not compatible with my laptop?

Possible. Maybe you could tell us the make and model of your laptop -- someone might have some more info?

A faulty disk image is also possible, can you try installing on another machine or installing from another disk?

---

### Post by jose1986 on 2005-09-26
Actualy this is 2nd time and a 2nd disc used for my installation process.  My friend recomended it to me a couple of months ago and I got the same problem.  HP Pavilion zv6000

---

### Post by poofyhairguy on 2005-09-26
My sister's Viao does the same thing. I could never get Ubuntu on there, the best way I can help is point you to SUSE Linux:

[http://www.novell.com/linux/suse/](http://www.novell.com/linux/suse/)

That worked great on hers.

---

### Post by az on 2005-09-26
There are a couple of boot options you can try

It sounds like the framebuffer is not being enabled.

file a bug report, or look for existing bug reports in bugzilla.ubuntu.com
Try these options:

vga=771
noapic nolapic
debian-installer/framebuffer=false
pci=noacpi

(Look at the F-key menus)
example:
linux vga=771
or
linux debian-installer/framebuffer=false

---

### Post by matthew on 2005-09-26
[QUOTE=jose1986]I just got my cd going and I get nowhere practically with it? It says "install base or default." I can choose either one, it goes through the part right after you hit enter and I get a black screen.[/QUOTE]
I had the exact same thing. I got it to work by typing at the prompt> linux vga=771

EDIT: azz beat me to it...

---

### Post by Jussi Kukkonen on 2005-09-27
Or another solution to get you through the installer (assuming that this is a framebuffer problem): Connect an external monitor to your HP (and use the display chooser buttons to select it).

---

### Post by nocturn on 2005-09-27
[QUOTE=jose1986]Actualy this is 2nd time and a 2nd disc used for my installation process.  My friend recomended it to me a couple of months ago and I got the same problem.  HP Pavilion zv6000[/QUOTE]

The zv6000 series is notoriously difficult with Linux.  I think Hoary will not work without massive tweaking (and replacing the kernel).

Can you try the Breezy preview?

---

### Post by jrev on 2005-09-27
What type of CD or DVD are you using to install which distribution version ?

---

### Post by jose1986 on 2005-10-06
Ok so this is weird.  I got Suse started on my laptop and it has to have been like 2 hours for it that it has prepared the drive and formatted it and it is at 100% but the cursor indicates that it is still going.  What should I do?

---

### Post by az on 2005-10-06
[QUOTE=jose1986].  What should I do?[/QUOTE]


Let me mail you a Breezy release candidate cd....

---

### Post by dasunst3r on 2005-10-06
Knowing that your screen is widescreen, I see your problem.  Ubuntu install is not very friendly on widescreens -- my install would show up as some weird, white screen **unless** I type in "framebuffer=false" (if I remember correctly) as the install option.  Give it a shot.

---

### Post by jose1986 on 2005-10-06
Uhhh seeing how **SuSe** supports 3d animation, i used that and cut away from ubuntu which doesn't besides the problem it was giving me.

---

### Post by az on 2005-10-07
[QUOTE=jose1986]Uhhh seeing how **SuSe** supports 3d animation, i used that and cut away from ubuntu which doesn't besides the problem it was giving me.[/QUOTE]
Do you mean hardware acceleration?   Ubuntu does that just as well as Suse.

---

### Post by jose1986 on 2005-10-07
Uhh I am done with ubuntu, I get nowhere.

---

