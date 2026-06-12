---
title: "Kubuntu CD boots to LCD &quot;out of range&quot; error"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by OneLinux on 2007-06-21
The normal boot and the minimal graphical boot options both make my LCD give an "Out of Range" error and I can't do anything from that point. <CTRL>+F1 gives a garbled unusable screen and <CTRL>+backspace goes to a blank screen where nothing responds.

I have a 17" Fujiplus 4:3 monitor with a native res. of 1024x768 and 60Hz which should be pretty vanilla, but I can't get into Kubuntu. My graphics card is an AGP NV 6600GT and is hooked to the monitor using a standard VGA cable.

I'm SOL unless someone here can help me.

Thanks!

---

### Post by Rocket2DMn on 2007-06-21
If you are looking to install Kubuntu, since you are having screen issues (this is not uncommon), we would recommend downloading and using the alternate cd.

---

### Post by OneLinux on 2007-06-21
But the Alternate CD is not the same as the standard Kubuntu install... what will I need to do to make it equal to the regular edition once installed?

---

### Post by OneLinux on 2007-06-22
Still no dice, I downloaded and installed the Alternate CD, and it still goes to an "out of range" error. It has to be something with the refresh rate because the only resolutions that were chosen were correct. This is truly frustrating, Fedora 7 and Mandriva Spring have no problem whatsoever.

If anyone can offer any advice I'd appreciate it, otherwise I'm going to have to give up on Ubuntu until this gets sorted out.

---

### Post by confused57 on 2007-06-22
> **OneLinux said:**
> Still no dice, I downloaded and installed the Alternate CD, and it still goes to an "out of range" error. It has to be something with the refresh rate because the only resolutions that were chosen were correct. This is truly frustrating, Fedora 7 and Mandriva Spring have no problem whatsoever.

If anyone can offer any advice I'd appreciate it, otherwise I'm going to have to give up on Ubuntu until this gets sorted out.

You might try booting without the quiet & splash boot options in your kernel line...highlight your Ubuntu entry, press "e", highlight your kernel line, press "e" again, then remove the quiet & splash options(then I think you may have to press "enter"), then press "b" to boot...may not work, but worth trying.
At least you should be able to access a console by pressing "Ctrl+Alt+F1", then you can open your /etc/X11/xorg.conf & check your monitor options.

---

### Post by OneLinux on 2007-06-23
Nope <CTRL>+<ALT>+F1 dumps me to the CLI but the screen is all garbled and unusable. I don't get it, this is the first version of Ubuntu to have this issue on this setup, and all of the other current distros handle it fine. It is a pretty straight forward setup:

NV 6600 GT
Fuji Plus 17" LCD
Albatron KDS PRO (nForce 2 mobo)
1Gb Dual channel 400Mhz DDR
Athlon XP 2700+ (No OC)
Maxtor 320 GB IDE HDD
Liteon DVD/rw IDE

I'm at a loss.

---

### Post by kevdog on 2007-06-23
There is probably something you need to modify in your /etc/X11/xorg.conf file --- that would be my first guess.

Can you boot into a terminal or command line mode.  If you can, then its possible to edit the file above.

---

### Post by OneLinux on 2007-06-23
I booted into the recovery mode and edited my xorg.conf... it has detected my video card right and it is set to nv, and then I set my monitor up with the proper ranges for refresh rates and save the file and startx, it goes right to "out of range."

Then I tried dpkg-reconfigure xserver-xorg and again selected these values and used the medium and advanced monitor setup... both times it went straight to "Out of range."

I thought for sure one of them would work, but nothing. Any other thoughts?

---

### Post by confused57 on 2007-06-23
> **OneLinux said:**
> I booted into the recovery mode and edited my xorg.conf... it has detected my video card right and it is set to nv, and then I set my monitor up with the proper ranges for refresh rates and save the file and startx, it goes right to "out of range."

Then I tried dpkg-reconfigure xserver-xorg and again selected these values and used the medium and advanced monitor setup... both times it went straight to "Out of range."

I thought for sure one of them would work, but nothing. Any other thoughts?
One thing you might try is to set the default color depth to 16, instead of 24...worth a try.

Another thing you might try is to run "sudo dpkg-reconfigure xserver-xorg"  & select "no" for framebuffer device.

---

