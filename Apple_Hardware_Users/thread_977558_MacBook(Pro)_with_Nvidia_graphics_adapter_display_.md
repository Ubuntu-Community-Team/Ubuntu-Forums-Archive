---
title: "MacBook(Pro) with Nvidia graphics adapter display backlight fix call for testing"
date: 2008-11-10
forum: Apple Hardware Users
---

### Post by _mario_ on 2008-11-10
Hi all,

the display backlight on those models with Nvidia graphics adapter is always at its maximum brightness after resuming from suspend, but the chip, and thus the driver, still reports the last recently set value. This updated driver fixes this issue, by re-sending the value upon suspend. Can anyone please confirm that it actually works?

Instructions:
1. Install the attached deb package and reload the module:
```
sudo dpkg -i mbp-nvidia-bl-dkms_0.11_all.deb
sudo rmmod mbp_nvidia_bl
sudo modprobe mbp_nvidia_bl
```

2. MacBookPro 3 and 4 users: Set display brightness to some low value, e.g.:
```
echo 1 | sudo tee /sys/class/backlight/mbp_backlight/brightness
```, suspend, resume and report whether it works.

3. MacBook 5 and MacBookPro 5 users: This might also work for the new 5th generation models. I don't have these machines and thus cannot test it. Please check out this driver and report whether it works at all.

4. If it didn't work, remove the package:
```
sudo apt-get remove --purge mbp-nvidia-bl-dkms
```

If you want to have a look, the sources are attached as well.

thanks & ciao,
Mario

EDIT: removed attachments. use the mactel PPA instead.

---

### Post by _mario_ on 2008-11-10
> **_mario_ said:**
> 
2. MacBookPro 3 and 4 users: Set display brightness to some low value, suspend, resume and report whether it works.


well, how surprising, of course it works on my MacBookPro 4.

---

### Post by kosumi68 on 2008-11-10
Great work, mario!

I am excited about the possibility that this might actually fix the problem with heat and battery life on the new unibody Macbooks.

---

### Post by hyperboloid on 2008-11-10
> **_mario_ said:**
> 
the display backlight on those models with Nvidia graphics adapter is always at its maximum brightness after resuming from suspend, but the chip, and thus the driver, still reports the last recently set value. This updated driver fixes this issue, by re-sending the value upon suspend. Can anyone please confirm that it actually works?

Instructions:
1. Install the attached deb package and reload the module:
```

sudo dpkg -i mbp-nvidia-bl-dkms_0.11_all.deb
sudo rmmod mbp_nvidia_bl
sudo modprobe mbp_nvidia_bl

```

2. MacBookPro 3 and 4 users: Set display brightness to some low value, e.g.:
```

sudo echo 1 > /sys/class/backlight/mbp_backlight/brightness

```, suspend, resume and report whether it works.

3. MacBook 5 and MacBookPro 5 users: This might also work for the new 5th generation models. I don't have these machines and thus cannot test it. Please check out this driver and report whether it works at all.

4. If it didn't work, remove the package:
```

sudo apt-get remove --purge mbp-nvidia-bl-dkms

```

If you want to have a look, the sources are attached as well.

thanks & ciao,
Mario

It is working *almost* OK on my MBP 4,1 running Ubuntu 8.10 release. Upon reboot/suspend the previous display brightness setting is remembered. 

***One small problem:*** When the brightness is very low, one encounters a black screen upon resume, and at that point (before password verification) the brightness controls are disabled, so one must enter the password blindly and then use the controls to manually up the display brightness. 

This seems like a rounding issue with a floating point variable, although I have not tried to look at the code. Anyway, perhaps a minimum threshold should be something non-zero so that the display will never come back completely black, which is disconcerting. 

By the way, the suggested code in step 2 ```
sudo echo 1 > /sys/class/backlight/mbp_backlight/brightness
``` does not work for me - it gives me back "permission denied" even though I did not forget the "sudo" prefix. Very strange. Anyway, I set the brightness using the manual control F1-F2.

Good work, Mario. Can you similarly figure out a way to make it remember the KEYBOARD backlight settings after suspend/reboot?

---

### Post by ercoppa on 2008-11-10
For me seems not to work on MacBook 5,1 2.0Ghz. The applet on GNOME not change the brightness.
```
ercoppa@ercoppa-laptop:~$ lsmod | grep nvidia
mbp_nvidia_bl          11140  0 
nvidia               6900560  28 
agpgart                42184  1 nvidia
i2c_core               31892  1 nvidia
ercoppa@ercoppa-laptop:~$ modinfo mbp_nvidia_bl 
filename:       /lib/modules/2.6.27-7-generic/updates/dkms/mbp_nvidia_bl.ko
alias:          svnAppleInc.:pnMacBookPro5,1
alias:          svnAppleInc.:pnMacBook5,1
alias:          svnAppleInc.:pnMacBookPro4,1
alias:          svnAppleInc.:pnMacBookPro3,2
alias:          svnAppleInc.:pnMacBookPro3,1
license:        GPL
description:    Nvidia-based Macbook Pro Backlight Driver
author:         Matthew Garrett <mjg@redhat.com>
srcversion:     DBA60E7089F1D0F6F752D48
depends:        
vermagic:       2.6.27-7-generic SMP mod_unload modversions 586 

ercoppa@ercoppa-laptop:~$ sudo echo 1 > /sys/class/backlight/mbp_backlight/brightness 
bash: /sys/class/backlight/mbp_backlight/brightness: Permission denied

root@ercoppa-laptop:/home/ercoppa# echo 1 > /sys/class/backlight/mbp_backlight/brightness 

root@ercoppa-laptop:/home/ercoppa# echo 1 > /sys/class/backlight/mbp_backlight/actual_brightness 
bash: /sys/class/backlight/mbp_backlight/actual_brightness: Permission denied

ercoppa@ercoppa-laptop:~$ sudo echo 1 > /sys/class/backlight/mbp_backlight/brightness 
bash: /sys/class/backlight/mbp_backlight/brightness: Permission denied

ercoppa@ercoppa-laptop:~$ cat /sys/class/backlight/mbp_backlight/brightness 
1
ercoppa@ercoppa-laptop:~$ cat /sys/class/backlight/mbp_backlight/actual_brightness 
15


```

Anyway thanks for the work :)

How can I help you?

---

### Post by cyberdork33 on 2008-11-10
> **hyperboloid said:**
> By the way, the suggested code in step 2 ```
sudo echo 1 > /sys/class/backlight/mbp_backlight/brightness
``` does not work for me - it gives me back "permission denied" even though I did not forget the "sudo" prefix. Very strange
It doesn't work because it is really two different commands... You don't need sudo for the echo command, (you normal user can do that), but you need sudo for '>' command because you are trying to pipe to a protected file.

Try it like this:
```
echo 1 |sudo tee /sys/class/backlight/mbp_backlight/brightness
```

---

### Post by kosumi68 on 2008-11-10
> **hyperboloid said:**
> 
```
sudo echo 1 > /sys/class/backlight/mbp_backlight/brightness
``` does not work for me - it gives me back "permission denied" even though I did not forget the "sudo" prefix. Very strange.


It should read
```

echo 1 | sudo tee -a /sys/class/backlight/mbp_backlight/brightness

```
file pipes do not work with sudo (it is a different command, executed as the normal user)

EDIT: oops - I obviously forgot to refresh my tab :-)

---

### Post by kosumi68 on 2008-11-10
> **ercoppa said:**
> For me seems not to work on MacBook 5,1 2.0Ghz. The applet on GNOME not change the brightness.


Does the thank you to cyberdork's post mean it works for you to change the screen brightness on the MacBook5,1?

---

### Post by ercoppa on 2008-11-10
> Does the thank you to cyberdork's post mean it works for you to change the screen brightness on the MacBook5,1?
The command works (only for /sys/class/backlight/mbp_backlight/brightness) but the brightness doesn't change.

P.s. excuse me for my bad english :(

---

### Post by cyberdork33 on 2008-11-10
> **kosumi68 said:**
> It should read
```

echo 1 | sudo tee -a /sys/class/backlight/mbp_backlight/brightness

```file pipes do not work with sudo (it is a different command, executed as the normal user)

EDIT: oops - I obviously forgot to refresh my tab :-)
Just a small off-topic question... Doesn't the -a switch mean append? Does it make a difference if you append or replace for a sys file like that?

---

### Post by bryonak on 2008-11-10
Confirming that this **works** on a MacbookPro 3.1.
No problems with low values either (the float rounding issue hyperboloid mentioned)

Keep up the good work!

---

### Post by _mario_ on 2008-11-10
Hi,

> **hyperboloid said:**
> 
***One small problem:*** When the brightness is very low, one encounters a black screen upon resume, and at that point (before password verification) the brightness controls are disabled, so one must enter the password blindly and then use the controls to manually up the display brightness. 

This seems like a rounding issue with a floating point variable, although I have not tried to look at the code. Anyway, perhaps a minimum threshold should be something non-zero so that the display will never come back completely black, which is disconcerting.
that's interesting. the brightness values are indeed integral values. there's no floating point at all. and on my machine the brightness keys work during this login window. (not the GDM chooser, but a lock screen.)

> **hyperboloid said:**
> 
By the way, the suggested code in step 2 ```
sudo echo 1 > /sys/class/backlight/mbp_backlight/brightness
``` does not work for me - it gives me back "permission denied" even though I did not forget the "sudo" prefix. Very strange. Anyway, I set the brightness using the manual control F1-F2.
sorry. my fault. (I usually prefer to use a root shell instead.) I'm  going to write it correctly next time. I also edited my initial post according to the changes proposed in the forum.

> **hyperboloid said:**
> 
Good work, Mario. Can you similarly figure out a way to make it remember the KEYBOARD backlight settings after suspend/reboot?
probably not. keyboard backlight is something completely different.

ciao,
Mario

---

### Post by Nikos.Alexandris on 2008-11-11
> **_mario_ said:**
> Hi all,
[...]
3. MacBook 5 and MacBookPro 5 users: This might also work for the new 5th generation models. I don't have these machines and thus cannot test it. Please check out this driver and report whether it works at all.
[...]
thanks & ciao,
Mario

Sorry Mario, it does not work for me (MBP5) :-(

---

### Post by hyperboloid on 2008-11-11
> **hyperboloid said:**
>  
***One small problem:*** When the brightness is very low, one encounters a black screen upon resume, and at that point (before password verification) the brightness controls are disabled, so one must enter the password blindly and then use the controls to manually up the display brightness. 


More info on the above. The reported screen blanking behavior was caused by interference from testing the light sensors; see the thread: [http://ubuntuforums.org/showthread.php?p=6148340]("http://ubuntuforums.org/showthread.php?p=6148340"). I had uncommented the commented code in /usr/share/hal/fdi/information/10freedesktop/10-applesmc.fdi. Somehow that seems to have caused the screen to blank on resume after suspend, but only when the display was set to its lowest brightness setting: 1. Anyway, once I reverted that fdi file back to its original version, with the light sensor stuff commented out, the screen blanking issue went away, even on the lowest brightness setting.

In short, it seems that mario's fix works fine on my MBP 4,1. By the way, this is just for a suspend/resume. The fix has no effect on a cold boot. In the case of a boot, the previous display brightness settings are not remembered. I'm assuming this is the intended behavior.

---

### Post by druggo on 2008-11-11
I can confirm that this is **not working** on MB 5,1 let me know if you wan't to try something else that might fix it mario.

Regards

---

### Post by cllgnc89 on 2008-11-11
Thanks, Great Work!

---

### Post by Nikos.Alexandris on 2008-11-18
I don't know who, what and how fixed the suspend issue. I got now the nvidia driver 177.80 and suspend does not take so long any more, keyboard backlight is adjusted when (un-)plugging the AC power supply cable, dual head works (twinview and xinerama, with rotation as well). Unfortunately brightness regulation does not work.

Cheers, Nikos

---

### Post by linuxbest on 2008-11-21
after half day reserved with apple driver for windows xp, I geting the brightness control works in linux with Macbook5,1. Hope the driver will good works in all intel base mac book.

I put the source code here:
[http://bj.soulinfo.com/~hugang/mac5_1/bl/](http://bj.soulinfo.com/~hugang/mac5_1/bl/)

Issue:
 echo 1 > /sys/class/backlight/mbp_backlight/brightness 
 I using NVIDIA xorg driver, I must switch back to text mode, doing echo, in x11 echo change nothing.

---

### Post by linuxbest on 2008-11-21
after half day reserved with apple driver for windows xp, I geting the brightness control works in linux with Macbook5,1. Hope the driver will good works in all intel base mac book.

I put the source code here:
[http://bj.soulinfo.com/~hugang/mac5_1/bl/](http://bj.soulinfo.com/~hugang/mac5_1/bl/)

Issue:
 echo 1 > /sys/class/backlight/mbp_backlight/brightness 
 I using NVIDIA xorg driver, I must switch back to text mode, doing echo, in x11 echo change nothing.

---

### Post by ercoppa on 2008-11-21
First of all, thanks for the hard work!

In this moment, the download of files by your server is not permitted (403 Forbidden).

---

### Post by linuxbest on 2008-11-21
sorry, after chmod a+r, it can download.

---

### Post by linuxbest on 2008-11-21
Ok, I package with ubuntu dkms, dpkg -i /tmp/mbp*.deb

this driver will support all intel base macbook.

---

### Post by ercoppa on 2008-11-21
Yeah! Work for me on MacBook 5,1. Thanks a lot linuxbest!! \\:D/

Issues:
- power manager applet of gnome doesn't work
- change with echo works only in tty

---

### Post by Nikos.Alexandris on 2008-11-21
> **linuxbest said:**
> after half day reserved with apple driver for windows xp, I geting the brightness control works in linux with Macbook5,1. Hope the driver will good works in all intel base mac book.

I put the source code here:
[http://bj.soulinfo.com/~hugang/mac5_1/bl/](http://bj.soulinfo.com/~hugang/mac5_1/bl/)

Issue:
 echo 1 > /sys/class/backlight/mbp_backlight/brightness 
 I using NVIDIA xorg driver, I must switch back to text mode, doing echo, in x11 echo change nothing.

Let us test it... :-)

---

### Post by _mario_ on 2008-11-21
> **linuxbest said:**
> after half day reserved with apple driver for windows xp, I geting the brightness control works in linux with Macbook5,1. Hope the driver will good works in all intel base mac book.

I put the source code here:
[http://bj.soulinfo.com/~hugang/mac5_1/bl/](http://bj.soulinfo.com/~hugang/mac5_1/bl/)
great work. thanks. that's good news.

in the meantime i tried to prepare a patch for upstream inclusion for which i cleaned up the init code as well as changed handling of brightness after hibernation, so i'd like to release the next version.

btw: to name you appropriately, would you tell me your name? (or send me a private message?)

ciao,
Mario

EDIT: removed attachments. use the mactel PPA instead.

---

### Post by Nikos.Alexandris on 2008-11-21
> **_mario_ said:**
> great work. thanks. that's good news.

in the meantime i tried to prepare a patch for upstream inclusion for which i cleaned up the init code as well as changed handling of brightness after hibernation, so i'd like to release the next version.

btw: to name you appropriately, would you tell me your name? (or send me a private message?)

ciao,
Mario

Sorry folks, does not work for me :-( After suspend I get a super-bright LCD.

---

### Post by linuxbest on 2008-11-21
My name is hu gang.

My macbook5,1 is ok after suspend, do you installed vbetools, we need it doing vga bio init after resume, without it noting works.

---

### Post by Nikos.Alexandris on 2008-11-21
> **linuxbest said:**
> after half day reserved with apple driver for windows xp, I geting the brightness control works in linux with Macbook5,1. Hope the driver will good works in all intel base mac book.

I put the source code here:
[http://bj.soulinfo.com/~hugang/mac5_1/bl/](http://bj.soulinfo.com/~hugang/mac5_1/bl/)

Issue:
 echo 1 > /sys/class/backlight/mbp_backlight/brightness 
 I using NVIDIA xorg driver, I must switch back to text mode, doing echo, in x11 echo change nothing.

MBP5,1

The brightness directory does not even exist!?

```
$ echo 1 > /sys/class/backlight/mbp_backlight/brightness
bash: /sys/class/backlight/mbp_backlight/brightness: No such file or directory
```

Furthermore, after the latest usbhid-dkms update the system does not shutdown properly anymore!?

---

### Post by linuxbest on 2008-11-21
which package are you installed?

can you output the lsmod here.

---

### Post by linuxbest on 2008-11-21
or try this, 

sudo rmmod mbp_nvidia_bl 
sudo modprobe mbp_nvidia_bl

cat /sys/class/backlight/mbp_backlight/brightness

---

### Post by Nikos.Alexandris on 2008-11-21
> **linuxbest said:**
> or try this, 

sudo rmmod mbp_nvidia_bl 
sudo modprobe mbp_nvidia_bl

cat /sys/class/backlight/mbp_backlight/brightness

Great :-)

That worked!!

After **sudo modprobe mbp_nvidia_bl** it got automatically to full-brightness and **cat /sys/class/backlight/mbp_backlight/brightness** gave 15.

Now the good thing is that it works also in X11 with super-user rights:

```
sudo su

echo 1 > /sys/class/backlight/mbp_backlight/brightness

```

and that is it :-)

Thank you Hu Gang, Nikos

---

### Post by Nikos.Alexandris on 2008-11-21
> **Nikos.Alexandris said:**
> Great :-)

That worked!!

After **sudo modprobe mbp_nvidia_bl** it got automatically to full-brightness and **cat /sys/class/backlight/mbp_backlight/brightness** gave 15.

Now the good thing is that it works also in X11 with super-user rights:

```
sudo su

echo 1 > /sys/class/backlight/mbp_backlight/brightness

```

and that is it :-)

Thank you Hu Gang, Nikos

Some time back I managed to fix the broken "brithness up/down" function using "Fn+up/down arrow key(s)" on a Samsung R20 following this guide: [http://www.ubuntugeek.com/fix-your-laptops-brightness-function-keys-operating-properly-in-hardy.html](http://www.ubuntugeek.com/fix-your-laptops-brightness-function-keys-operating-properly-in-hardy.html)

Is it the same remaining issue for the MB(P)s or has this nothing to do?

---

### Post by _mario_ on 2008-11-21
> **Nikos.Alexandris said:**
> MBP5,1

The brightness directory does not even exist!?

```
$ echo 1 > /sys/class/backlight/mbp_backlight/brightness
bash: /sys/class/backlight/mbp_backlight/brightness: No such file or directory
```

the suspend code is almost the same in both versions. however, that would mean that the driver isn't loaded anymore. to iron out such bugs, can you please load the module, then suspend/hibernate and check whether it is still loaded:
```
lsmod | grep mbp_nvidia_bl
```
... and of course working.

thanks & ciao,
Mario

---

### Post by Nikos.Alexandris on 2008-11-21
> **_mario_ said:**
> the suspend code is almost the same in both versions. however, that would mean that the driver isn't loaded anymore. to iron out such bugs, can you please load the module, then suspend/hibernate and check whether it is still loaded:
```
lsmod | grep mbp_nvidia_bl
```
... and of course working.

thanks & ciao,
Mario

1. Booting-up
```
lsmod | grep mbp
```

gives nothing!

2. Loading the module gives brightness value 15
```
sudo modprobe mbp_nvidia_bl
# display becomes BRIGHT
cat /sys/class/backlight/mbp_backlight/brightness 
15
```

3. change brightness as su
```
echo 1 > /sys/class/backlight/mbp_backlight/brightness 
bash: /sys/class/backlight/mbp_backlight/brightness: Permission denied
# the same with sudo echo 1 > /sys/class/backlight/mbp_backlight/brightness
sudo su
echo 1 > /sys/class/backlight/mbp_backlight/brightness
# works with all values between 1 and 15 :-)

```

4. After restarting X11 (Ctrl + Alt + Backspace)
```
cat /sys/class/backlight/mbp_backlight/brightness 
8
```

5. Going to a tty and back does not change the brightness level

6. After suspend unfortunately is dark. I barely could see something... Restarting X (Ctrl + Alt + Backspace) and blind-logging does the trick and resumes to 8 again.

---

### Post by Nikos.Alexandris on 2008-11-21
> **Nikos.Alexandris said:**
> Some time back I managed to fix the broken "brithness up/down" function using "Fn+up/down arrow key(s)" on a Samsung R20 following this guide: [http://www.ubuntugeek.com/fix-your-laptops-brightness-function-keys-operating-properly-in-hardy.html](http://www.ubuntugeek.com/fix-your-laptops-brightness-function-keys-operating-properly-in-hardy.html)

Is it the same remaining issue for the MB(P)s or has this nothing to do?

I tried to use the following two scripts created as root under **/etc/acpi** but it does not work. Maybe I am just trying nonsense(?).

1. video_brightnessup.sh

```

#!/bin/bash

CURRENT=`cat /sys/class/backlight/mbp_backlight/actual_brightness`


case "$CURRENT" in

15)
echo -n 15 > /sys/class/backlight/mbp_backlight/brightness;
;;
14)
echo -n 14 > /sys/class/backlight/mbp_backlight/brightness;
;;
13)
echo -n 13 > /sys/class/backlight/mbp_backlight/brightness;
;;
12)
echo -n 12 > /sys/class/backlight/mbp_backlight/brightness;
;;
11)
echo -n 11 > /sys/class/backlight/mbp_backlight/brightness;
;;
10)
echo -n 10 > /sys/class/backlight/mbp_backlight/brightness;
;;
9)
echo -n 9 > /sys/class/backlight/mbp_backlight/brightness;
;;
8)
echo -n 8 > /sys/class/backlight/mbp_backlight/brightness;
;;
7)
echo -n 7 > /sys/class/backlight/mbp_backlight/brightness;
;;
6)
echo -n 6 > /sys/class/backlight/mbp_backlight/brightness;
;;
5)
echo -n 5 > /sys/class/backlight/mbp_backlight/brightness;
;;
4)
echo -n 4 > /sys/class/backlight/mbp_backlight/brightness;
;;
3)
echo -n 3 > /sys/class/backlight/mbp_backlight/brightness;
;;
3)
echo -n 2 > /sys/class/backlight/mbp_backlight/brightness;
;;
1)
echo -n 1 > /sys/class/backlight/mbp_backlight/brightness;
;;
*)
echo -n 15 > /sys/class/backlight/mbp_backlight/brightness ;
;;
esac
```

2.
```
#!/bin/bash

CURRENT=`cat /sys/class/backlight/mbp_backlight/actual_brightness`


case "$CURRENT" in

1)
echo -n 1 > /sys/class/backlight/mbp_backlight/brightness;
;;
2)
echo -n 2 > /sys/class/backlight/mbp_backlight/brightness;
;;
3)
echo -n 3 > /sys/class/backlight/mbp_backlight/brightness;
;;
4)
echo -n 4 > /sys/class/backlight/mbp_backlight/brightness;
;;
5)
echo -n 5 > /sys/class/backlight/mbp_backlight/brightness;
;;
6)
echo -n 6 > /sys/class/backlight/mbp_backlight/brightness;
;;
7)
echo -n 7 > /sys/class/backlight/mbp_backlight/brightness;
;;
8)
echo -n 8 > /sys/class/backlight/mbp_backlight/brightness;
;;
9)
echo -n 9 > /sys/class/backlight/mbp_backlight/brightness;
;;
10)
echo -n 10 > /sys/class/backlight/mbp_backlight/brightness;
;;
11)
echo -n 11 > /sys/class/backlight/mbp_backlight/brightness;
;;
12)
echo -n 12 > /sys/class/backlight/mbp_backlight/brightness;
;;
13)
echo -n 13 > /sys/class/backlight/mbp_backlight/brightness;
;;
14)
echo -n 14 > /sys/class/backlight/mbp_backlight/brightness;
;;
15)
echo -n 15 > /sys/class/backlight/mbp_backlight/brightness;
;;
*)
echo -n 7 > /sys/class/backlight/mbp_backlight/brightness ;
;;
esac
```

---

### Post by Nikos.Alexandris on 2008-11-21
+extra: the LCD dims down if there is no activity for some time and dims up again when keyboard is used! That's really nice :-p

(EDIT) ++extra: the "Use ambient light to adjust LCD brightness" (System > Preferences > Power Management) starts doing something when checking/unchecking. Maybe it works?? Is there something more to test?

---

### Post by JairunCaloth on 2008-11-22
The update works perfectly for me. I installed, adjusted backlight, and suspended. When I came back from suspend, it was right where I set it.

---

### Post by ercoppa on 2008-11-22
> Now the good thing is that it works also in X11 with super-user rights
For me in X11 as root doesn't work the echo, only in tty.

---

### Post by _mario_ on 2008-11-22
thanks for the detailed description. i'll comment it.

> **Nikos.Alexandris said:**
> 1. Booting-up 'lsmod | grep mbp' gives nothing!
the modules isn't loaded automatically right now. i still have to figure out why. however if you add a line mbp_nvidia_bl to /etc/modules, it should. did you try that already?

> **Nikos.Alexandris said:**
> 2. Loading the module gives brightness value 15
```
sudo modprobe mbp_nvidia_bl
# display becomes BRIGHT
cat /sys/class/backlight/mbp_backlight/brightness 
15
```
the driver reads the current value while loading. maximum brightness seems to be the firmware boot default (at least on my machine). or did the brightness change when you loaded the module (as the comment suggests)? that's an interesting difference.

> **Nikos.Alexandris said:**
> 
3. change brightness as su
```
echo 1 > /sys/class/backlight/mbp_backlight/brightness 
bash: /sys/class/backlight/mbp_backlight/brightness: Permission denied
# the same with sudo echo 1 > /sys/class/backlight/mbp_backlight/brightness
sudo su
echo 1 > /sys/class/backlight/mbp_backlight/brightness
# works with all values between 1 and 15 :-)

```
the first commands will never work. you don't have enough permissions on that files as a normal user. i posted wrong commands in my initial post. sorry for that. you'll always need sudo, either sudo su or:
```
echo 1 | sudo tee /sys/class/backlight/mbp_backlight/brightness
```

> **Nikos.Alexandris said:**
> 
4. After restarting X11 (Ctrl + Alt + Backspace)
```
cat /sys/class/backlight/mbp_backlight/brightness 
8
```
5. Going to a tty and back does not change the brightness level

thats good.

> **Nikos.Alexandris said:**
> 
6. After suspend unfortunately is dark. I barely could see something... Restarting X (Ctrl + Alt + Backspace) and blind-logging does the trick and resumes to 8 again.
does it work without the mbp_nvidia_bl driver? i mean: in hardy days i had a similar problem with my machine: after resuming from suspend the display was completely black although i could see that the backlight was turned on. after logging in blindly i got my desktop back. that sounds like an graphics adapter/video state problem.

ciao,
Mario

---

### Post by _mario_ on 2008-11-22
> **Nikos.Alexandris said:**
> I tried to use the following two scripts created as root under **/etc/acpi** but it does not work. Maybe I am just trying nonsense(?).
what are you trying to do (to fix)? what is the problem?

ciao,
Mario

---

### Post by _mario_ on 2008-11-22
the package has finally been included in the mactel repository. version 0.14 adds nothing dramatically new, except for a debug switch and 2nd generation MacBook Air IDs. you are still encouraged to test.
(please take instructions from my initial post.)

ciao,
Mario

---

### Post by kosumi68 on 2008-11-22
> **_mario_ said:**
> 
the package has finally been included in the mactel repository. version 0.14 adds nothing dramatically new, except for a debug switch and 2nd generation MacBook Air IDs. you are still encouraged to test.
(please take instructions from my initial post.)

*applause* :guitar:

Truly outstanding work, mario!

---

### Post by Nikos.Alexandris on 2008-11-22
> **_mario_ said:**
> thanks for the detailed description. i'll comment it.

the modules isn't loaded automatically right now. i still have to figure out why. however if you add a line mbp_nvidia_bl to /etc/modules, it should. did you try that already?

Yes, I did exactly that (read about what happens below).


> the driver reads the current value while loading. maximum brightness seems to be the firmware boot default (at least on my machine). or did the brightness change when you loaded the module (as the comment suggests)? that's an interesting difference.

While booting I think I get the "last OSX brightness level value". Suddenly the brightness becomes super-bright (I suppose it's when the mbp_nvidia_bl module gets into the game) and after some seconds the brightness value get's to (I think) the last /sys/class/backlight/.../brightness value.




> the first commands will never work. you don't have enough permissions on that files as a normal user. i posted wrong commands in my initial post. sorry for that. you'll always need sudo, either sudo su or:
```
echo 1 | sudo tee /sys/class/backlight/mbp_backlight/brightness
```

O.K., I did not try the "tee". I will.


> 
does it work without the mbp_nvidia_bl driver? i mean: in hardy days i had a similar problem with my machine: after resuming from suspend the display was completely black although i could see that the backlight was turned on. after logging in blindly i got my desktop back. that sounds like an graphics adapter/video state problem.

I'll have to check that when I'll find some free time again. No I have to re-install Intrepid 64-bit due to the mess cause by the Alsa 0.18 script :-(

> ciao,
Mario

Regards and thank you for your work Mario, Nikos

---

### Post by Nikos.Alexandris on 2008-11-22
> **_mario_ said:**
> what are you trying to do (to fix)? what is the problem?

ciao,
Mario

The brightness keys :-)

Yes, maybe I am doing nonsense as I wrote. I just thought to give it a try since the brightness levels can be changed now it should be a matter of some auto-script to get the Function Keys (for the MB(p)5,1 = the F1 & F2 keys) working. Or not?

---

### Post by oalonso on 2008-11-23
Backlight does not seem to work with the latest Nvidia drivers (177.82) and my MacBook "5,1".  :(

---

### Post by druggo on 2008-11-23
0.14 confirmed **working** on MB 5,1 using nvidia 177.80 driver. Great work!

Any chance of having this working without having to go to text-mode (using CTRL+ALT+F1) changing, and going back to X, and also, any chance of having this interacting with the ambient light sensor??

Keep up the good work!

Druggo

---

### Post by joka. on 2008-11-23
> **druggo said:**
> 0.14 confirmed **working** on MB 5,1 using nvidia 177.80 driver. Great work!

Any chance of having this working without having to go to text-mode (using CTRL+ALT+F1) changing, and going back to X, and also, any chance of having this interacting with the ambient light sensor??

Keep up the good work!

Druggo

Hey, Druggo,
Just curious, I'm a Linux newb so sorry for the ignorant question. I'm planning on getting a macbook pro soon and installing Linux on it. I have a couple of questions:
1. What do you guys mean by the nvidia 177.80 driver?
2. When you say going back to X do you mean OS X? Shouldn't all the things in OS X be working... just not for Linux... I thought you guys were fixing stuff in the Linux OS?? :confused:

---

### Post by Nikos.Alexandris on 2008-11-23
> **joka. said:**
> Hey, Druggo,
Just curious, I'm a Linux newb so sorry for the ignorant question. I'm planning on getting a macbook pro soon and installing Linux on it. I have a couple of questions:
1. What do you guys mean by the nvidia 177.80 driver?
2. When you say going back to X do you mean OS X? Shouldn't all the things in OS X be working... just not for Linux... I thought you guys were fixing stuff in the Linux OS?? :confused:

Hi joka!

1. The nvidia driver (version 177.80) is in the repositories and will get installed automatically (sort of -- you have to activate the restricted nvidia driver when asked for it from ubuntu :-)). 

*There is also a newer driver provided by nvidia (177.82) but I did not try it yet to see whether there are further improvements. Maybe the changelog is useful to read.

2. "...going back to X"  means going back to the graphical interface of linux (the X server -- in our case Xorg). You might wonder going back from where? If you jump in a terminal (tty) and just see black screen with nice white letters this is... well, a terminal which you can use to interact with the linux-kernel and successively with your computer.

Anyhow, in these last posts the discussion is about whether the LCD brightness regulation can be achieved from within X (the GUI) or if it only works from a tty (terminal not from within the X) and then go back to X and see the effects.

(Please correct me in case I don't describe things the way they are)

EDIT: You can "jump" in a tty by pressing Ctrl+Alt+F1 (or F2 or F3 or F4 or F5 or F6). There are 7 tty's befault under Ubuntu. The 7th is used by/from/for the X usually. Note, to use the F? keys under MB(P) you might need to press the Fn key (bottom left corner of the keyboard) -- depending on whether you have installed MacTel support packages or not. Refer to the wiki[1] for more... :-)

.

Just some update from my side: I confirm that the suspend vs. LCS brightness level has been solved with the latest mbp_nvidia_bl module.

Thank you all for your efforts, Nikos

[1] [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) Aluminum

---

### Post by joka. on 2008-11-23
> **Nikos.Alexandris said:**
> Hi joka!

1. The nvidia driver (version 177.80) is in the repositories and will get installed automatically (sort of -- you have to activate the restricted nvidia driver when asked for it from ubuntu :-)). 

*There is also a newer driver provided by nvidia (177.82) but I did not try it yet to see whether there are further improvements. Maybe the changelog is useful to read.

2. "...going back to X"  means going back to the graphical interface of linux (the X server -- in our case Xorg). You might wonder going back from where? If you jump in a terminal (tty) and just see black screen with nice white letters this is... well, a terminal which you can use to interact with the linux-kernel and successively with your computer.

Anyhow, in these last posts the discussion is about whether the LCD brightness regulation can be achieved from within X (the GUI) or if it only works from a tty (terminal not from within the X) and then go back to X and see the effects.

(Please correct me in case I don't describe things the way they are)

EDIT: You can "jump" in a tty by pressing Ctrl+Alt+F1 (or F2 or F3 or F4 or F5 or F6). There are 7 tty's befault under Ubuntu. The 7th is used by/from/for the X usually. Note, to use the F? keys under MB(P) you might need to press the Fn key (bottom left corner of the keyboard) -- depending on whether you have installed MacTel support packages or not. Refer to the wiki[1] for more... :-)

Thank you very much, Nikos.Alexandris! Your description is very helpful. One question tho, does it matter which tty you put in scripts [since there are 7]? Also, can you recommend a Linux/Ubuntu book/website to help me get started? i.e. with basic commands etc etc. Thanks!

---

### Post by _mario_ on 2008-11-23
> **Nikos.Alexandris said:**
> 
Yes, I did exactly that (read about what happens below).

While booting I think I get the "last OSX brightness level value". Suddenly the brightness becomes super-bright (I suppose it's when the mbp_nvidia_bl module gets into the game) and after some seconds the brightness value get's to (I think) the last /sys/class/backlight/.../brightness value.


that's still confusing. if you reboot the machine the module cannot restore the previous value. it simply isn't saved anywhere. (in contrast to suspend/hibernation.) hmm...

well, since i added a debug switch in 0.14, we can try something else:
[LIST=1]
[*]remove the line from /etc/modules and reboot. thus, the module shouldn't be loaded anymore during boot. do you still observe the same effect?
[*]load the module with:```
sudo modprobe mbp_nvidia_bl debug=1
```
what happens? the same?
[*]send me the output of your /var/log/kern.log. the last messages after loading the module. should start with mbp_nvidia_bl.
[/LIST]

thanks & ciao,
Mario

---

### Post by _mario_ on 2008-11-23
> **oalonso said:**
> Backlight does not seem to work with the latest Nvidia drivers (177.82) and my MacBook "5,1".

that's a pity. can you please search the file nv-kernel.o (Nvidia's pre-compiled kernel driver module). it is /usr/src/nvidia-177.80/nv-kernel.o if you installed the ubuntu package. otherwise i cannot tell.
finally run:
```
objdump -ldSC nv-kernel.o
```
(package binutils) and attach the output.

thanks & ciao,
Mario

EDIT: the package was wrong. it didn't include support for 5th generation models anymore. please try again. also note that it might not work in X.

---

### Post by Nikos.Alexandris on 2008-11-23
> **_mario_ said:**
> that's still confusing. if you reboot the machine the module cannot restore the previous value. it simply isn't saved anywhere. (in contrast to suspend/hibernation.) hmm...

well, since i added a debug switch in 0.14, we can try something else:
[LIST=1]
[*]remove the line from /etc/modules and reboot. thus, the module shouldn't be loaded anymore during boot. do you still observe the same effect?
[*]load the module with:```
sudo modprobe mbp_nvidia_bl debug=1
```
what happens? the same?
[*]send me the output of your /var/log/kern.log. the last messages after loading the module. should start with mbp_nvidia_bl.
[/LIST]

thanks & ciao,
Mario

Here you go:

1. I don't (need to) try the first one since it was the behaviour before adding the module under /etc/modules, that is: the brightness was set from OSX's last used value -- No brightness changes during booting.

*Or does it make a difference and I do need to try again?*

Manual loading of the mbp_nvidia_bl module gave a superbright LCD which then could be adjusted as usual (well, it became usual now :-)).

2. Loading the module manually
```
nik@vertical:~$ sudo modprobe mbp_nvidia_bl debug=1
FATAL: Error inserting mbp_nvidia_bl (/lib/modules/2.6.27-7-generic/updates/dkms/mbp_nvidia_bl.ko): Unknown symbol in module, or unknown parameter (see dmesg)

#the following works as usual
nik@vertical:~$ sudo modprobe mbp_nvidia_bl
```

3. Messages taken from the *kern.log*

Message during the boot-up process (when the module-name was present under /etc/modules
```
Nov 23 20:57:59 vertical kernel: [   15.331154] mbp_nvidia_bl: MacBookPro 5,1 detected
```

Message when attempting to load the module manually with the debug option
```
Nov 23 23:16:31 vertical kernel: [ 8331.753750] mbp_nvidia_bl: Unknown parameter `debug'
```

Manual load without the debug option
```
Nov 23 23:16:34 vertical kernel: [ 8334.537657] mbp_nvidia_bl: MacBookPro 5,1 detected

```

Cheers, Nikos

---

### Post by Nikos.Alexandris on 2008-11-23
> **joka. said:**
> Thank you very much, Nikos.Alexandris! Your description is very helpful. One question tho, does it matter which tty you put in scripts [since there are 7]? Also, can you recommend a Linux/Ubuntu book/website to help me get started? i.e. with basic commands etc etc. Thanks!

I have really no idea about which tty! I even think, if I am not wrong they are many for the average user and TOO many for the casual user. there is a way to deactivate some and keep only 3 for example but I am unsure if it requires kernel (re-)compilation.

That might help [https://answers.launchpad.net/ubuntu/+question/38901](https://answers.launchpad.net/ubuntu/+question/38901). About Books, I have seen several Ubuntu-based Books but I never bought one. I prefer to dig the net, search the forums, post in *active* mailing lists. The *community* is a great learning platform :-)

FWIW,

I think the best way to learn is to find something that you want to do, or better said, try to do something that you really want to do by using the terminal and not the GUI.

For example, you want to compress a folder with photos and move them in another directory. Or you want to apply this process for a bunch of folders by creating a small script or just a one-line "for loop" command.

There are plenty of examples on the net.

Regards, Nikos

---

### Post by _mario_ on 2008-11-23
> **Nikos.Alexandris said:**
> Here you go:...


that version couldn't work at all. i messed up my build scripts. sorry. please use the new version that is to be available within a few minutes.

btw: the tty to use doesn't really matter.

ciao,
Mario

---

### Post by Nikos.Alexandris on 2008-11-23
> **_mario_ said:**
> please use the new version that is to be available within a few minutes.
ciao,
Mario

Messages taken from *kern.log*

Booting without mbp_nvidia_bl module loaded (present under /etc/modules) and loading it manually
```
sudo modprobe mbp_nvidia_bl debug=1
Nov 24 02:15:16 vertical kernel: [   87.852919] mbp_nvidia_bl: MacBookPro 5,1 detected
Nov 24 02:15:16 vertical kernel: [   87.853376] mbp_nvidia_bl: read brightness of 15
Nov 24 02:15:16 vertical kernel: [   87.853460] mbp_nvidia_bl: setting brightness to 15
```

Adjusting manually the brightness level
```
sudo su
echo 8 > /sys/class/backlight/mbp_backlight/brightness
Nov 24 02:15:38 vertical kernel: [  109.240574] mbp_nvidia_bl: setting brightness to 8
```

Hope that helps, Nikos

---

### Post by Nikos.Alexandris on 2008-11-23
> **Nikos.Alexandris said:**
> 
Just some update from my side: I confirm that the suspend vs. LCS brightness level has been solved with the latest mbp_nvidia_bl module.


Update2: I have reasons to believe that there is still some suspend-related bug.

* After suspend the laptop's LCD is just dark but I can just see something... the after-suspend log-in dialog. I blind-log-in and it still remains dark.

* Furthermore, the mouse pointer does not react to *clicks*. It just moves.

* With an external LCD attached the same issue but only for the laptop's LCD. The external is viewable like before the suspend.

* The keyboard works

* Even after going to a tty and back the laptop's LCD is still dark.

* Ctrl+Alt+Backspace solves it.

Regards, Nikos

---

### Post by kosumi68 on 2008-11-24
> **Nikos.Alexandris said:**
> 
* After suspend the laptop's LCD is just dark but I can just see something... the after-suspend log-in dialog. I blind-log-in and it still remains dark.


The dark screen could be related to the ambient auto-adjust. To disable (to deal with it later), do
```

gconftool-2 --type bool --set /apps/gnome-power-manager/ambient/enable false

```

The ambient stuff is in this thread: [http://ubuntuforums.org/showthread.php?t=951477](http://ubuntuforums.org/showthread.php?t=951477)

---

### Post by kosumi68 on 2008-11-24
> **druggo said:**
> 0.14 confirmed **working** on MB 5,1 using nvidia 177.80 driver. Great work!

Any chance of having this working without having to go to text-mode (using CTRL+ALT+F1) changing, and going back to X, and also, any chance of having this interacting with the ambient light sensor??

Keep up the good work!

Druggo

Are you running pommed? It would explain why you are able to control the backlight at all, since the method used by default in gnome-power-manager (XRandR) is the reason why the mbp_nvidia_bl kernel module is needed.

I have attached a package which installs a HAL dbus interface, which is the other interface (apart from XRandR) that gnome-power-manager knows how to use. Pressing the brightness keys should send messages to the lcd-backlight addon of this package, which in turn sends them to the sysfs interface that mario has been updating. Hopefully it works :-)

The attached package is 32-bit and for testing only; once confirmed working, I will put it in the mactel PPA.

---

### Post by linuxbest on 2008-11-24
> **kosumi68 said:**
> Are you running pommed? It would explain why you are able to control the backlight at all, since the method used by default in gnome-power-manager (XRandR) is the reason why the mbp_nvidia_bl kernel module is needed.


beacause we do not have the method to doing backlight control with xrandr tools.

xrandr control the backlight using the xorg video driver, but the Macbook5,1 seem not using the normal nvidia backlight control.
so we reversed the MacHalDriver.sys from XP, And we know how to changed the backlight.

current, we still can not change the brightness in X11 mode with nvidia driver, I reading the reverse code to making it works.

---

### Post by druggo on 2008-11-24
> **kosumi68 said:**
> Are you running pommed? 
Nope.
> **kosumi68 said:**
> 
The attached package is 32-bit and for testing only; once confirmed working, I will put it in the mactel PPA.
Sorry i cannot test, i'm on x64, post one of those and i'll test it in a jiffy!

[QUOTE=linuxbest]
current, we still can not change the brightness in X11 mode with nvidia driver, I reading the reverse code to making it works.
[/QUOTE]
Keep up the good work!

Druggo

---

### Post by _mario_ on 2008-11-24
> **Nikos.Alexandris said:**
> Messages taken from *kern.log*
Booting without mbp_nvidia_bl module loaded (present under /etc/modules) and loading it manually
```
sudo modprobe mbp_nvidia_bl debug=1
Nov 24 02:15:16 vertical kernel: [   87.852919] mbp_nvidia_bl: MacBookPro 5,1 detected
Nov 24 02:15:16 vertical kernel: [   87.853376] mbp_nvidia_bl: read brightness of 15
Nov 24 02:15:16 vertical kernel: [   87.853460] mbp_nvidia_bl: setting brightness to 15
```

that explains everything. you observed:
[LIST=1]
[*]brightness is low during boot, because the firmware doesn't change when switching from OSX to ubuntu. (on my machine brightness gets set to maximum.)
[*]while the driver loads: the value is read (15), which erroneously indicates maximum.
[*]thereafter the brightness is set to this value. that's why the display is suddenly bright.
[/LIST]
well, but unfortunately there's no simple solution. if we wouldn't set brightness (step 3), and you later decide to adjust incrementally using the functions keys (when they will work), your brightness will immediately jump to 14, i.e., hal's read value of 15 minus 1. that's not better either. so we'll have to wait until Apple eventually fixes its firmware.

ciao,
Mario

---

### Post by _mario_ on 2008-11-24
> **kosumi68 said:**
> 
I have attached a package which ... Hopefully it works :-)


great. :-) that's been the final piece.

thanks & ciao,
Mario

---

### Post by ercoppa on 2008-11-24
> I have attached a package which installs a HAL dbus interface, which is the other interface (apart from XRandR) that gnome-power-manager knows how to use. Pressing the brightness keys should send messages to the lcd-backlight addon of this package, which in turn sends them to the sysfs interface that mario has been updating. Hopefully it works

The attached package is 32-bit and for testing only; once confirmed working, I will put it in the mactel PPA.

It works but not changes brightness because I am in X (as for echo). In order to explain:
```
ercoppa@ercoppa-laptop:~$ cat /sys/class/backlight/mbp_backlight/actual_brightness 
1
```
- I press F2 (in gnome) and the value increases:
```
ercoppa@ercoppa-laptop:~$ cat /sys/class/backlight/mbp_backlight/actual_brightness 
2
```
- I press F1 and the value decreases:
```
ercoppa@ercoppa-laptop:~$ cat /sys/class/backlight/mbp_backlight/actual_brightness 
1
```
But brightness in real not changes.

I have the last version in mactel PPA of mbp_nvidia_bl and nvidia driver 180.08 (beta version).

---

### Post by kosumi68 on 2008-11-24
> **druggo said:**
> 
Sorry i cannot test, i'm on x64, post one of those and i'll test it in a jiffy!


I got partial confirmation regarding the package, so uploaded to the PPA. Should be available within thirty minutes.

---

### Post by kosumi68 on 2008-11-24
> **ercoppa said:**
> It works but not changes brightness because I am in X (as for echo). In order to explain:
```
ercoppa@ercoppa-laptop:~$ cat /sys/class/backlight/mbp_backlight/actual_brightness 
1
```
- I press F2 (in gnome) and the value increases:
```
ercoppa@ercoppa-laptop:~$ cat /sys/class/backlight/mbp_backlight/actual_brightness 
2
```
- I press F1 and the value decreases:
```
ercoppa@ercoppa-laptop:~$ cat /sys/class/backlight/mbp_backlight/actual_brightness 
1
```
But brightness in real not changes.

I have the last version in mactel PPA of mbp_nvidia_bl and nvidia driver 180.08 (beta version).

Did you get the brightness to change using the manual "echo" command?

---

### Post by ercoppa on 2008-11-24
> Did you get the brightness to change using the manual "echo" command? 
In tty yes, in X11 no.

---

### Post by _mario_ on 2008-11-24
> **ercoppa said:**
> In tty yes, in X11 no.

yep. unfortunately, that's a known problem. unfortunately, because there's no known solution yet. in the meantime you can play with the following tiny progam, that does essentially the same the driver would do. like this:
```
apple-backlight32 --reg1 1
```
to change to lowest level.

--reg1 is known to work on 3rd and 4th generation MacBook Pro while --reg2 works on 5th generation MacBook Pro. the latter code is used on the MacBook 5 as well, but doesn't work in X. this is state of the art, if you'd like to get involved.

i'd especially like to know whether --reg1 works on a tty (MacBook 5).

ciao,
Mario

EDIT: removed attachments. deprecated now.

---

### Post by ercoppa on 2008-11-24
> i'd especially like to know whether --reg1 works on a tty (MacBook 5).
No, --reg1 not works for me (not in tty and not in X11).
```
ercoppa@ercoppa-laptop:~/Desktop$ cat /sys/class/backlight/mbp_backlight/actual_brightness 
1
ercoppa@ercoppa-laptop:~/Desktop$ sudo ./apple-backlight32 --reg1 2
setting brightness to: 2
current brightness is now: 15
ercoppa@ercoppa-laptop:~/Desktop$ cat /sys/class/backlight/mbp_backlight/actual_brightness 
1

```

Instead --reg2 works (as you say) in tty (not in X11).

---

### Post by kosumi68 on 2008-11-24
A theory: how about disabling gnome-power-manager temporarily (kill process will do), then trying to adjust the brigthness through the "echo" method, while in X?

PS. Also, since it is untested, could someone please provide the output of
```

hal-find-by-capability --capability laptop_panel

```

---

### Post by kosumi68 on 2008-11-24
> **linuxbest said:**
> beacause we do not have the method to doing backlight control with xrandr tools.

xrandr control the backlight using the xorg video driver, but the Macbook5,1 seem not using the normal nvidia backlight control.
so we reversed the MacHalDriver.sys from XP, And we know how to changed the backlight.

current, we still can not change the brightness in X11 mode with nvidia driver, I reading the reverse code to making it works.

Thanks for the detective work :-)

---

### Post by undoIT on 2008-11-24
Subscribing. I still haven't figured out how to set the brightness for the MacBook 5,1.

---

### Post by _mario_ on 2008-11-25
> **undoIT said:**
> Subscribing. I still haven't figured out how to set the brightness for the MacBook 5,1.
[LIST=1]
[*]enable the mactel repository.
[*]install the packages: mbp-nvidia-bl-dkms and hal-nvidia-bl.
[/LIST]
known bug: changing the backlight in X doesn't work as expected (the value is sent to hardware, but backlight doesn't change). you'll have to switch to a text console first. there issue:
```
echo 1 | sudo tee /sys/class/backlight/mbp_backlight/brightness
```

ciao,
Mario

---

### Post by _mario_ on 2008-11-25
> **Nikos.Alexandris said:**
> Update2: I have reasons to believe that there is still some suspend-related bug.

* After suspend the laptop's LCD is just dark but I can just see something... the after-suspend log-in dialog. I blind-log-in and it still remains dark.

* Furthermore, the mouse pointer does not react to *clicks*. It just moves.

* With an external LCD attached the same issue but only for the laptop's LCD. The external is viewable like before the suspend.

* The keyboard works

* Even after going to a tty and back the laptop's LCD is still dark.

* Ctrl+Alt+Backspace solves it.

Regards, Nikos
last night a got an idea. we should also check the following:
[LIST=1]
[*]load the module with debug=1, after the system is up: ```
sudo rmmod mbp_nvidia_bl
sudo modprobe mbp_nvidia_bl debug=1
```
[*]put a marker in you kern.log:```
echo "----- cut here -----" | sudo tee /var/run/klogd/kmsg
```
[*]now trigger suspend and resume.
[/LIST]
the module should output debug messages indicating what it does while resuming, so please attach the output of /var/log/kern.log after the marker (or only those lines containing 'mbp_nvidia_bl').

thanks & ciao,
Mario

EDIT: fixed commands to work with root privileges.

---

### Post by majormar on 2008-11-25
Is there a x86_64 version coming soon? I don't see it in the repos yet. :popcorn:

---

### Post by ercoppa on 2008-11-25
> A theory: how about disabling gnome-power-manager temporarily (kill process will do), then trying to adjust the brigthness through the "echo" method, while in X
Not works for me.
> 
PS. Also, since it is untested, could someone please provide the output of
```
ercoppa@ercoppa-laptop:~$ hal-find-by-capability --capability laptop_panel
/org/freedesktop/Hal/devices/computer_backlight
```

---

### Post by kosumi68 on 2008-11-25
> **ercoppa said:**
> 
```
ercoppa@ercoppa-laptop:~$ hal-find-by-capability --capability laptop_panel
/org/freedesktop/Hal/devices/computer_backlight
```


I see... here is another test:

0. Make sure the hal addon is loading:

```

sed 's/mbp_nvidia_bl/applesmc/' /usr/share/hal/fdi/policy/10osvendor/10-nvidia-bl.fdi | sudo tee /etc/hal/fdi/policy/nvidia-testing.fdi

```

1. Remove the backlight module

```

sudo rmmod mbp_nvidia_bl

```

2. Restart HAL

```

sudo /etc/init.d/hal restart

```

3. Check for hal devices
```

hal-find-by-capability --capability laptop_panel

```

4. Start the backlight module
```

sudo modprobe mbp_nvidia_bl

```

5. Restart X (log out, log in)

If everything is correct, there should be a /org/freedesktop/Hal/devices/nvidia_laptop_panel hal device present (and the brightness might work).

6. Remove the test file

```

sudo rm /etc/hal/fdi/policy/nvidia-testing.fdi

```

7. Restart HAL and restart X to get back to normal.

---

### Post by _mario_ on 2008-11-25
> **kosumi68 said:**
> A theory: how about disabling gnome-power-manager temporarily (kill process will do), then trying to adjust the brigthness through the "echo" method, while in X?
does g-p-m adjust brightness itself? or does it call the (same) hal interface?

> **kosumi68 said:**
> I see... here is another test:
i installed the hal-nvidia-bl package, although i don't need it. but it works:
```
udi = '/org/freedesktop/Hal/devices/computer_backlight'
  info.capabilities = {'laptop_panel'} (string list)
  info.category = 'laptop_panel'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.LaptopPanel'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Generic Backlight Device'  (string)
  info.subsystem = 'backlight'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_backlight'  (string)
  laptop_panel.access_method = 'general'  (string)
  laptop_panel.num_levels = 16  (0x10)  (int)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'backlight'  (string)
  linux.sysfs_path = '/sys/devices/virtual/backlight/mbp_backlight'  (string)
  org.freedesktop.Hal.Device.LaptopPanel.method_argnames = {'brightness_value', ''} (string list)
  org.freedesktop.Hal.Device.LaptopPanel.method_execpaths = {'hal-system-lcd-set-brightness', 'hal-system-lcd-get-brightness'} (string list)
  org.freedesktop.Hal.Device.LaptopPanel.method_names = {'SetBrightness', 'GetBrightness'} (string list)
  org.freedesktop.Hal.Device.LaptopPanel.method_signatures = {'i', ''} (string list)


udi = '/org/freedesktop/Hal/devices/nvidia_laptop_panel'
  info.addons = {'hald-addon-generic-lcd-backlight'} (string list)
  info.capabilities = {'laptop_panel'} (string list)
  info.interfaces = {'org.freedesktop.Hal.Device.LaptopPanel'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/platform_mbp_nvidia_bl'  (string)
  info.product = 'Nvidia Backlight Interface'  (string)
  info.subsystem = 'unknown'  (string)
  info.udi = '/org/freedesktop/Hal/devices/nvidia_laptop_panel'  (string)
  laptop_panel.access_method = 'custom'  (string)
  laptop_panel.num_levels = 16  (0x10)  (int)
  linux.sysfs_path = '/sys/class/backlight/mbp_backlight'  (string)

```
the first one is the existing approach, while the latter on was added by your package. to me, both seem to use the same sysfs interface. so it should have been working all the time (or will not work at all). or am i completely wrong?

ciao,
Mario

---

### Post by ercoppa on 2008-11-25
> If everything is correct, there should be a /org/freedesktop/Hal/devices/nvidia_laptop_panel hal device present .
```
ercoppa@ercoppa-laptop:~/Desktop/ercoppa$ hal-find-by-capability --capability laptop_panel
/org/freedesktop/Hal/devices/computer_backlight
/org/freedesktop/Hal/devices/nvidia_laptop_panel

```
> (and the brightness might work)
:( not works (with echo or pressing F1/F2 or with apple-backlight32) in X.

---

### Post by kosumi68 on 2008-11-25
> **_mario_ said:**
> does g-p-m adjust brightness itself? or does it call the (same) hal interface?


It uses either xrandr or hal. Thanks for the details of the backlight interface - I had not seen the details of it. It does seem to use the same sysfs interface, so there should be no need for the hal-nvidia-bl package. It seems the video mode itself is the most likely reason why it does not work on the 9400M.

Thanks!

---

### Post by kosumi68 on 2008-11-25
> **ercoppa said:**
> ```
ercoppa@ercoppa-laptop:~/Desktop/ercoppa$ hal-find-by-capability --capability laptop_panel
/org/freedesktop/Hal/devices/computer_backlight
/org/freedesktop/Hal/devices/nvidia_laptop_panel

```

:( not works (with echo or pressing F1/F2 or with apple-backlight32) in X.

Thanks for checking this. It seems clear now that the problem is really the video mode, not gnome.

---

### Post by Nikos.Alexandris on 2008-11-25
> **_mario_ said:**
> last night a got an idea. we should also check the following:
[LIST=1]
[*]load the module with debug=1, after the system is up.
[*]put a marker in you kern.log:```
echo "----- cut here -----" >> /var/run/klogd/kmsg
```
[*]now trigger suspend and resume.
[/LIST]
the module should output a debug message indicating what it does while resuming, so please attach the output in /var/log/kern.log after the marker.

thanks & ciao,
Mario

Mario,
should I just post the log (after cut) here? Is it safe? Or should I post it to you off-line? Sorry for the *beginners* question, but I am unaware on how important are some of the messages in this specific log.

Regards

---

### Post by cyberdork33 on 2008-11-25
> **majormar said:**
> Is there a x86_64 version coming soon? I don't see it in the repos yet. :popcorn:

dkms packages do not need a separate 64bit package as it compiles on your system.

---

### Post by undoIT on 2008-11-26
> **_mario_ said:**
> [LIST=1]
[*]enable the mactel repository.
[*]install the packages: mbp-nvidia-bl-dkms and hal-nvidia-bl.
[/LIST]
known bug: changing the backlight in X doesn't work as expected (the value is sent to hardware, but backlight doesn't change). you'll have to switch to a text console first. there issue:
```
echo 1 | sudo tee /sys/class/backlight/mbp_backlight/brightness
```

ciao,
Mario

Hi Mario. I have the regular MacBook, not MacBook pro. I have the following packages installed:

hal-applesmc
applesmc-dkms
bcm5974-dkms
mbp-nvidia-bl-dkms
hal-nvidia-bl

When I enter this command:

```
echo 1 | sudo tee /sys/class/backlight/mbp_backlight/brightness
```

I get this: No such file or directory

Do I need anything else installed? Does this not work with regular MacBook?

---

### Post by _mario_ on 2008-11-26
> **Nikos.Alexandris said:**
> Mario,
should I just post the log (after cut) here? Is it safe? Or should I post it to you off-line? Sorry for the *beginners* question, but I am unaware on how important are some of the messages in this specific log.

i do only need the lines after resuming, i.e., after the cut marker. you may safely compress the whole file (or parts of it) and attach it to your post. alternatively you may also send a private message. with respect to sensitivity, everyone else having your machine will get almost the same kernel messages. if you don't want to release you kernel messages, run:
```
grep mbp_nvidia_bl /var/log/kern.log
``` right after resuming (the module should be loaded before with the debug=1 switch). i'm only interested in the module's messages after resuming.

ciao,
Mario

---

### Post by ercoppa on 2008-11-26
> Do I need anything else installed?
Do You load the relative module (mbp_nvidia_bl)?

---

### Post by _mario_ on 2008-11-26
> **undoIT said:**
> Hi Mario. I have the regular MacBook, not MacBook Pro. I have the following packages installed:

hal-applesmc
applesmc-dkms
bcm5974-dkms
mbp-nvidia-bl-dkms
hal-nvidia-bl

Do I need anything else installed? Does this not work with regular MacBook?

hal-nvidia-bl should be unnecessary. in addition, you might like to install gnome-power-manager (mactel version), hid-dkms, and usbhid-dkms (have a look at the [mactel ppa]("https://launchpad.net/~mactel-support/+archive")).

however, i forgot to mention that, the mbp_nvidia_bl driver isn't loaded automatically (neither the upstream version nor this version), so you'll either have to add it to /etc/modules or to load it manually and restart hal thereafter. sorry for causing confusion.

ciao,
Mario

---

### Post by undoIT on 2008-11-26
Thanks Mario. I have the following packages installed:

hal-applesmc
applesmc-dkms
bcm5974-dkms
mbp-nvidia-bl-dkms
gnome-power-manager (mactel version)
hid-dkms
usbhid-dkms

After adding mbp_nvidia_bl to modules, I rebooted, opened up terminal and entered this command:

```
sudo modprobe mbp_nvidia_bl
```

Then I dropped into tty and typed in:

```
echo 1 | sudo tee /sys/class/backlight/mbp_backlight/brightness
```

It didn't give me a file not found error this time but it didn't adjust the brightness either. Am I missing anything?

---

### Post by _mario_ on 2008-11-26
> **undoIT said:**
> 
After adding mbp_nvidia_bl to modules, I rebooted, opened up terminal and entered this command:```
sudo modprobe mbp_nvidia_bl
```
you don't have to load the module as it's already loaded due to /etc/modules. however, it doesn't hurt.

> **undoIT said:**
> 
Then I dropped into tty and typed in:
```
echo 1 | sudo tee /sys/class/backlight/mbp_backlight/brightness
```
It didn't give me a file not found error this time but it didn't adjust the brightness either. Am I missing anything?
in theory no. so we'd better check twice:
[LIST=1]
[*]```
sudo grep mbp_nvidia_bl /var/log/kern.log
```
should give something like:
```
Nov 26 16:57:22 snoopy kernel: [82444.741081] mbp_nvidia_bl: MacBookPro 4,1 detected
```
[*]loading with the debug option:
```
sudo rmmod mbp_nvidia_bl
sudo modprobe mbp_nvidia_bl debug=1

```
should give something like:
```
Nov 24 00:13:26 snoopy kernel: [51384.775227] mbp_nvidia_bl: read brightness 1
Nov 24 00:13:26 snoopy kernel: [51384.775229] mbp_nvidia_bl: setting brightness to 1
```
each time you read or write to the sysfs file.
[/LIST]

if the all works, the right module is loaded and does what it's supposed to do. if the brightness still doesn't change, you've got a very interesting model ;-).

ciao,
Mario

---

### Post by undoIT on 2008-11-26
```
sudo rmmod mbp_nvidia_bl
```

usur-macbook kernel: [ 1367.664698] mbp_nvidia_bl: MacBook 5,1 detected

```
sudo rmmod mbp_nvidia_bl
```

ERROR: Module mbp_nvidia_bl does not exist in /proc/modules

Wait a minute, I think I found something...

---

Oh man do I feel stupid. I had "mbp_nividia_bl" in etc/modules (notice the extra i). After fixing that, the brightness adjustment is working and maintains level after suspend. Also explains why I had to modprobe after rebooting. No more eyeball fry. My eyeballs are grateful :)

Really sorry for wasting your time on this Mario. And many thanks for your work on this. It is amazing how well everything works already. That was the last fix needed to make Ubuntu fully usable. It will be awesome once the brightness keys are working. Let me know if I can help with testing or anything (no more bonehead misspellings).

An added note:

**with bcm5974-dkms installed you need to hit: fn control option F1 to go into tty, rather than the usual control option F1**

---

### Post by _mario_ on 2008-11-26
> **undoIT said:**
> It will be awesome once the brightness keys are working. Let me know if I can help with testing or anything (no more bonehead misspellings).
perhaps. does it work (at first, i mean the echo command to the sysfs file) in X or only on a tty? if it doesn't work in X, that's the reason why function keys cannot work, although the right handler should be called (reported by ercoppa).

additionally, please run the attached program on a tty and in X, like this:
```
apple-backlight32 --step-up
apple-backlight32 --step-down
```
what happens?

essentially, it uses the same interface (SMI) as the driver, so it's very unlikely to work better. however, according to the Windows XP driver, it allows to test all functions Apple's firmware provides.

btw: did you install Windows (either XP or Vista)? does it work there? since this tool does exactly the same as the Windows driver, there's no reason why we cannot change backlight from within X on a MacBook 5.

> **undoIT said:**
> 
**with bcm5974-dkms installed you need to hit: fn control option F1 to go into tty, rather than the usual control option F1**
that shouldn't be a matter of bcm5974. it's a trackpad driver. instead hid-dkms (updated linux kernel's HID driver) allows to select what the primary function of keys F1-F12 is. either hardware stuff (brightness, volume, eject, ...) or the usual F1-F12. the module option is called 'pb_fnmode' (0 = disabled, 1 = fkeyslast, 2 = fkeysfirst).

ciao,
Mario

---

### Post by undoIT on 2008-11-26
1. ```
echo 1 | sudo tee /sys/class/backlight/mbp_backlight/brightness
```
works in tty. doesn't work in X

2. how do i run this? i downloaded and unzipped apple-backlight64 to home directory. when i try and run "apple-backlight32 --step-up" in terminal it says: "apple-backlight64: command not found"

3. Brightness keys: F1, F2

They pull up the gnome brightness adjustment popup which indicates with the bar that brightness is being increased and decreased, but the brightness does not actually change. Encouraging sign :)

4. I only have Windows XP on my XPS M1330 running in VirtualBox. Would this require dual-boot to test on the MacBook?

---

### Post by _mario_ on 2008-11-26
> **undoIT said:**
> 1. ```
echo 1 | sudo tee /sys/class/backlight/mbp_backlight/brightness
```
works in tty. doesn't work in X
i know. that's the main problem on MacBook5 and MacBookAir2, i'm trying to solve.

> **undoIT said:**
> 
2. how do i run this? i downloaded and unzipped apple-backlight64 to home directory. when i try and run "apple-backlight32 --step-up" in terminal it says: "apple-backlight64: command not found"[/CODE]
download either apple-backlight64.gz (AMD64 version) or apple-backlight32.gz (i386 version). which one depends on your installed architecture. the i386 version should be safe if in doubt. then run:
```
chmod +x apple-backlight32
sudo ./apple-backlight32 --nvidia --step-up
sudo ./apple-backlight32 --nvidia --step-down
```
substitute 32 by 64 if you downloaded the other one. please also note that brightness doesn't exceed minimum and maximum, so the effects depend on you current setting. i'd especially like to know whether the incremental interface function works within X.

Setting the backlight to a particular value (what the driver does), i.e., running:
```
sudo ./apple-backlight32 --nvidia 1
```
is reported to not work within X. (the argument is between 0 and 15. 0 turns backlight off. 15 is maximum.) if both methods don't work, the firmware is seriously broken, or Nvidia's proprietary driver interferes.

> **undoIT said:**
> 
3. Brightness keys: F1, F2
They pull up the gnome brightness adjustment popup which indicates with the bar that brightness is being increased and decreased, but the brightness does not actually change. Encouraging sign :)
no. the handler is called and outputs via the sysfs interface, which doesn't work as you observed.

> **undoIT said:**
> 
4. I only have Windows XP on my XPS M1330 running in VirtualBox. Would this require dual-boot to test on the MacBook?
yes. indeed, triple-boot. but don't mind. it was just a guess: if we do the same the Windows driver would do, it should work as well or shouldn't work at all. but in both operating systems.

ciao,
Mario

EDIT: wrong commands have been fixed.

---

### Post by undoIT on 2008-11-26
okay, had the right permissions but wasn't running the app properly.

1. in both X and tty i get this:

> decreasing brightness
current brightness is now: 15

increasing brightness
current brightness is now: 15

value does not change.

2. sudo ./apple-backlight64 --nvidia 1

in X, changes values but does not change brightness

in tty, changes values and changes brightness. (much easier than typing the tee command)

---

### Post by _mario_ on 2008-11-26
> **undoIT said:**
> 2. sudo ./apple-backlight32 --nvidia 1
in X, changes values but does not change brightness in tty, changes values and changes brightness.
that's it. i forgot the option. my fault. sorry. both commands to test should on your machine indeed be:
```
sudo ./apple-backlight32 **--nvidia** --step-down
sudo ./apple-backlight32 **--nvidia** --step-up
```

thanks & ciao,
Mario

---

### Post by undoIT on 2008-11-26
okay, that gets some results:

in tty, brightness is increased and decreased accordingly

in X value is increased and decreased but brightness does not change.

---
on other note. now after resuming from suspend, backlight seems to be set to 0. i have to shut down and start over. then brightness is set at 15.

p.s. is there a way to copy and paste from X to tty?

---

### Post by _mario_ on 2008-11-26
> **undoIT said:**
> okay, that gets some results: in tty, brightness is increased and decreased accordingly, in X value is increased and decreased but brightness does not change.
that's a pity. looks like there's no solution. at least, i don't have any idea anymore.

> **undoIT said:**
>  on other note. now after resuming from suspend, backlight seems to be set to 0. i have to shut down and start over. then brightness is set at 15.
Nikos.Alexandris did report a similar problem. are you observing the same? if so, please follow the steps described [here]("http://ubuntuforums.org/showpost.php?p=6248127&postcount=73"). i'm still waiting for Nikos's reply.

> **undoIT said:**
>  p.s. is there a way to copy and paste from X to tty?
what about using a temporary script?

ciao,
Mario

---

### Post by undoIT on 2008-11-26
> **_mario_ said:**
> that's a pity. looks like there's no solution. at least, i don't have any idea anymore.

Darn. I wish I could help more, I'm just a web developer and don't have time to learn another programming language right now. Maybe there is another way to get this working.

btw, this time after resuming from suspend, brightness was set to 8. seems to be kind of sporadic and maybe gnome power manager has something to do with it.

---

### Post by Nikos.Alexandris on 2008-11-26
> **_mario_ said:**
> i do only need the lines after resuming, i.e., after the cut marker. you may safely compress the whole file (or parts of it) and attach it to your post. alternatively you may also send a private message. with respect to sensitivity, everyone else having your machine will get almost the same kernel messages. if you don't want to release you kernel messages, run:
```
grep mbp_nvidia_bl /var/log/kern.log
``` right after resuming (the module should be loaded before with the debug=1 switch). i'm only interested in the module's messages after resuming.

ciao,
Mario

Sorry for replying kind of late. Here you are :-)

---

### Post by Nikos.Alexandris on 2008-11-26
Well, how many of you did try to set the "Set display brightness to:" in the Power Management Preferences?

Surprise...:) Brightness level changes from 0% (black) to 100% (full-bright). I don't remember this working before. So, is it "safe" to assume that we are getting (that You dev's bring us) closer to full-functional brightness-regulation keys (in the keyboard)? Or maybe not...

Anyhow, it's another way to avoid the command line :-)

Regards

EDIT: WoW!! The Brightness level applet (Gnome) works also!! WoW!

---

### Post by _mario_ on 2008-11-27
> **Nikos.Alexandris said:**
> Sorry for replying kind of late. Here you are :-)
don't mind. however, according to the log the module works. nothing unusual. it did set the brightness to 15 after resuming. so i see no reason for having a black screen. could be some issue with properly saving and restoring video state (i.e., graphics driver), but that stuff is far beyond my knowledge.

ciao,
Mario

EDIT: hey, it's post number #100 in this thread. and it could be the final one. as a conclusion, the remaining problems seem to be beyond the scope:
[LIST=1]
[*]i don't think the suspend/resume (black screen) issues are because of this driver.
[*]changing backlight on MacBook5 (and probably MacBookAir2) doesn't work within X. there's no explanation yet. however, it looks like Nvidia's graphics driver interferes. hopefully a newer release will fix it.
[/LIST]

---

### Post by hawkwing3141 on 2008-11-29
> 
EDIT: hey, it's post number #100 in this thread. and it could be the final one. as a conclusion, the remaining problems seem to be beyond the scope:
[LIST=1]
[*]i don't think the suspend/resume (black screen) issues are because of this driver.
[*]changing backlight on MacBook5 (and probably MacBookAir2) doesn't work within X. there's no explanation yet. however, it looks like Nvidia's graphics driver interferes. hopefully a newer release will fix it.
[/LIST]

Sorry to mess up the post count, and I should say I haven't had the time to understand this whole thread, but the 'echo' command to change the brightness works fine inside X11 using Kubuntu (KDE 4.1.2) and a console (konsole) on a Macbook5,1.  I wrote the following shell scripts to make it easier:

brighten.sh
```

#!/bin/bash
BRIGHTNESS=$(cat /sys/class/backlight/mbp_backlight/actual_brightness)
let "BRIGHTNESS+=1"
echo $BRIGHTNESS | sudo tee /sys/class/backlight/mbp_backlight/brightness

```

darken.sh
```

#!/bin/bash
BRIGHTNESS=$(cat /sys/class/backlight/mbp_backlight/actual_brightness)
let "BRIGHTNESS-=1"
echo $BRIGHTNESS | sudo tee /sys/class/backlight/mbp_backlight/brightness

```

also regarding the discussion of using the Fn-key to access the F1-F12 keys when hid-dkms is installed, I think that happened for me after installing applesmc-dkms or hal-applesmc, and I haven't installed hid-dkms to my knowledge.

not sure the right way to see which modules are installed...
```

find /lib/modules/ | grep dkms
/lib/modules/2.6.27-9-generic/updates/dkms
/lib/modules/2.6.27-9-generic/updates/dkms/applesmc.ko
/lib/modules/2.6.27-9-generic/updates/dkms/bcm5974.ko
/lib/modules/2.6.27-9-generic/updates/dkms/usbhid.ko
/lib/modules/2.6.27-9-generic/updates/dkms/nvidia.ko
/lib/modules/2.6.27-9-generic/updates/dkms/mbp_nvidia_bl.ko

```

---

### Post by ercoppa on 2008-11-30
> Sorry to mess up the post count, and I should say I haven't had the time to understand this whole thread, but the 'echo' command to change the brightness works fine inside X11 using Kubuntu (KDE 4.1.2) and a console (konsole) on a Macbook5,1.
I have installed KDE 4 on my Ubuntu 8.10 & MacBook 5,1, but the echo don't works in X11 (as in gnome) :(

---

### Post by undoIT on 2008-11-30
@: hawkwing3141

Which Nvidia driver version are you running? Are you sure you have a MacBook 5,1? You can run this command to check:

```
sudo grep mbp_nvidia_bl /var/log/kern.log
```

I have installed Kubuntu for testing and like ercoppa, I get the same behaviour as in Ubuntu, that is, brightness changes in TTY but not in X. Also, in Kubuntu, the backlit keyboard doesn't light up.

---

### Post by heluani on 2008-11-30
Can confirm that it works in TTY on a macbook Air 2,1 but somehow whenever I install this package from mactel I start having issues with the wireless driver, I see two repeated drivers in nm-applet and I keep dropping my wireless connection. This issue is resolved if I remove the package mbp_nvidia_bl_dkms

Edit: strangely, a reboot solved the wireless issue...

R.

---

### Post by hawkwing3141 on 2008-11-30
> **undoIT said:**
> @: hawkwing3141

Which Nvidia driver version are you running? Are you sure you have a MacBook 5,1? You can run this command to check:

```
sudo grep mbp_nvidia_bl /var/log/kern.log
```

I have installed Kubuntu for testing and like ercoppa, I get the same behaviour as in Ubuntu, that is, brightness changes in TTY but not in X. Also, in Kubuntu, the backlit keyboard doesn't light up.

I think I'm running the nvidia 177.80 drivers unless they auto-updated, not sure how to check that.

```

Nov 30 14:49:46 tremalking kernel: [   16.581135] mbp_nvidia_bl: MacBook 5,1 detected

```

As of this week I am getting a new problem that if the AC adapter gets unplugged (not even going into suspend, just unplugged) the brightness gets set to 0, which now that I've figured out how to change it back isn't such a big problem but it sure is annoying.  Does anyone else have this problem?

I have the 2GHz, so no backlit keyboard.

If there's anything else I can do to help let me know.

---

### Post by _mario_ on 2008-12-01
> **hawkwing3141 said:**
> I think I'm running the nvidia 177.80 drivers unless they auto-updated, not sure how to check that.
```
glxinfo | grep OpenGL
```
(package mesa-utils) i'm very excited to see the result. perhaps you're running the open-source driver.

> **hawkwing3141 said:**
> 
As of this week I am getting a new problem that if the AC adapter gets unplugged (not even going into suspend, just unplugged) the brightness gets set to 0, which now that I've figured out how to change it back isn't such a big problem but it sure is annoying.  Does anyone else have this problem?

did you configure some power manager (like gnome-power-manager) to automatically adjust backlight? since you're running KDE, i can't tell how to disable this, but it would be nice to do so to figure out what the reason for this behaviour is.

additionally, you might also enable debugging messages by running:
```
echo 1 | sudo tee /sys/module/mbp_nvidia_bl/parameters/debug
```
(since version 0.16). if there are no messages in /var/log/kern.log related to mbp_nvidia_bl when you unplug power, the driver doesn't do anything.

ciao,
Mario

---

### Post by _mario_ on 2008-12-01
> **heluani said:**
> Can confirm that it works in TTY on a macbook Air 2,1 but somehow whenever I install this package from mactel I start having issues with the wireless driver, I see two repeated drivers in nm-applet and I keep dropping my wireless connection. This issue is resolved if I remove the package mbp_nvidia_bl_dkms

Edit: strangely, a reboot solved the wireless issue...
i observe the same effect. it happens when hal gets restarted during package upgrades. known, not dangerous, but annoying. restarting the machine, as you said, helps.

ciao,
Mario

---

### Post by cyberdork33 on 2008-12-01
Linked here for info:
[http://ubuntuforums.org/showpost.php?p=6284657&postcount=258](http://ubuntuforums.org/showpost.php?p=6284657&postcount=258)

---

### Post by undoIT on 2008-12-01
ummm... should we get out the champagne?

I deactivated the proprietary Nvidia driver and rebooted. Lo and behold, the echo command and applet that Mario wrote both work to change the brightness in X. You were right Mario, it is a driver issue. Hurray for open source drivers!

I don't even really need the 3D stuff. Has anyone gotten the backlight working for the keyboard in Kubuntu? Is that functionality something specific to the gnome-power-manager package in mactel ppa?

:guitar:

---

### Post by hawkwing3141 on 2008-12-01
> **_mario_ said:**
> ```
glxinfo | grep OpenGL
```
(package mesa-utils) i'm very excited to see the result. perhaps you're running the open-source driver.


Hmmm, I get a segfault when running glxinfo, also as root:
```

Xlib:  extension "GLX" missing on display ":0.0".
...
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
...
2 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Segmentation fault

```

I also found a program called NVIDIA X Server Settings, and when I run it it says I am NOT running the nvidia drivers and that I need to run nvidia-config as root.

but I find this in the syslog:
```

cat /var/log/syslog | grep -i nvidia
Dec  1 14:35:00 tremalking kernel: [   15.684037] nvidia 0000:02:00.0: PCI INT A -> Link[LGPU] -> GSI 23 (level, low) -> IRQ 23
Dec  1 14:35:00 tremalking kernel: [   15.684118] nvidia 0000:02:00.0: setting latency timer to 64
Dec  1 14:35:00 tremalking kernel: [   15.684241] NVRM: loading NVIDIA UNIX x86 Kernel Module  177.80  Wed Oct  1 14:38:10 PDT 2008
Dec  1 14:35:00 tremalking kernel: [   17.576905] mbp_nvidia_bl: MacBook 5,1 detected

```

So I still don't know which driver is actually running...

> 
did you configure some power manager (like gnome-power-manager) to automatically adjust backlight? since you're running KDE, i can't tell how to disable this, but it would be nice to do so to figure out what the reason for this behaviour is.


Aha, thank you.  I may have done it to myself by mistake. I found the software power manager in KDE (Guidance Power Manager, stealthily located as the battery icon in the tray, but not present in the KDE menus) and the brightness levels were set all the way down.  I can't remember if I did this or something else did, but it is fixed now.  Also the slider works so that it changes the brightness on the fly... 

> 
additionally, you might also enable debugging messages by running:
```
echo 1 | sudo tee /sys/module/mbp_nvidia_bl/parameters/debug
```
(since version 0.16). if there are no messages in /var/log/kern.log related to mbp_nvidia_bl when you unplug power, the driver doesn't do anything.


EDIT: debugging works in 0.16, as you say :)

---

### Post by heluani on 2008-12-01
Hmmm, with the update that came in upstream today I can now hit F1-F2 on X and I see the the brightness icon, so I guess the command is being sent... but still only works in TTY (on a Macbook Air 2,1).

R.

---

### Post by pouipschngoku on 2008-12-01
Hi Guys,

While reading this thread one of the posts gave me the idea to enable the pre-release updates in my software sources to see if there were any nvidia related updates out there.

Three relevant updates for the nvidia driver appeared and after installing them and rebooting I can now modify the backlight level from a terminal within the GUI with "sudo pico /sys/class/backlight/mbp_backlight/brightness" and just modifying the value and saving the file - the brightness is adjusted as soon as the save is complete.

I'm guessing that my F1 and F2 keys would also work now had I not screwed up the config when playing around with KDE4 (I tried removing and reinstalling the mactel packages to resolve this to no avail - if anyone has any ideas how to get this back up and running I'm all ears :)).

Anyway I hope this helps a few people and that I'm not just repeating old information that's displayed elsewhere.

If I can provide any information from my system that can help, just tell me what to do and I will be happy to oblige

Cheers

---

### Post by undoIT on 2008-12-02
WOOHOO!! In Ubuntu With Nvidia open source driver, F1 and F2 now work for adjusting the brightness. Suspend does not work with the open source driver :(

@ pouipschngoku

Did you install all of the updates after enabling pre-release? I'm seeing 79 updates including kernel updates.

---

### Post by pouipschngoku on 2008-12-02
@ undoIT: No I unchecked everything but the three nvidia packages

---

### Post by _mario_ on 2008-12-02
> **hawkwing3141 said:**
> Hmmm, I get a segfault when running glxinfo, also as root:
...
So I still don't know which driver is actually running...

no GLX extension means you're running the open-source driver. (and of course it is an Nvidia driver ;-), but one that's not recognized by Nvidia's proprietary tools.) however, the open-source driver has been reported to work within X. that's why i asked, so unfortunately we have still no solution.

ciao,
Mario

---

### Post by _mario_ on 2008-12-02
> **pouipschngoku said:**
> Hi Guys,
While reading this thread one of the posts gave me the idea to enable the pre-release updates in my software sources to see if there were any nvidia related updates out there.

Three relevant updates for the nvidia driver appeared and after installing them and rebooting I can now modify the backlight level from a terminal within the GUI. [...]

If I can provide any information from my system that can help, just tell me what to do and I will be happy to oblige.
yes you can. which repository did you enable? proposed-updates? i'm running with proposed-updates as well, but there's no new version. and: which driver are you using? please run:
```
dpkg -l | grep nvidia
```
and:
```
apt-cache search -n nvidia-kernel
```
and:
```
apt-cache policy nvidia-177-kernel-source
```

thanks & ciao,
Mario

---

### Post by pouipschngoku on 2008-12-02
Hey Mario,

I am running proposed-updates

Here is the output from the commands

dpkg -l | grep nvidia gives me:

ii  hal-nvidia-bl                             0.1.0                                       LCD backlight support
ii  mbp-nvidia-bl-dkms                        0.16                                        Supplementary mbp_nvidia_bl support
ii  nvidia-173-modaliases                     173.14.12-1-0ubuntu4                        Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-177-kernel-source                  177.80-0ubuntu3                             NVIDIA binary kernel module source
ii  nvidia-177-modaliases                     177.80-0ubuntu3                             Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-71-modaliases                      71.86.04-0ubuntu10                          Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-96-modaliases                      96.43.09-0ubuntu1                           Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-common                             0.2.4                                       Find obsolete NVIDIA drivers
ii  nvidia-glx-177                            177.80-0ubuntu3                             NVIDIA binary Xorg driver
ii  nvidia-settings                           177.78-0ubuntu2.1                           Tool of configuring the NVIDIA graphics driv

apt-cache search -n nvidia-kernel gives me:

nvidia-173-kernel-source - NVIDIA binary kernel module source
nvidia-71-kernel-source - NVIDIA binary kernel module source
nvidia-kernel-common - NVIDIA binary kernel module common files
nvidia-96-kernel-source - NVIDIA binary kernel module source
nvidia-177-kernel-source - NVIDIA binary kernel module source

apt-cache policy nvidia-177-kernel-source gives me:

nvidia-177-kernel-source:
  Installed: 177.80-0ubuntu3
  Candidate: 177.80-0ubuntu3
  Version table:
 *** 177.80-0ubuntu3 0
        100 /var/lib/dpkg/status
     177.80-0ubuntu2 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages

Cheers

---

### Post by heluani on 2008-12-02
@pouipschngoku: Installed the latest nvidia drivers as you, still only TTY works

R.

---

### Post by undoIT on 2008-12-02
Has anyone filed a bug report with Nvidia?

---

### Post by _mario_ on 2008-12-02
> **pouipschngoku said:**
> Hey Mario,
I am running proposed-updates
Here is the output from the commands
that all looks like you installed the latest version of nvidia-177-kernel-source and nvidia-glx-177, i.e., 177.80-0ubuntu3 of proposed-updates while 177.80-0ubuntu2 is in Intrepid. that's pretty much the same version.

is the driver really active? does
```
glxinfo | grep OpenGL
```
name NVIDIA corporation as vendor (without crashing)? if not you're still running the open-source driver.

ciao,
Mario

---

### Post by ercoppa on 2008-12-02
Hi, I see [here]("http://www.nvnews.net/vbulletin/showthread.php?t=124059"):
> Added support for the following new GPUs:
GeForce 9400M
:guitar:
 I running to install this driver.

---

### Post by ercoppa on 2008-12-02
Argh, now (with last beta driver) changing brightness (with echo) not works in X11 :(

Some ideas?

---

### Post by pouipschngoku on 2008-12-03
Hi Mario,

glxinfo | grep OpenGL gives me:

OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 9600M GT/PCI/SSE2
OpenGL version string: 2.1.2 NVIDIA 177.80
OpenGL shading language version string: 1.20 NVIDIA via Cg compiler
OpenGL extensions:

I'm not getting any crashing and am using my machine for work so I'm pretty much on it full time

Cheers

---

### Post by _mario_ on 2008-12-03
> **pouipschngoku said:**
> 
glxinfo | grep OpenGL gives me:

OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 9600M GT/PCI/SSE2
OpenGL version string: 2.1.2 NVIDIA 177.80
OpenGL shading language version string: 1.20 NVIDIA via Cg compiler
OpenGL extensions:

I'm not getting any crashing and am using my machine for work so I'm pretty much on it full time.
i meant that glxinfo whould crash if you were running the open-source driver.

however, it looks like you're (a) using the proprietary driver and (b) on a MacBookPro 5. this problem only affects MacBook 5 and MacBook Air 2, so we still have no solution yet.

ciao,
Mario

---

### Post by Nikos.Alexandris on 2008-12-05
I've posted in another thread[1] The News :), but why not also here? The brightness regulation keys F(n)1 and F(n)2 work on the MBP 5,1 with the 3D-effects enabled (activate effects, shutdown, boot).

Regards, Nikos

[1] [http://ubuntuforums.org/showpost.php?p=6311131&postcount=36](http://ubuntuforums.org/showpost.php?p=6311131&postcount=36)

---

### Post by ercoppa on 2008-12-05
> 
The brightness regulation keys F(n)1 and F(n)2 work on the MBP 5,1 with the 3D-effects enabled (activate effects, shutdown, boot). 
Not for me :(
What version of nvidia is installed? Do you have installed hal-nvidia-bl? With 3D-effects enabled, the echo (*echo 15 | sudo tee /sys/class/backlight/mbp_backlight/brightness*) works in X11?

---

### Post by Nikos.Alexandris on 2008-12-05
> **ercoppa said:**
> Not for me :(
What version of nvidia is installed? Do you have installed hal-nvidia-bl? With 3D-effects enabled, the echo (*echo 15 | sudo tee /sys/class/backlight/mbp_backlight/brightness*) works in X11?

Dear ercoppa,
here you go.

1. Driver version
```
nvidia-settings -g | grep version

Xlib:  extension "RANDR" missing on display ":0.0".
  server glx version string: 1.4
  client glx version string: 1.4
  OpenGL version string: 2.1.2 NVIDIA 177.80
```

2. About "hal"
```
lsmod | grep nvidia
mbp_nvidia_bl          12568  0 
nvidia               7804864  38 
i2c_core               36128  1 nvidia
```

3. Yes, the command (you mentioned above) works fine.

Regards, Nikos

---

### Post by _mario_ on 2008-12-06
> **ercoppa said:**
> Not for me :(
What version of nvidia is installed? Do you have installed hal-nvidia-bl? With 3D-effects enabled, the echo (*echo 15 | sudo tee /sys/class/backlight/mbp_backlight/brightness*) works in X11?
the package hal-nvidia-bl shouldn't be necessary. however, i believe, you won't have luck asking Nikos.Alexandris. he's running a MacBookPro 5, while your machine, according to your previous posts, is a MacBook 5. this problem only affects MacBook 5 and MacBookAir 2 in conjunction with Nvidia's proprietary driver. MacBookPro 5's were reported to work, no matter which driver is in use.

ciao,
Mario

---

### Post by heluani on 2008-12-10
Edit: erased not to bother in this thread. _mario_'s answer below could be useful anyway to other users.

---

### Post by _mario_ on 2008-12-10
> **heluani said:**
> I don't mean to hijack this thread (I'll erase/edit this post upon request)
you could have started a new thead, haven't you ;-)

> **heluani said:**
> 
... but I've been trying to get the screen working without the restricted drivers on a Macbook Air 2.1. Indeed the brightness can be controlled within X in this case, but the problem is that I can't get 1280x800. Getting the modeline with gtf and adding the mode with xrandr seems to work fine, but then trying to change the mode either from xrandr or gnome-display-properties just gives an error (configure crtc 0 failed). Is there another method of changing the resolution without the restricted drivers?
which driver are you using? i changed to the open-source driver for testing purposes and it worked. what does:
```
grep "NV: Found" /var/log/Xorg.0.log
```
give? the open-source driver starts all lines with 'NV:'.

you can also list all detected modelines by issuing:
```
grep "NV(0): Modeline" /var/log/Xorg.0.log
```
and a modern display should report all supported modes properly.

however, since the open-source driver doesn't seem to support the 9400M yet (a least it's not listed), could it be that you're using the vesa framebuffer driver? that doesn't support xrandr? just a guess...

ciao,
Mario

---

### Post by joka. on 2008-12-10
> **Nikos.Alexandris said:**
> The brightness regulation keys F(n)1 and F(n)2 work on the MBP 5,1 with the 3D-effects enabled (activate effects, shutdown, boot).

Can anyone confirm this? I've been checking [https://help.ubuntu.com/community/MacBook%20Aluminum](https://help.ubuntu.com/community/MacBook%20Aluminum) for a few days now thinking someone would update the brightness section if the above state is true.

---

### Post by cyberdork33 on 2008-12-11
> **joka. said:**
> Can anyone confirm this? I've been checking [https://help.ubuntu.com/community/MacBook%20Aluminum](https://help.ubuntu.com/community/MacBook%20Aluminum) for a few days now thinking someone would update the brightness section if the above state is true.
that page is not for the MacBookPro5,1, it is for the MacBook5,1.

---

### Post by Nikos.Alexandris on 2008-12-11
> **joka. said:**
> Can anyone confirm this? I've been checking [https://help.ubuntu.com/community/MacBook%20Aluminum](https://help.ubuntu.com/community/MacBook%20Aluminum) for a few days now thinking someone would update the brightness section if the above state is true.

I did not update the page because (a) I have an MBP5,1 and the page is (primarily) for MB5,1s, (b) nobody else tried that out (?)

Regards, Nikos

---

### Post by joka. on 2008-12-11
> **cyberdork33 said:**
> that page is not for the MacBookPro5,1, it is for the MacBook5,1.

All the scripts for that link has to do with macbook pro tho [notice that in some of the scripts they write 'mbp' instead of 'mb']. If not... do you happen to know the link for the macbook pro? If it isn't for the pro then someone should really change the 3rd link under 'About' at [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro) because it sends you to that page.

edit--
> **Nikos.Alexandris said:**
> I did not update the page because (a) I have an MBP5,1 and the page is (primarily) for MB5,1s, (b) nobody else tried that out (?)
Yeaaa... I'm getting really confused :confused::( Maybe someone should start a separate page... 1 for the macbook and another for the pro or specify which script is for which.

---

### Post by Nikos.Alexandris on 2008-12-11
> **joka. said:**
> All the scripts for that link has to do with macbook pro tho [notice that in some of the scripts they write 'mbp' instead of 'mb']. If not... do you happen to know the link for the macbook pro? If it isn't for the pro then someone should really change the 3rd link under 'About' at [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro) because it sends you to that page.

Most of the things work with the MBPro. The machines are pretty similar. But it's better to separate of course. Someone with free-time has to start it.

---

### Post by cyberdork33 on 2008-12-12
[https://help.ubuntu.com/community/MacBookPro5-1](https://help.ubuntu.com/community/MacBookPro5-1)

If you feel inclined, please move the MBP5,1 specific information to the new page.

Also, I changed the base MacBook Pro page.

---

### Post by undoIT on 2008-12-15
Has anyone tried out the latest 180.16 beta driver?

x86_64:
[ftp://download.nvidia.com/XFree86/Linux-x86_64/180.16/](ftp://download.nvidia.com/XFree86/Linux-x86_64/180.16/)

x86:
[ftp://download.nvidia.com/XFree86/Linux-x86/180.16/](ftp://download.nvidia.com/XFree86/Linux-x86/180.16/)

---

### Post by ercoppa on 2008-12-16
Yes, I. No good news.

---

### Post by uager on 2008-12-16
Hallo Folks,
in Intrepid is already mpb-nvidia-bl-dkms v.0.16 implemented, but I still have problems on my Macbook Pro v. 4,1 with the brightness. I can't adjust it at all. Neither it works with F1-F2 or with the brightness applet in the panel(it reports: cannot get laptop panel brightness). Can somebody help me?

---

### Post by _mario_ on 2008-12-18
all patches have been sent upstream ([http://lkml.org/lkml/2008/12/10/336]("http://lkml.org/lkml/2008/12/10/336"), [http://lkml.org/lkml/2008/12/12/293]("http://lkml.org/lkml/2008/12/12/293"), [http://http://lkml.org/lkml/2008/12/12/294]("http://http://lkml.org/lkml/2008/12/12/294")) and now added to the -mm tree.

the issues on MacBook 5 (not MacBook Pro 5) and MacBook Air 2 when using Nvidia's proprietary graphics driver remains unsolved.

ciao,
Mario

---

### Post by _mario_ on 2008-12-18
> **uager said:**
> Hallo Folks,
in Intrepid is already mpb-nvidia-bl-dkms v.0.16 implemented, but I still have problems on my Macbook Pro v. 4,1 with the brightness. I can't adjust it at all. Neither it works with F1-F2 or with the brightness applet in the panel(it reports: cannot get laptop panel brightness). Can somebody help me?
[LIST=1]
[*]ensure that the module gets loaded on boot by adding 'mbp_nvidia_bl' to /etc/modules.
[*]or: load the module manually:
```
sudo modprobe mbp_nvidia_bl
```
[*]check that it's really loaded:
```
lsmod | grep mbp_nvidia_bl
```
[*]change brightness:
```
echo 1 | sudo tee /sys/class/backlight/mbp_backlight/brightness
```
[*]check hal interface:
```
lshal --show /org/freedesktop/Hal/devices/computer_backlight
```
[/LIST]

if step 4 works, but the last command shows nothing you probably started hal before loading the module. so either restart hal:
```
sudo /etc/init.d/hal restart
```
which works immediately or add the module to /etc/modules (step 1 above) and reboot.

ciao,
Mario

---

### Post by uager on 2008-12-19
Many thanks to you. It Works!

---

### Post by ercoppa on 2008-12-25
I was reading [this]("http://www.nvnews.net/vbulletin/showthread.php?t=125251"). Can Nvclock help us?

---

### Post by ercoppa on 2008-12-29
Hi folks, good news (I think) :). I contact nvclock's author to support GeForce 9400M. And now we can adjust backlight in Xorg.

Open terminal and download latest CVS version of nvclock:
```
cvs -d:pserver:anonymous@nvclock.cvs.sourceforge.net:/cvsroot/nvclock login
```
(press enter at password request)
```
cvs -z3 -d:pserver:anonymous@nvclock.cvs.sourceforge.net:/cvsroot/nvclock co -P nvclock
```
```
cd nvclock
```
Compile it:
```
./configure
```
```
make
```
```
sudo make install
```

And enjoy with:
```
nvclock -S 15
```
The value represents a percentuage between 15% (min value) and 100%. You can use also a delta value:
```
nclock -S +10
```

I think that:
```
echo 1 | sudo tee /sys/class/backlight/mbp_backlight/brightness
```
is equivalent to:
```
nvclock -S 13
```
(but this value is not accepted by nvclock)

------------------------------------

How we can control nvclock with F1 & F2? Is it possible introduce the nvclock's hack in mbp_nvidia_bl?

Greets, ercoppa

---

### Post by carrick on 2008-12-29
Worked great for me!  Finally possible to adjust brightness in X.  Thanks!  The only thing I had to change is in the configure step I had to use:

 ./configure --disable-nvcontrol

otherwise it gave the error
 
  "X11 required for nvcontrol support"

This is on my macbook aluminum 5.1.

---

### Post by ercoppa on 2008-12-29
> otherwise it gave the error

"X11 required for nvcontrol support"
I don't have this error :confused:

---

### Post by olavjunior on 2008-12-29
Great! Works like a charm :) (I dint get the error either)

---

### Post by ercoppa on 2008-12-30
Hi, I have update the ["MacBook Aluminium" page]("https://help.ubuntu.com/community/MacBook%20Aluminum#Screen%20brightness%20adjustment") on wiki with the nvclock instructions. Please check this and correct my bad english (or wiki mistakes).

Greets, ercoppa.

---

### Post by ercoppa on 2008-12-30
Hi, I write a script to save & restore backlight level with nvclock at boot/shutdown. It's not a big hack, but works.

Create a script:
```
sudo gedit /etc/init.d/backlight-set
```
and copy this:
```
#! /bin/sh

case "$1" in
    start)
	HOME=/root /usr/local/bin/nvclock -S `cat /root/.backlight`
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
	HOME=/root /usr/local/bin/nvclock -i | grep Backlight | awk '{print $3}' > /root/.backlight
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac

```
Make it executable with:
```
sudo chmod +x /etc/init.d/backlight-set
```
Finally insert in runlevel with:
```
sudo update-rc.d backlight-set defaults
```
And enjoy (I hope).

Greets, ercoppa.

---

### Post by undoIT on 2008-12-30
@ercoppa

Many thanks for the clear instructions installing nvclock and the script. Works great! I had been using the open source driver. I did have to use this command like carrick when installing (perhaps because I installed nvclock before the Nvidia 177.80 driver?)

```
./configure --disable-nvcontrol
```

Now my screen is running at full resolution, I am able to suspend, and brightness is consistent after reboot / suspend. =D>

---

### Post by ercoppa on 2008-12-31
Hi, I add the script to wiki page, but I have trouble with:
```
#! /bin/sh
```
wiki parse it and don't show it in the final page. So I insert with a space before:
```
 #! /bin/sh
```
It's not elegant, but works.

However, I have yet three relevant problem with the graphic card:
- [SOLVED] when I resume from a suspend, the backlight level is too high, how can I execute a script at resume?
- Associate F1 & F2 to nvclock
- usplash at shutdown is corrupted (only for half screen). It's an [open bug]("https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/127280") (and many others) on this, anybody finds a solution?

**EDIT:**
To save & restore backlight level at suspend/resume, create a script:
```
sudo gedit /etc/pm/sleep.d/55backlight
```
and copy in it:
```
#!/bin/sh

# Save & restore backlight level

. "${PM_FUNCTIONS}" || . "${FUNCTIONS}"

case "$1" in
	hibernate|suspend)
		HOME=/root /usr/local/bin/nvclock -i | grep Backlight | awk '{print $3}' > /root/.backlight
		;;
	thaw|resume)
		HOME=/root /usr/local/bin/nvclock -S `cat /root/.backlight`
		;;
	*) exit $NA
		;;
esac

```
Make it executable:
```
sudo chmod +x /etc/pm/sleep.d/55backlight 
```
Please test it (if you want).

Greets, ercoppa.

---

### Post by hyperboloid on 2009-01-01
> **ercoppa said:**
> Hi, I add the script to wiki page, but I have trouble with:
```
#! /bin/sh
```
wiki parse it and don't show it in the final page. So I insert with a space before:
```
 #! /bin/sh
```
It's not elegant, but works.


A more elegant workaround to this problem is posted here: [http://ubuntuforums.org/showthread.php?p=6473653#142]("http://ubuntuforums.org/showthread.php?p=6473653#142"). The solution is to use #!plain on the first line, as in:
```
{{{#!plain
#!/bin/sh
hello world
}}}
```

---

### Post by olavjunior on 2009-01-03
> **ercoppa said:**
> (...)
- Associate F1 & F2 to nvclock
(...) 

This is easily fixed with gconf-editor. Just go to apps -> metacity and add two new global keybindings with XF86MonBrightnessDown and XF86MonBrightnessUp, and also add the nclock commands in keybindings-command (like nvclock -S -10) :popcorn:

Restart X and it works great!

---

### Post by heluani on 2009-01-22
nvclock doesn't work on a Macbook Air 2.1, the video card is not supported. Trying with -f options just spits "Unable to shadow the video bios" 

R.

---

### Post by ercoppa on 2009-01-22
heluani do you have the latest CVS version?
If yes, contact the author of NvClock, his mail is "thunderbird AT linuxhardware DOT org". He helps me with your error on my graphic card.

Greets, ercoppa.

---

### Post by copyrights on 2009-01-25
Yeah, great work!

Next step would be to get data form ambient light sensor to adjust backlight. Has someone already done this?

---

### Post by Freek07 on 2009-01-31
I just installed ubuntu on MBP 5,1 and when I change the brightness, it either turns on or off the backlight (the step is too big).

So..
[ 3870.139766] mbp_nvidia_bl: MacBookPro 5,1 detected
[ 3870.142478] mbp_nvidia_bl: read brightness of 12
[ 3870.142839] mbp_nvidia_bl: setting brightness to 12
[ 3873.260427] mbp_nvidia_bl: setting brightness to 0
[ 3873.819489] mbp_nvidia_bl: setting brightness to 12

The max detected value is 15...is there any way to change the step?

---

### Post by _mario_ on 2009-02-02
> **Freek07 said:**
> I just installed ubuntu on MBP 5,1 and when I change the brightness, it either turns on or off the backlight (the step is too big).

So..
[ 3870.139766] mbp_nvidia_bl: MacBookPro 5,1 detected
[ 3870.142478] mbp_nvidia_bl: read brightness of 12
[ 3870.142839] mbp_nvidia_bl: setting brightness to 12
[ 3873.260427] mbp_nvidia_bl: setting brightness to 0
[ 3873.819489] mbp_nvidia_bl: setting brightness to 12

The max detected value is 15...is there any way to change the step?

no. the driver itself contains no step at all. it's up to the userland to read the current setting and adjust it. what does
```
lshal -u /org/freedesktop/Hal/devices/computer_backlight
```
give?

ciao,
Mario

---

### Post by Nikos.Alexandris on 2009-03-11
Hi folks!

Has anybody installed the 180 version of the nvidia driver on the MBPro(5,1)? Does it work, any improvement?

Cheers, Nikos

---

### Post by buntuLo on 2009-03-12
hi Nikos, i got the nvidia 180.11 driver quite some time ago: everything works as before, which means good :~)
which improvements are you looking for?
ciao, Lo.

---

### Post by Nikos.Alexandris on 2009-03-12
> **buntuLo said:**
> hi Nikos, i got the nvidia 180.11 driver quite some time ago: everything works as before, which means good :~)
which improvements are you looking for?
ciao, Lo.

Thanks Lo.

I installed yesterday. It works :-). I was thinking about 2-D acceleration, the suspend and the reboot issues.

I am not sure if it is directly related but I have the impression that the overall 2D performance is better !?. Suspending and turning on the system does still give me a black screen which is due to brightness set very low and reboot does not work (it never did!).

Cheers, Nikos

---

### Post by buntuLo on 2009-03-12
hi Nikos,
i didn't notice any difference for rendering and graphic acceleration, but i don't use that much graphic power anyway and didn't do any serious testing.
for what i understood, the reboot problem has to do with some EFI variables more than the graphic driver, please correct me if i'm wrong, guys!
suspend (to ram) works flawlessy for me. also hibernate (suspend to disk) does work, even though resuming is pretty slow. when resuming from both suspend modes, i run /etc/rc.local to restore keyboard and display backlight leves and fan speed.

a side note for other KDE users: i got the media keys to control diplay and keyboard backlight simply installing the pacthed gnome-power-manager from the Mactel PPA and removing any other power manager.

cia'cia', Lo.

---

### Post by Nikos.Alexandris on 2009-03-12
> **buntuLo said:**
> ...

a side note for other KDE users: i got the media keys to control diplay and keyboard backlight simply installing the pacthed gnome-power-manager from the Mactel PPA and removing any other power manager.

cia'cia', Lo.

Hey Lo,

do you know if this applies only to KDE?

---

### Post by buntuLo on 2009-03-12
oops, what do you mean? it is designed for gnome, and i heard it does work for gnome users. if you ask instead about xfce, i don't have any idea (but i might guess it will work as it does on kde).
do you use gnome and have troubles controlling backlight levels?

---

### Post by Nikos.Alexandris on 2009-03-12
> **buntuLo said:**
> oops, what do you mean? it is designed for gnome, and i heard it does work for gnome users. if you ask instead about xfce, i don't have any idea (but i might guess it will work as it does on kde).
do you use gnome and have troubles controlling backlight levels?


Sorry, incorrectly formulated before. All I want to say is: the brightness up and down keys do _not_ work for me, and AFAIK, they don't work in general. They do work when I enable the 3D-effects (but that's another thing).

From what you wrote I understand that these keys work for you. Do they?
Cheers, Nikos

---

### Post by buntuLo on 2009-03-12
Nikos,
display backlight control and keyboard backlight control do work for me via the default media keys (on top of f1/f2 and f5/f6) when using gnome-power-manager-2.24.0-1mactel4.
i did have desktop effects enabled (kwin as a window manager, compiz isn't installed here); but now that you say so, i tried to switch them off, checked that compiz is not installed, and rebooted: both backlight controls are still working :~)
how can i help you? any other info? am i really the only one who got them working?

---

### Post by Nikos.Alexandris on 2009-03-12
> **buntuLo said:**
> Nikos,
display backlight control and keyboard backlight control do work for me via the default media keys (on top of f1/f2 and f5/f6) when using gnome-power-manager-2.24.0-1mactel4.
i did have desktop effects enabled (kwin as a window manager, compiz isn't installed here); but now that you say so, i tried to switch them off, checked that compiz is not installed, and rebooted: both backlight controls are still working :~)
how can i help you? any other info? am i really the only one who got them working?

Thanks Lo.

Just to narrow down my problem: it's about the display brightness keys. The keys for the backlit keyboard work fine.

I also have installed the same version of gnome-power-manager. About more info... (?). I'll need some help here concerning what kind of information I would like to receive and give so a cross-comparison is possible.

I don't have currently too much time though.

Did you install anything else except the MacTel packages? Did you install nvclock for example? Any custom scripts you are running?

Thanks in advance, Nikos

---

### Post by buntuLo on 2009-03-13
> **Nikos.Alexandris said:**
> Did you install anything else except the MacTel packages? Did you install nvclock for example? Any custom scripts you are running?
yep, i did install nvclock, as i started playing with that when it was first written a few pages and months ago on this thread. at the time i did succeed controlling display backlight using nvclock from within a script.
all packages from the mactel PPA are installed here, in particular mbp-nvidia-bl-dkms (don't forget to add it in /etc/modules).
echoing values to /sys/class/backlight/mbp_backlight/brightness did also work. unluckily this would interfere with power states: when inserting or removing the plug, brightness was set to 0 or 1 (black screen), and blind typing in the terminal was necessary..
later on i discovered that guidance-power-manager (the default in KDE) was able to control backlight only for the display and within its gui. obviously it did not work before installing mbp-nvidia-bl-dkms.
more, i managed to map brightness up/down to f7/f9 keys (f1/f2 did not work..) and so to control guidance-power-manager (the sliders in its gui were moving while using the keys), hence avoiding interferences with power states.
finally i tried many power manager packages, last one the gnome one: it was the only one which could control also keyboard backlight for me.
so all packages from mactel PPA installed here, and also nvclock. said this, i don't think that gnome-power-manager is using nvclock commands for that.
one last note: i also edited the file /etc/rc.local to lower display brightness from before the KDE-login, which otherwise is set to max till the power manager gets in and dims it:
```
# display brightness [1 to 15]
echo 5  > /sys/devices/virtual/backlight/mbp_backlight/brightness
```
anyway this does not affect the functionality of f-keys.
good morning, Lo.

---

### Post by _mario_ on 2009-03-13
> **Nikos.Alexandris said:**
> Thanks Lo.
Just to narrow down my problem: it's about the display brightness keys.


if you like, let's check whether everything is set up correctly (to be sure):
```

# hal-find-by-capability --capability laptop_panel
/org/freedesktop/Hal/devices/computer_backlight

```
this is the hal device to use to change display brightness.

```

# lshal -u /org/freedesktop/Hal/devices/computer_backlight
udi = '/org/freedesktop/Hal/devices/computer_backlight'
  info.addons = {'hald-addon-generic-backlight'} (string list)
  info.capabilities = {'laptop_panel'} (string list)
  info.category = 'laptop_panel'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.LaptopPanel'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Generic Backlight Device'  (string)
  info.subsystem = 'backlight'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_backlight'  (string)
  laptop_panel.access_method = 'general'  (string)
  laptop_panel.num_levels = 1024  (0x400)  (int)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'backlight'  (string)
  linux.sysfs_path = '/sys/devices/virtual/backlight/nvidia_backlight'  (string)

```
both commands should output suitable information. please note, that i'm running the nvidia_bl driver, but output for mbp_nvidia_bl looks similar.

the first line: 
```
info.addons = {'hald-addon-generic-backlight'}
```
refers to /usr/lib/hal/hald-addon-generic-backlight which is called to change the brightness and should be present (package: hal). hence, the usual echo command should work.

for the function keys to work, the kernel has to emit an appropriate keycode. this work in Intrepid or Jaunty. finally Xorg should have assigned keysyms to each key. can you provide the output of xev when pressing those keys?

ciao,
Mario

---

### Post by Nikos.Alexandris on 2009-03-14
> **_mario_ said:**
> can you provide the output of xev when pressing those keys?

Here you go:

```
# hal capabilities
$ hal-find-by-capability --capability laptop_panel

/org/freedesktop/Hal/devices/computer_backlight

```

```
# hal device to change display brightness
$ lshal -u /org/freedesktop/Hal/devices/computer_backlight

udi = '/org/freedesktop/Hal/devices/computer_backlight'
  info.capabilities = {'laptop_panel'} (string list)
  info.category = 'laptop_panel'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.LaptopPanel'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Generic Backlight Device'  (string)
  info.subsystem = 'backlight'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_backlight'  (string)
  laptop_panel.access_method = 'general'  (string)
  laptop_panel.num_levels = 16  (0x10)  (int)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'backlight'  (string)
  linux.sysfs_path = '/sys/devices/virtual/backlight/mbp_backlight'  (string)
  org.freedesktop.Hal.Device.LaptopPanel.method_argnames = {'brightness_value', ''} (string list)
  org.freedesktop.Hal.Device.LaptopPanel.method_execpaths = {'hal-system-lcd-set-brightness', 'hal-system-lcd-get-brightness'} (string list)
  org.freedesktop.Hal.Device.LaptopPanel.method_names = {'SetBrightness', 'GetBrightness'} (string list)
  org.freedesktop.Hal.Device.LaptopPanel.method_signatures = {'i', ''} (string list)
```


```
# xev
$ xev > xev > xev.F1_F2.txt

## output attached
## I use Alt+F3 (that is, the combination of course and NOT _Alt_ then _plus_ then _F3) instead of Alt+F4 to close windows because F3 is more convenient :-)
## I pressed the keys in the following order:

F1
F2
Alt+F3
```

(With F1 and F2 of course I mean the brightness up and down).

[ATTACH]106403[/ATTACH]

Hope this is useful enough. Cheers, Nikos

---

### Post by Nikos.Alexandris on 2009-03-14
In addition the xev output when I enable compiz (and reboot) and the display brightness keys just work.

The output correspond to 15 times pressing the "F1" key (going from full brightness to zero) and 15 times pressing the "F2" key (going from zero to full brightness).

[ATTACH]106408[/ATTACH]

(With F1 and F2 of course I mean the brightness up and down).

EDIT: The output of ```
lshal -u /org/freedesktop/Hal/devices/computer_backlight
``` is identical as when without compiz enabled.

Cheers, Nikos
---

BTW, I rarely use the effects (I work usually with an external monitor attached) so I would like the keys to work when I don't enable compiz.

---

### Post by philcolbourn on 2009-03-15
```
sudo sh -c 'echo 1 > /sys/class/backlight/mbp_backlight/brightness'
```

May be more intuitive for most users.

> **_mario_ said:**
> Hi all,

the display backlight on those models with Nvidia graphics adapter is always at its maximum brightness after resuming from suspend, but the chip, and thus the driver, still reports the last recently set value. This updated driver fixes this issue, by re-sending the value upon suspend. Can anyone please confirm that it actually works?

Instructions:
1. Install the attached deb package and reload the module:
```
sudo dpkg -i mbp-nvidia-bl-dkms_0.11_all.deb
sudo rmmod mbp_nvidia_bl
sudo modprobe mbp_nvidia_bl
```

2. MacBookPro 3 and 4 users: Set display brightness to some low value, e.g.:
```
echo 1 | sudo tee /sys/class/backlight/mbp_backlight/brightness
```, suspend, resume and report whether it works.

3. MacBook 5 and MacBookPro 5 users: This might also work for the new 5th generation models. I don't have these machines and thus cannot test it. Please check out this driver and report whether it works at all.

4. If it didn't work, remove the package:
```
sudo apt-get remove --purge mbp-nvidia-bl-dkms
```

If you want to have a look, the sources are attached as well.

thanks & ciao,
Mario

EDIT: removed attachments. use the mactel PPA instead.

---

### Post by philcolbourn on 2009-03-15
Seems good. MacBook Pro 4,1

> **_mario_ said:**
> Hi all,

the display backlight on those models with Nvidia graphics adapter is always at its maximum brightness after resuming from suspend, but the chip, and thus the driver, still reports the last recently set value. This updated driver fixes this issue, by re-sending the value upon suspend. Can anyone please confirm that it actually works?

Instructions:
1. Install the attached deb package and reload the module:
```
sudo dpkg -i mbp-nvidia-bl-dkms_0.11_all.deb
sudo rmmod mbp_nvidia_bl
sudo modprobe mbp_nvidia_bl
```

2. MacBookPro 3 and 4 users: Set display brightness to some low value, e.g.:
```
echo 1 | sudo tee /sys/class/backlight/mbp_backlight/brightness
```, suspend, resume and report whether it works.

3. MacBook 5 and MacBookPro 5 users: This might also work for the new 5th generation models. I don't have these machines and thus cannot test it. Please check out this driver and report whether it works at all.

4. If it didn't work, remove the package:
```
sudo apt-get remove --purge mbp-nvidia-bl-dkms
```

If you want to have a look, the sources are attached as well.

thanks & ciao,
Mario

EDIT: removed attachments. use the mactel PPA instead.

---

### Post by _mario_ on 2009-03-16
> **Nikos.Alexandris said:**
> In addition the xev output when I enable compiz (and reboot) and the display brightness keys just work.


the basic stuff up to hal is correctly set up. in addition Xorg seems to produce keysyms, but is there any application listening? what do you use? GNOME? which power manager?

ciao,
Mario

---

### Post by Nikos.Alexandris on 2009-03-16
> **_mario_ said:**
> the basic stuff up to hal is correctly set up. in addition Xorg seems to produce keysyms, but is there any application listening? what do you use? GNOME? which power manager?

Hi Mario.

Not sure which or what kind of "application that is listening" you mean?
I am working with Ubuntu II / 64-bit, Gnome, gnome-power-manager.

Many thanks for your time, Nikos

---

### Post by heluani on 2009-03-20
> **ercoppa said:**
> heluani do you have the latest CVS version?
If yes, contact the author of NvClock, his mail is "thunderbird AT linuxhardware DOT org". He helps me with your error on my graphic card.

Greets, ercoppa.

Are you sure this is the right e-mail address? I can't deliver a mail there.

R.

---

### Post by ercoppa on 2009-03-21
The email is <thunderbird@linuxhardware.org> 

Greets, ercoppa.

---

### Post by _mario_ on 2009-03-24
> **Nikos.Alexandris said:**
> Hi Mario.
Not sure which or what kind of "application that is listening" you mean?
I am working with Ubuntu II / 64-bit, Gnome, gnome-power-manager.


sorry, for answering very late. i've been very busy last week.
nevertheless it works like this: the key press is captured by hald-addon-input and broadcasted through the DBUS system bus, which looks like this:
```
signal sender=:1.0 -> dest=(null destination) serial=1187 path=/org/freedesktop/Hal/devices/usb_device_5ac_231_noserial_if0_logicaldev_input; interface=org.freedesktop.Hal.Device; member=Condition
   string "ButtonPressed"
   string "brightness-down"
signal sender=:1.0 -> dest=(null destination) serial=1190 path=/org/freedesktop/Hal/devices/usb_device_5ac_231_noserial_if0_logicaldev_input; interface=org.freedesktop.Hal.Device; member=Condition
   string "ButtonPressed"
   string "brightness-up"

signal sender=:1.0 -> dest=(null destination) serial=2043 path=/org/freedesktop/Hal/devices/usb_device_5ac_231_noserial_if0_logicaldev_input; interface=org.freedesktop.Hal.Device; member=Condition
   string "ButtonPressed"
   string "kbd-illum-down"
signal sender=:1.0 -> dest=(null destination) serial=2045 path=/org/freedesktop/Hal/devices/usb_device_5ac_231_noserial_if0_logicaldev_input; interface=org.freedesktop.Hal.Device; member=Condition
   string "ButtonPressed"
   string "kbd-illum-up"

```

finally this DBUS signal has to be captured by some application listening to signals. in theory this is gnome-power-manager. if you can see the signal by issuing:
```
sudo dbus-monitor --system
```
and it still doesn't work, gnome-power-manager is buggy. and in fact it seems to be, as it sometimes doesn't work on my machine as well.

ciao,
Mario

---

### Post by Nikos.Alexandris on 2009-03-24
> **_mario_ said:**
> [...]
if you can see the signal by issuing:
```
sudo dbus-monitor --system
```
and it still doesn't work, gnome-power-manager is buggy. and in fact it seems to be, as it sometimes doesn't work on my machine as well.
[...]

Thanks Mario!

Just a quick test with the command above gives the following when I press *Brightness Up* (**F1**):
```
$ sudo dbus-monitor --system
signal sender=org.freedesktop.DBus -> dest=:1.106 path=/org/freedesktop/DBus; interface=org.freedesktop.DBus; member=NameAcquired
   string ":1.106"
signal sender=:1.6 -> dest=(null destination) path=/fi/epitest/hostap/WPASupplicant/Interfaces/0; interface=fi.epitest.hostap.WPASupplicant.Interface; member=StateChange
   string "INACTIVE"
   string "SCANNING"
^C
```

and if I press for example **F2** and then **F1** it takes a while to respond and gives similar messages:
```
$ sudo dbus-monitor --system
signal sender=org.freedesktop.DBus -> dest=:1.107 path=/org/freedesktop/DBus; interface=org.freedesktop.DBus; member=NameAcquired
   string ":1.107"
signal sender=:1.6 -> dest=(null destination) path=/fi/epitest/hostap/WPASupplicant/Interfaces/0; interface=fi.epitest.hostap.WPASupplicant.Interface; member=StateChange
   string "SCANNING"
   string "INACTIVE"
signal sender=:1.6 -> dest=(null destination) path=/fi/epitest/hostap/WPASupplicant/Interfaces/0; interface=fi.epitest.hostap.WPASupplicant.Interface; member=ScanResultsAvailable
signal sender=:1.6 -> dest=(null destination) path=/fi/epitest/hostap/WPASupplicant/Interfaces/0; interface=fi.epitest.hostap.WPASupplicant.Interface; member=StateChange
   string "INACTIVE"
   string "SCANNING"
^C
```

Unknown territory for me all this ;-).

Cheers, Nikos

---

### Post by undoIT on 2009-04-02
Has anyone tried out the Jaunty beta yet and are mactel ppa available? Do I get to be the guinea pig?  :wink:

---

### Post by cyberdork33 on 2009-04-02
> **undoIT said:**
> Has anyone tried out the Jaunty beta yet and are mactel ppa available? Do I get to be the guinea pig?  :wink:
most stuff is available in the ppa. I think there is one package that still needs to be converted.

---

### Post by Nikos.Alexandris on 2009-04-02
> **undoIT said:**
> Has anyone tried out the Jaunty beta yet and are mactel ppa available? Do I get to be the guinea pig?  :wink:

I've just tested the live-cd.

The good news:

* I tried to enable the external monitor and it just worked :-)

[LIST=1]
[*]I activated the NVidia driver (180) which is recommended.
[*]System > Preferences > Display and a message informs to use the vendor's software or something like that. NVIDIA X Server Settings pops-up automatically.
[*]X Server Display Configuration >  Coonfigure > TwinView and it worked :D
[/LIST]

* Only the Volume-Up/Down and Skip-Left/Skip-Right hotkeys work out of the box.

* Then (I think) I've added the Mactel PPA repository for jaunty, updated, upgraded, installed *mbp-nvidia-bl-dkms, applesmc-dkms, bcm5974-dkms*

I loaded these modules manually (sudo modprobe ...). After log-out and *fighting* to log-in without restarting of course, I finally made it and tried all hotkeys again. The display-brightness-keys work :D I have to note that I would expect this to be more responsive (e.g. the system isn't exactly fast at following quick repetitive pressing of the display-brightness-keys)

* The backlit-keyboard-keys did not but I think this will work after a proper restart (!?).

I am attaching some messages like lsmod, dmesg, etc.


Bad news:

Still no sound :-( Although I didn't try to load manually anything related with sound.

Anyhow, I think the situation is getting better and better.

---

### Post by Nikos.Alexandris on 2009-04-02
> **Nikos.Alexandris said:**
> I am attaching some messages like lsmod, dmesg, etc.

More attachments!

I cant upload the dmesg file! It's too big for the forum's limit! If interested I am sending it per-mail.

Cheers, Nikos

---

### Post by cyberdork33 on 2009-04-02
> **Nikos.Alexandris said:**
> More attachments!

I cant upload the dmesg file! It's too big for the forum's limit! If interested I am sending it per-mail.

Cheers, Nikos
zip your logs first

---

### Post by Nikos.Alexandris on 2009-04-02
> **cyberdork33 said:**
> zip your logs first

Right ;-) - Uploaded.

---

### Post by undoIT on 2009-04-02
I have so many other things that need to get done...

...must be patient and wait for stable release...

yes, must...

be patient ;)

---

### Post by cyberdork33 on 2009-04-03
> **undoIT said:**
> I have so many other things that need to get done...

...must be patient and wait for stable release...

yes, must...

be patient ;)
jaunty is pretty stable at the moment... my hardware might be a little better supported though...

---

### Post by heluani on 2009-06-05
Is there anyway of compiling mbp_nvidia_bl_dkms on the latest stable vanilla 2.6.29.4 kernel (I'm having problems building against that kernel), I can attach the make.log if you want.

R.

---

### Post by _mario_ on 2009-06-05
> **heluani said:**
> Is there anyway of compiling mbp_nvidia_bl_dkms on the latest stable vanilla 2.6.29.4 kernel (I'm having problems building against that kernel), I can attach the make.log if you want.


of course. please, attach the log and i'm going to fix what's wrong.

ciao,
Mario

---

### Post by heluani on 2009-06-05
Great, thanks, this is the one trying the .deb, get the same errors compiling the source.

R.

[ATTACH]116513[/ATTACH]

---

### Post by _mario_ on 2009-06-08
> **heluani said:**
> Great, thanks, this is the one trying the .deb, get the same errors compiling the source.


uploaded new packages. as it turns out, i forgot to rename 2 functions.

ciao,
Mario

---

### Post by heluani on 2009-06-09
Great, now it builds, but the Kernel won't boot after installing this module. I'll try to find something relevant in my logs

R.

Edit: Well, it's going to be tough to find the reason. The thing is that none of the Mactel PPA packages builds on this Kernel.

---

### Post by undoIT on 2009-06-10
> **ercoppa said:**
> Hi, I write a script to save & restore backlight level with nvclock at boot/shutdown. It's not a big hack, but works.

Create a script:
```
gksudo gedit /etc/init.d/backlight-set
```
and copy this:
```
#! /bin/sh

case "$1" in
    start)
	HOME=/root /usr/local/bin/nvclock -S `cat /root/.backlight`
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
	HOME=/root /usr/local/bin/nvclock -i | grep Backlight | awk '{print $3}' > /root/.backlight
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac

```
Make it executable with:
```
sudo chmod +x /etc/init.d/backlight-set
```
Finally insert in runlevel with:
```
sudo update-rc.d backlight-set defaults
```
And enjoy (I hope).

Greets, ercoppa.

Hi ercoppa. Have you come up with a script like this for Jaunty? I wouldn't know how to adjust this since nvclock is not neccessary anymore.

---

### Post by Purell on 2009-06-10
I finally got mine working. Thanks for all the tips!

---

### Post by ercoppa on 2009-06-11
undoIT, I am already with Intrepid (no yet ADSL in my new house :() but without nvclock I think that the script is:
```
#! /bin/sh

case "$1" in
    start)
        echo `cat /root/.backlight` > /sys/class/backlight/nvidia_backlight/brightness
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        cat /sys/class/backlight/nvidia_backlight/actual_brightness > /root/.backlight
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac

```

Please, test it for me ;)

Greets, ercoppa.

---

### Post by undoIT on 2009-06-11
> **ercoppa said:**
> undoIT, I am already with Intrepid (no yet ADSL in my new house :() but without nvclock I think that the script is:
```
#! /bin/sh

case "$1" in
    start)
        echo `cat /root/.backlight` > /sys/class/backlight/nvidia_backlight/brightness
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        cat /sys/class/backlight/nvidia_backlight/actual_brightness > /root/.backlight
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac

```

Please, test it for me ;)

Greets, ercoppa.

It works! Thank you much :)

Do you think something similar could be done for the keyboard backlight? It also starts at max brightness each reboot.

---

### Post by ercoppa on 2009-06-11
I think (I don't have the PRO):
```
#! /bin/sh

case "$1" in
    start)
        echo `cat /root/.keybacklight` > /sys/class/leds/smc::kbd_backlight/brightness
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        cat **/sys/class/leds/smc::kbd_backlight/actual_brightness** > /root/.keybacklight
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac
```
Please check the path in bold, I have some doubts that is correct.

Greets, ercoppa.

---

### Post by undoIT on 2009-06-11
There is no actual_brightness, only brightness in that path. I tried creating the script with that but it doesn't seem to work.

---

### Post by heluani on 2009-06-11
Only usbhid-dkms and hid-dkms (from all packages in the PPA) don't compile on 2.6.29.4 so that shouldn't affect mbp-nvidia-bl. Has anyone tried succesfully booting this Kernel with mbp-nvidia-bl? my booting process dies at loading the modules and there's nothing interesting (to me) in the logs.

R.

---

### Post by heluani on 2009-06-12
Blacklisting the module and then loading it manually, the Kernel boots (last stable vanilla Kernel) but the console where one runs modprobe hangs (modprobe never exits)

The module loads and creates the backlight/mbp_backlight/ filesystem, but the process hangs trying to either read "actual_brightness" or write to "brightness"

R.


Edit: using Mario's nvidia_bl module works changing the brightness through nvidia_backlight/brightness and within X!!! I'm just surprised I didn't try this before trying mbp_nvidia_bl!.

---

### Post by _mario_ on 2009-06-18
> **heluani said:**
> Blacklisting the module and then loading it manually, the Kernel boots (last stable vanilla Kernel) but the console where one runs modprobe hangs (modprobe never exits)

The module loads and creates the backlight/mbp_backlight/ filesystem, but the process hangs trying to either read "actual_brightness" or write to "brightness"


what's in your /var/log/kern.log? did the module crash?

> **heluani said:**
> 
Edit: using Mario's nvidia_bl module works changing the brightness through nvidia_backlight/brightness and within X!!! I'm just surprised I didn't try this before trying mbp_nvidia_bl!.

in general, nvidia-bl is the better module, but doesn't support the MacBook Pro 5. do you have a MacBook Pro 5?

ciao,
Mario

---

### Post by ercoppa on 2009-06-19
undoIT, the script for the keyboard simply (Mario helps me) is:
```
#! /bin/sh

case "$1" in
    start)
        echo `cat /root/.keybacklight` > /sys/class/leds/smc::kbd_backlight/brightness
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        cat /sys/class/leds/smc::kbd_backlight/brightness > /root/.keybacklight
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac
```

Test it (I don't have PRO).

Greets, ercoppa.

---

### Post by undoIT on 2009-06-19
> **ercoppa said:**
> undoIT, the script for the keyboard simply (Mario helps me) is:
```
#! /bin/sh

case "$1" in
    start)
        echo `cat /root/.keybacklight` > /sys/class/leds/smc::kbd_backlight/brightness
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        cat /sys/class/leds/smc::kbd_backlight/brightness > /root/.keybacklight
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac
```

Test it (I don't have PRO).

Greets, ercoppa.

This works, but after logging in, once the desktop is loaded, Gnome resets the brightness to 100%. So there is somewhere else that the brightness is being set. I edited the settings in gconf-editor so that keyboard brightness is 0 for both AC and battery, but still Gnome insists on 100%.

---

### Post by _mario_ on 2009-06-21
you can also change:
> **ercoppa said:**
> 
```
echo `cat /root/.keybacklight` > /sys/class/leds/smc::kbd_backlight/brightness
```

to:
```
cat /root/.keybacklight > /sys/class/leds/smc::kbd_backlight/brightness
```

> **undoIT said:**
> This works, but after logging in, once the desktop is loaded, Gnome resets the brightness to 100%. So there is somewhere else that the brightness is being set. I edited the settings in gconf-editor so that keyboard brightness is 0 for both AC and battery, but still Gnome insists on 100%.

this is gnome-power-manager, that for some reason i don't know, always sets the keyboard brightness to maximum when starting.

ciao,
Mario

---

### Post by undoIT on 2009-06-21
> **_mario_ said:**
> this is gnome-power-manager, that for some reason i don't know, always sets the keyboard brightness to maximum when starting.

Bad gnome... Obey my commands!

;)

---

### Post by mulbric3 on 2011-08-21
Unfortunately this is** not working** on my Macbook Pro 3,1.
**The archive is not found!**

This is driving me nuts. I'm new too Linux Mint 11. Some problems like Blueooth and Sound took me forever to fix.

I'm not sure if this helps. I've got the following packeges installed:

nvidia-common
nvidia-current
nvidia-settings

Thank you for any help.

---

### Post by mulbric3 on 2011-08-22
Help!

---

### Post by mbradlcu on 2011-12-08
I don't see any option with nvidia-settings, but apparently the brightness can be set via CL:
```
sudo echo "100" > /sys/class/leds/smc\:\:kbd_backlight/brightness
```

I'm using ubuntu 10.04 lts

---

