---
title: "Gnome is nice .. but ..."
date: 2005-09-15
forum: Absolute Beginner Talk
---

### Post by utw-mephisto on 2005-09-15
First : I LOVE Ubuntu .. I already talked to everybody in the company about that, even they did not want to hear it :D :D 

It is the first distr. which found all my hardware on either desktop or laptop.

Anyway.

I have actually two questions : 

How can I achieve that the Linux start straight away into the command line instead of the x-server. As far as I know I can start Gnome with startx anyway, can I ? Anyway, how can I do that :D ? Starting the PC into commandline only upon reboot.

2. How can I change the resolution in the commandline ? When I check certain files it seems I have only 640x320 or 800x600 

Every help is much appreciated ..

Michael

---

### Post by SilentCacophony on 2005-09-15
1. if it were me, I'd try uninstalling gdm, the gnome display manager, since you wouldn't be using it

2. add 'vga=791' to the kernel line in /boot/grub/menu.lst

[Here](http://www.linux.org/docs/ldp/howto/Framebuffer-HOWTO-5.html) is a page that describes the process.

---

### Post by utw-mephisto on 2005-09-15
[QUOTE=SilentCacophony]1. if it were me, I'd try uninstalling gdm, the gnome display manager, since you wouldn't be using it.[/QUOTE]

How do I do it ?!? I mean without leaving some rubbish behind ? 

I would love to see a possibility chose the packages anyway before installing ..

---

### Post by wellery on 2005-09-15
There's this which should tell you how to disable x at boot:


[http://www.ubuntuforums.org/showthread.php?t=58082&highlight=startx](http://www.ubuntuforums.org/showthread.php?t=58082&highlight=startx) 
[http://www.ubuntuforums.org/showthread.php?t=61061&highlight=startx](http://www.ubuntuforums.org/showthread.php?t=61061&highlight=startx)

---

### Post by SilentCacophony on 2005-09-15
You should be able to just remove gdm using synaptic, then next time you boot, it won't go into X.

Personally, I did the minimal 'server' install, then used the aptitude package manager to load up the rest, as I like aptitude's garbage collection. That's a lot of downloading, though.

Also, here is a sample of my boot.lst, for reference:

```
title		Debian GNU/Linux, kernel 2.4.27-2-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.4.27-2-386 root=/dev/hda2 ro vga=794 
initrd		/boot/initrd.img-2.4.27-2-386
savedefault
boot

title		Debian GNU/Linux, kernel 2.4.27-2-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.4.27-2-386 root=/dev/hda2 ro vga=794 single
initrd		/boot/initrd.img-2.4.27-2-386
savedefault
boot
```

It's from debian, but you can see how to add the vga= option

---

### Post by utw-mephisto on 2005-09-15
[QUOTE=SilentCacophony]Personally, I did the minimal 'server' install,[/QUOTE]

You did this also with Debian 3.1 or 3.0 instead of Ubuntu ?

---

### Post by SilentCacophony on 2005-09-15
I was referring to ubuntu there. When you boot the ubuntu cd, you type 'server' and enter, which will start the server install. It's a pretty minimal install, so I can't actually recommend it to most beginners, but I did it shortly after trying the normal install without trouble. You'd have to choose your X environment yourself, such as:

x-window-system-core, xscreensaver, menu, icewm, xterm, rox-filer

which would give a light-weight desktop, then also install other applications.

If you'd like to try such a thing, I'd recommend doing it on another partition.

---

### Post by utw-mephisto on 2005-09-15
[QUOTE=utw-mephisto]You did this also with Debian 3.1 or 3.0 instead of Ubuntu ?[/QUOTE]
 Just answered the question myself :D

---

### Post by utw-mephisto on 2005-09-15
[QUOTE=SilentCacophony]I was referring to ubuntu there. When you boot the ubuntu cd, you type 'server' and enter, which will start the server install. It's a pretty minimal install, so I can't actually recommend it to most beginners, but I did it shortly after trying the normal install without trouble. You'd have to choose your X environment yourself, such as:

x-window-system-core, xscreensaver, menu, icewm, xterm, rox-filer

which would give a light-weight desktop, then also install other applications.

If you'd like to try such a thing, I'd recommend doing it on another partition.[/QUOTE]

Believe it or not, I am actually a beginner in customizing, but I am more fmailiar with a minimal installation since all my root server I have rented are debian minimal :D

---

### Post by SilentCacophony on 2005-09-15
Good deal, then.

I'm not sure if aptitude is included in the server install, but I'd recommend it if you haven't tried it (can always apt-get it if it's not). It's got a text ui that works pretty well, and it seems to work well with removing things not depended upon after uninstalls. My two favorite controls in it are / for find, and \ for find next.

---

