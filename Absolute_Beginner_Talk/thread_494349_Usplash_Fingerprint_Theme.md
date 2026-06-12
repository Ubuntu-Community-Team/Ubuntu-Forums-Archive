---
title: "Usplash Fingerprint Theme"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by snwbord2456 on 2007-07-06
Hey, first I'd like to say this forum has been amazing and really helpful these past few days and has allowed me to keep my sanity, thanks to anyone who has helped its been much appreciated. Now to yet another problem. I want to install and run the theme:

[https://sourceforge.net/projects/u-fingerprint/](https://sourceforge.net/projects/u-fingerprint/)

I've downloaded the 0.1 stable version and used the howto here:

[https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765](https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765)

and I've gotten all the way to the installation part and when I enter:

mark@Mark:~/Desktop$ sudo cp usplash-theme-fingerprint.so /usr/lib/usplash 
 
 
I got the error: 
 
cp: cannot stat `usplash-theme-fingerprint.so': No such file or directory 
 
 
I tried searching in the usplash-fingerprint sources file as well as running a search on my comp for usplash-theme-fingerprint and found nothing. 
 
Any help would be greatly appreciated. 
Thanks again.

---

### Post by abn91c on 2007-07-06
you did not really say but you can install kdm theme manager if you are running Kubuntu(KDE) to change the matching log  in screen available at [www.kde-look.org](www.kde-look.org). If you install kde the fingerprint is included.
sudo apt-get kubuntu-desktop

---

### Post by overdrank on 2007-07-06
> **snwbord2456 said:**
> Hey, first I'd like to say this forum has been amazing and really helpful these past few days and has allowed me to keep my sanity, thanks to anyone who has helped its been much appreciated. Now to yet another problem. I want to install and run the theme:

[https://sourceforge.net/projects/u-fingerprint/](https://sourceforge.net/projects/u-fingerprint/)

I've downloaded the 0.1 stable version and used the howto here:

[https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765](https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765)

and I've gotten all the way to the installation part and when I enter:

mark@Mark:~/Desktop$ sudo cp usplash-theme-fingerprint.so /usr/lib/usplash 
 
 
I got the error: 
 
cp: cannot stat `usplash-theme-fingerprint.so': No such file or directory 
 
 
I tried searching in the usplash-fingerprint sources file as well as running a search on my comp for usplash-theme-fingerprint and found nothing. 
 
Any help would be greatly appreciated. 
Thanks again.

Hi and yes I just installed sorry it took so long. In the read me text it says to copy all the files to your desktop file. so If you download the file to your desktop the open and archive to your desktop you still need to copy and past the usplash-theme-fingerprint.so (edit) onto the desktop. I am so proud that is the first of that kind lol good luck!

---

### Post by snwbord2456 on 2007-07-06
Which of these should I add the vga=791 to?

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=31d22bf9-9773-4040-a46f-3712956fec33 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=31d22bf9-9773-4040-a46f-3712956fec33 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=31d22bf9-9773-4040-a46f-3712956fec33 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=31d22bf9-9773-4040-a46f-3712956fec33 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

because they all say quiet at the bottom instead of boot and none say locale = en

---

### Post by overdrank on 2007-07-06
```
> **snwbord2456 said:**
> Which of these should I add the vga=791 to?

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=31d22bf9-9773-4040-a46f-3712956fec33 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=31d22bf9-9773-4040-a46f-3712956fec33 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=31d22bf9-9773-4040-a46f-3712956fec33 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=31d22bf9-9773-4040-a46f-3712956fec33 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

because they all say quiet at the bottom instead of boot and none say locale = en

```
I personally skipped that portion of the install and it worked great. lol
:D

---

### Post by snwbord2456 on 2007-07-06
I skipped the VGA thing, but I extracted the FingerpringSourcers. tar.gz to my desktop and got usplash-fingerprint-sources and yet I still get

mark@Mark:~/Desktop$ sudo cp usplash-theme-fingerprint.so /usr/lib/usplash
cp: cannot stat `usplash-theme-fingerprint.so': No such file or directory

---

### Post by overdrank on 2007-07-06
> **snwbord2456 said:**
> I skipped the VGA thing, but I extracted the FingerpringSourcers. tar.gz to my desktop and got usplash-fingerprint-sources and yet I still get

mark@Mark:~/Desktop$ sudo cp usplash-theme-fingerprint.so /usr/lib/usplash
cp: cannot stat `usplash-theme-fingerprint.so': No such file or directory

Hi and that is what I edited this post earlier
**Hi and yes I just installed sorry it took so long. In the read me text it says to copy all the files to your desktop file. so If you download the file to your desktop the open and archive to your desktop you still need to copy and past the usplash-theme-fingerprint.so (edit) on to the desktop.** I am so proud that is the first of that kind lol good luck!
:D

---

### Post by snwbord2456 on 2007-07-06
So you've made it idiot-proof, almost....

I extracted the file then when i right-click on the usplash-fingerprint-sources and goto archive I see the option of archiving to the desktop in:

.tar.gz
.tar.bz2
.tar
.zip
.ar
.ear
.jar
.war

I don't see .so, what am I doing wrong? Do I have the correct files extracted? Sorry for the step-by-step need, I'm really new.

---

### Post by overdrank on 2007-07-06
HI PM me please ( private message) and I will try and help!

---

### Post by snwbord2456 on 2007-07-06
So I tried to install the theme by creating an empty file on my desktop named usplash-theme-fingerprint.so and the howto guide seemed to work, but now on start-up it shows the text of everything starting up, then goes to the ubuntu start up-screen. And when rebooting (havent shut down yet) it shows a text prompt of GNOME shutting down. What did  I do?

---

