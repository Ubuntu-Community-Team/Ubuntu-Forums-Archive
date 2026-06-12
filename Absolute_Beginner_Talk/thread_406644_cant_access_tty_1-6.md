---
title: "cant access tty 1-6"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by halo6819 on 2007-04-11
Hey guys, brand new to linux (loaded up edgy last Monday) trying to install new video drivers for my video card, but to do that i have to stop GDM and run the nvidia driver. only when i go to a TTY all i get is video garbage. I have tried modifying the grub menu adding vga=791 and many other values, but when i do that grub gives me an error 
You passed an undefined mode number

i have a dell optiplex gx110 with built in video, i had to disable the secondary card that i have (nvidia mx440) until l get the drivers installed because that card wont load ubuntu at all.

any help would be greatly appreciated!

---

### Post by cantormath on 2007-04-11
You can kill gdm this way.....

open a terminal

```
~$ sudo /etc/init.d/gdm stop
```

to start it again

```
~$ sudo /etc/init.d/gdm start
```

---

### Post by justleen on 2007-04-11
im assuming you access the tty the normal way, CTRL-ALT- 1/6 ?

did you try VGA=normal by any chance to?

---

### Post by halo6819 on 2007-04-11
yes, i am trying to access tty via CTRL + ALT + F1/6

just tried VGA=normal, no go

also when i tried shutting down gdm, same screen garbage, and couldnt restart gdm

---

### Post by pxwpxw on 2007-04-11
use recovery mode, or
single
or linux single
in kernel parameterrs
then edit /etc/rc2.d to temporarily kill gdm,
then starts up in console,

edit that should have been rc2,d sorry.
and not edit but change @Sxxgdm to @Kyygdm
where yy=100-xx

---

### Post by halo6819 on 2007-04-11
im sorry but i didnt understand anything you just said...

---

### Post by pxwpxw on 2007-04-11
> **halo6819 said:**
> im sorry but i didnt understand anything you just said...

My bad. 
When you restart, the grub menu should show a "recovery" or rescue item.
That will start you as root in a text console.

Then if you do
```

~$ ls -l /etc/rc2.d
total 4
-rw-r--r-- 1 root root 556 2006-10-06 22:34 README
lrwxrwxrwx 1 root root  16 2007-04-03 16:07 S01apport -> ../init.d/apport
lrwxrwxrwx 1 root root  17 2007-04-03 16:07 S05vbesave -> ../init.d/vbesave
lrwxrwxrwx 1 root root  15 2007-04-03 16:07 S10acpid -> ../init.d/acpid
lrwxrwxrwx 1 root root  25 2007-04-03 16:09 S10powernowd.early -> ../init.d/powernowd.early
lrwxrwxrwx 1 root root  18 2007-04-04 00:35 S10sysklogd -> ../init.d/sysklogd
lrwxrwxrwx 1 root root  15 2007-04-04 00:35 S11klogd -> ../init.d/klogd
lrwxrwxrwx 1 root root  13 2007-04-03 16:21 S13gdm -> ../init.d/gdm
lrwxrwxrwx 1 root root  16 2007-04-03 16:17 S19cupsys -> ../init.d/cupsys
lrwxrwxrwx 1 root root  15 2007-04-03 16:17 S19hplip -> ../init.d/hplip
lrwxrwxrwx 1 root root  14 2007-04-03 16:07 S20apmd -> ../init.d/apmd
lrwxrwxrwx 1 root root  14 2007-04-03 16:07 S20dbus -> ../init.d/dbus
lrwxrwxrwx 1 root root  21 2007-04-03 21:14 S20firestarter -> ../init.d/firestarter
lrwxrwxrwx 1 root root  13 2007-04-03 15:43 S20gpm -> ../init.d/gpm
lrwxrwxrwx 1 root root  22 2007-04-03 16:09 S20hotkey-setup -> ../init.d/hotkey-setup
lrwxrwxrwx 1 root root  17 2007-04-04 00:33 S20makedev -> ../init.d/makedev
lrwxrwxrwx 1 root root  19 2007-04-03 16:09 S20powernowd -> ../init.d/powernowd
lrwxrwxrwx 1 root root  15 2007-04-04 00:38 S20rsync -> ../init.d/rsync
lrwxrwxrwx 1 root root  13 2007-04-11 21:36 S30mpd -> ../init.d/mpd
lrwxrwxrwx 1 root root  17 2007-04-03 16:07 S89anacron -> ../init.d/anacron
lrwxrwxrwx 1 root root  13 2007-04-04 00:38 S89atd -> ../init.d/atd
lrwxrwxrwx 1 root root  14 2007-04-04 00:38 S89cron -> ../init.d/cron
lrwxrwxrwx 1 root root  17 2007-04-03 16:16 S98usplash -> ../init.d/usplash
lrwxrwxrwx 1 root root  22 2007-04-03 16:07 S99acpi-support -> ../init.d/acpi-support
lrwxrwxrwx 1 root root  18 2007-04-04 00:33 S99rc.local -> ../init.d/rc.local
lrwxrwxrwx 1 root root  19 2007-04-04 00:33 S99rmnologin -> ../init.d/rmnologin
lrwxrwxrwx 1 root root  24 2007-04-03 16:09 S99stop-readahead -> ../init.d/stop-readahead
~$ 

```
the line :
lrwxrwxrwx 1 root root  13 2007-04-03 16:21 S13gdm -> ../init.d/gdm

 
you can change the link name from
S13gdm
to
K87gdm

which will kill gdm at runlevel 2, which is the normal startup level.

Is that ok so far?

---

### Post by halo6819 on 2007-04-11
ill give it a shot :)

---

### Post by halo6819 on 2007-04-11
i restarted, and went into what i believe is recovery mode, i was able to pull up the list, but cant figure out how to change

thanks for all your help and patience

---

### Post by pxwpxw on 2007-04-11
I will detail that,
just need to check it first.

---

### Post by pxwpxw on 2007-04-11
Like this:
```

root@oldibm:# ls /etc/rc2.d/*gdm
/etc/rc2.d/S13gdm
root@oldibm:# mv /etc/rc2.d/S13gdm /etc/rc2.d/K87gdm
root@oldibm:# ls /etc/rc2.d/*gdm
/etc/rc2.d/K87gdm
root@oldibm:# 

```

---

### Post by halo6819 on 2007-04-11
no luck. when i tried doing what you said ubuntu didnt load at all, just screen garbage

---

### Post by pxwpxw on 2007-04-11
> **halo6819 said:**
> no luck. when i tried doing what you said ubuntu didnt load at all, just screen garbage

Seems to confirm the screen problem is not caused by running gdm.
 
Was there any screen problem  using the recovery optiion?

The change can be reversed from the recovery console.

What have you got the vga=   set to in the menu, you can check this by selecting 'e' for edit when the grub menu comes up at restart, and compare what is in the rescue setting.

And are you using the Desktop or the Alternate install CD?

What is your monitor screen resolution?

I am checking the valid vga=xxx setings and the rescue options  here, will comeback.

Edit:
Was the nvidia card disabled before the ubuntu install?
Were the text consoles ever usable after the installation?

---

### Post by confused57 on 2007-04-11
You can try what pxwpxw suggested, at the grub boot menu, highlight your Ubuntu entry , press "e", then in your kernel line take out the word splash, then press "b" to boot.
Once you've booted into Ubuntu, then try to access a console.

---

### Post by pxwpxw on 2007-04-12
Some valid linux vesa mode numbers are, for 8 bit:

vga=769  640x480
vga=773  1024x768
vga=775  1280x1024 
vga=796  1600x1200

[http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#VESA_video_mode_numbers](http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#VESA_video_mode_numbers)

---

### Post by halo6819 on 2007-04-12
> **pxwpxw said:**
> Seems to confirm the screen problem is not caused by running gdm.
 
Was there any screen problem  using the recovery optiion?
no, everything worked fine in recovery.

> **pxwpxw said:**
> 
The change can be reversed from the recovery console.

What have you got the vga=   set to in the menu, you can check this by selecting 'e' for edit when the grub menu comes up at restart, and compare what is in the rescue setting.
i have tried multiple settings for the vga= tag i dont remember all of them... i also tried  vga=normal, no luck

> **pxwpxw said:**
> And are you using the Desktop or the Alternate install CD?

What is your monitor screen resolution?

using the desktop and my monitors resolution is 1680 x 1050
> **pxwpxw said:**
> 
I am checking the valid vga=xxx setings and the rescue options  here, will comeback.

Edit:
Was the nvidia card disabled before the ubuntu install?
Were the text consoles ever usable after the installation?
[/QUOTE]
NVIDIA card has been disabled from the begining, i wanted to install with it but Ubuntu didnt seem to like that so i disabled it and started using on board just to get the compy running. 
and no, the text consoles never worked, the first thing i did when i got Ubuntu up and running was try and install the NVIDIA driver so i can use the other graphics card.

---

### Post by halo6819 on 2007-04-12
hey everyone, thanks for all your help! either taking out the splash or entering the vga setting to 769 did the trick

THANK YOU SO SO SO SO MUCH!

---

### Post by confused57 on 2007-04-12
> **halo6819 said:**
> hey everyone, thanks for all your help! either taking out the splash or entering the vga setting to 769 did the trick

THANK YOU SO SO SO SO MUCH!

You might want to make the change in your defoptions in your menu.lst:
[http://users.bigpond.net.au/hermanzone/p15.htm#defoptions](http://users.bigpond.net.au/hermanzone/p15.htm#defoptions)
otherwise, a kernel update will add the splash option back.

---

