---
title: "A couple of Xfce issues"
date: 2006-01-21
forum: Absolute Beginner Talk
---

### Post by johnkennethhughes on 2006-01-21
Is there a more elegant way of getting at my USB key ring drive in Xfce than running the "nautilus --no-desktop" command from the terminal? I'm not the only person using this computer and I can't see the others buying my 'Linux is great' routine while they still have to go through a terminal to get at some of their files!

The other issue I have is that I can't open PDF files in Xfce. Again, this isn't going to make me very popular...

Thanks!

---

### Post by localzuk on 2006-01-21
You could place a launcher icon in the bar at the bottom of the screen that runs 'nautilus --no-desktop', and you should be able to open pdfs in any of the pdf viewers such as evince, xpdf or if you want Adobe reader take a look at the ubuntuguide.org site for information on how to install it.

---

### Post by ysse on 2006-01-21
Hi,

In Gnome, USB-drives always have worked for me. I used to believe that USB drives were automounted regardless of what desktop you used, but I was wrong. The reason /media/usbdisk is mounted in Gnome is gnome-volume-manager, a background program that mounts removable media as soon as they're inserted. 

Because you want your USB drive automounted, you need to have gnome-volume-manager started each time you log in to Xfce.

One way could be to run it from "Run Program" and make sure you save your session when you log out. But I find that the Autostart folder is more reliable.

If you create a folder ~/Desktop/Autostart, e.g. /home/hughes/Desktop/Autostart, and put an executable script file inside it, every command in that file will be run when you log in.

I called the script file 'autostart.sh'. What needs to be in it is the command ```
gnome-session-manager
```

Then make sure it is executable. ```
chmod 755 autostart.sh
```

Unmounting you do from the right-click menu on /media/usbdisk.

Well. Now I've tried Xfce for the first time, and it looks pretty. Just to satisfy my curiosity: Why would you recommend Xfce before Gnome or KDE?

Cheers
/Anders

---

### Post by localzuk on 2006-01-21
> Well. Now I've tried Xfce for the first time, and it looks pretty. Just to satisfy my curiosity: Why would you recommend Xfce before Gnome or KDE?

Personally, I use XFCE over gnome due to it being more lightweight - but I only use it on machines that can't handle KDE.

---

### Post by johnraff on 2006-01-23
[QUOTE=ysse]The reason /media/usbdisk is mounted in Gnome is gnome-volume-manager, a background program that mounts removable media as soon as they're inserted. 

I called the script file 'autostart.sh'. What needs to be in it is the command ```
gnome-session-manager
```
[/QUOTE]

I guess that should say
```
gnome-volume-manager
``` ? :)

---

### Post by johnkennethhughes on 2006-01-24
Thanks for that - I'll give it go. And in answer to your question, I've got two reasons for using Xfce:

1. I'm using a very old computer and Gnome slows it down quite a lot.

2. I'm quite new to Linux and I like to try out different things. I thought it might be fun!

Thanks again!

---

