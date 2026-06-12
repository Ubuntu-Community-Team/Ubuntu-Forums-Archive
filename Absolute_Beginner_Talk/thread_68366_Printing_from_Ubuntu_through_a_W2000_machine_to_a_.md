---
title: "Printing from Ubuntu through a W2000 machine to a printer"
date: 2005-09-22
forum: Absolute Beginner Talk
---

### Post by Wardley.Fish on 2005-09-22
Here is the Deal

I need to use my Shared Printer that is nailed to the back of a Windows 2000 machine.  I read somewhere that I need to install and configure SAMBA, odd name but who am I to comment.

I went to the SAMBA site and downloaded the package and started to read the installations instructions.

Is Ubuntu really "linux for human beeings" as, being a human, I can't even figure how to install the package, I may in fact already have it installed!!

Is there a human out there who can point me in the right direction?

Warfley

---

### Post by bsussman on 2005-09-22
Survival tip # 2.34:  install package 'xxx' will almost always mean 'use Synaptic to install the ubuntu package 'xxx'.


All linux names are puns or otherwise weird.  ;-)

Samba is linux implementation of the SMB protocol - the Windows way of sharing files and printers.

It is probably running already and you just have to share the printer out on the w2k box and configure properly on the ubuntu box

The first part (share on w2k) is done on the box where the printer lives in the printers manager.

are you using gnome or KDE - the printer config program is different and I do not remember the gnome name

---

### Post by Wardley.Fish on 2005-09-22
[QUOTE=bsussman]are you using gnome or KDE - the printer config program is different and I do not remember the gnome name[/QUOTE]

I believe I am using gnome, whatever comes with Ubuntu.  I haven't changed anything in fact I don't think I could if I wanted to.  :???: 

Wardley

---

### Post by bsussman on 2005-09-23
ok - I just booted the live cd - the installed sys should be the same.

System => Administration => Printing => Install New Printer.

Fill out with the name W2K box, the name you assigned the shared printer and the security info you input when you set it up - my W2k system (oh the shame...) does not allow access without a user/password, and continue configuring.

There may still be a problem or two (in fact, I have not yet seen my test page :??)

I suggest you look at this: [http://ubuntuforums.org/showthread.php?t=32190]("http://ubuntuforums.org/showthread.php?t=32190")

the Windows end should be close and the ubuntu end the same.

---

