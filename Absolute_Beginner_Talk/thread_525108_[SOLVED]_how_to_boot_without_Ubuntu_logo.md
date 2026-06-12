---
title: "[SOLVED] how to boot without Ubuntu logo?"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by Diabolis on 2007-08-13
I have a dual boot in my laptop with ubuntu/xubuntu. When I pick my ubuntu installation through grub, a ubutnu logo and a orange bar will appear. For some reason the boot up time is taking longer than usual(only with ubuntu), the orange bar hangs at 2 spots for around 5 or 10 seconds each. So what I want to know is if I can use a command or something while booting, so the logo and the orange bar won't appear. In that way I can look to what is going on when the boot up hangs.

---

### Post by Arisna on 2007-08-13
I think if you press Alt+F4 or one of the other F# keys during the boot process, you'll be dropped to a text readout of what the system is doing.  I believe you can turn off the bootsplash completely by editing your bootloader configuration, but that probably isn't necessary if you just want to troubleshoot a couple of problems.  If you get stuck in one of the text screens, your graphical login will appear at Alt+F7.  To get to one of these consoles from the graphical part of the system, use Ctrl+Alt+F#.

---

### Post by diatribe on 2007-08-13
also if you edit /boot/grub/menu.lst to not include the 'quiet' and 'splash' options it will just give you a verbose text readout

---

### Post by mcduck on 2007-08-14
> **diatribe said:**
> also if you edit /boot/grub/menu.lst to not include the 'quiet' and 'splash' options it will just give you a verbose text readout
..or if you just remove the "quiet" but leave "splash", you get a graphical boot _with_ boot texts :)

---

### Post by graigsmith on 2007-08-14
the easiest way to turn off the boot splash thing is just to remove it.

sudo apt-get remove usplash

---

### Post by vexorian on 2007-08-14
btw, this is not going to speed up your boot process, it would be good however to disable it so you can see what is the booting section in which it freezes...

---

### Post by mali2297 on 2007-08-14
> **Diabolis said:**
> I have a dual boot in my laptop with ubuntu/xubuntu. When I pick my ubuntu installation through grub, a ubutnu logo and a orange bar will appear. For some reason the boot up time is taking longer than usual(only with ubuntu), the orange bar hangs at 2 spots for around 5 or 10 seconds each. So what I want to know is if I can use a command or something while booting, so the logo and the orange bar won't appear. In that way I can look to what is going on when the boot up hangs.

Do you mean that the boot up time for xubuntu is significantly shorter? 

In that case, can anyone explain why?

I might consider changing my ubuntu flavour to xubuntu.

---

### Post by Diabolis on 2007-08-16
Removing quiet and/or splash from /boot/grub/menu.lst didn't work, pressing alt+f4 while booting up worked, but I think the best way (the one I liked the most and that I would recommend) is to remove usplash. thanks all for their help.

About xubuntu being faster, I guess it is, but I wouldn't say significantly at least in my computer. I'm not sure how different they are but basicallly xubuntu comes with xfce desktop and ubuntu uses gnome which is pretty good. If you want to boot really quick then try fluxbox, I've been using it for a few days and its pretty light. You could even try fluxbuntu.

---

