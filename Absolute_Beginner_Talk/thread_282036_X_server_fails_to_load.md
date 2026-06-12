---
title: "X server fails to load"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by G-Prime on 2006-10-22
Hello

I just installed Ubuntu for the first time and it all went smoothly, then I rebooted the system like it told me and when it started to boot it told me that the x server failed to load and showed a screen sort of like the earlier install screen but with random weird characters, the detials in the error message said something about the graphics and it gave me this "/var/log/xorg.o.log" after that it took me to a black screen asking me to log in....it was very much in the fashion of DOS


I'm not entirely sure what this means as it's my first time with Linux

I installed the genereic x86 intel version of Ubuntu

and if it makes any difference or helps I have a Conroe e6600 processor and ATI x1900xt GPU

---

### Post by taurus on 2006-10-22
Go ahead and log in with your username and password.  Then at the prompt, reconfigure your X again with

```
sudo dpkg-reconfigure xserver-xorg
(use the same password that you use to log in...)
sudo /etc/init.d/gdm start
```

---

### Post by jorn on 2006-10-22
You may also want to read this:
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

---

### Post by Mortimer5 on 2006-10-22
> **taurus said:**
> Go ahead and log in with your username and password.  Then at the prompt, reconfigure your X again with

```
sudo dpkg-reconfigure xserver-xorg
(use the same password that you use to log in...)
sudo /etc/init.d/gdm start
```

I've been having the same problem. I tried this and went through the configuration but it still doesn't work. I tried what someone else suggested and went into the configuration file to modify it, but I found that the file is totally blank.

Any help would be appreciated.

Here's the info:

Toshiba Satellite A105-S4334 laptop, 15.4” diagonal widescreen TruBrite™ TFT active-matrix LCD
display at 1280x800 native resolution (WXGA), Intel Graphics Media Accelerator 950 with 8MB-128MB dynamically
allocated shared graphics memory, Ubuntu version 5.10

---

### Post by taurus on 2006-10-22
When you said you wanted to modify it but it was blank, what exactly did you type to modify it?  What is the output of this command then?

```
ls -la /etc/X11/xorg.conf
```
And if you want to modify it, you can either use GUI or text base...

```
gksudo gedit /etc/X11/xorg.conf <-- for GUI editor
sudo nano /etc/X11/xorg.conf <-- for text editor
```

---

### Post by G-Prime on 2006-10-22
Hey everyone

Thanks for the help, I got Ubuntu to work, i'm now useing it and playing around for the first time :) I love the multiple workspace feature

Anyways, about the problem I had
after I reconfigrued my GPU and monitor and pressed ctr+alt+f7 then ctrl+alt+backspace to reboot the GUI it wouldn't respond to that or the command line sudo /etc/init.d/gdm start, it just stayed in the dead state nothing worked, so I fiddled around for an hour then after reading the link that was posted I tried using the command startx which kicked it into gear and booted up and fixed the problem,

so to the other guy that was having the same problem as me, if you still are I hope that helps you

anyways, thanks again for the help.

---

### Post by Mortimer5 on 2006-10-22
When I try the startx command it says 'Fatal server error: no screens found' and at thee bottom of the screen it says:

XIO: fatal IO error 104 (connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining.

Also, when I tried "gksudo gedit /etc/X11/xorg.conf" it says "Gtk-WARNING **: cannot open display:"

When I put in "ls -la /etc/X11/xorg.conf" the output is:

-rw-r--r-- 1 root root 3097 2006-10-22 14:16 /etc/X11/xorg.conf

I think I'm probably doing something wrong when configuring the X server. It might also have something to do with it being a laptop. I had the same problem with the Live CD. It just doesn't accept the display.

---

### Post by taurus on 2006-10-22
Did you try to run the command to reconfigure your X again?

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Mortimer5 on 2006-10-22
I just tried reconfiguring it again and still no result. I have the laptop set up for dual-booting so I'm going to go into Windows to try to find out everything I can about the display in case I'm giving it the wrong info.

---

### Post by Mortimer5 on 2006-10-22
All right, I went into Windows and wrote down everything I could find about the display setup, including the things I hadn't been sure of like the PCI bus. Then I got back into Ubuntu and tried reconfiguring it again with the official information, and got exactly the same result as every other time. It keeps saying that it can't find any devices. I'm going to try it again a few times, and hopefully in that time someone will think of something that will get me out of this mess. I wonder if I'm going to need to try installing Dapper Drake instead.

---

### Post by Mortimer5 on 2006-10-22
There is absolutely NOTHING in the /etx/X11/xorg.conf file. Whenever I finish reconfiguring it says that it's saving a backup, so I've checked the backup and it's also blank.

---

### Post by bulldog on 2006-10-22
Well a copy of a blank sheet will be a blank sheet I suppose.

You can try ```
sudo dpkg-reconfigure -phigh  xserver-xorg
``` but I'll doubt if it gets you anywhere.

There should be a standard config in your xorg.conf which you can alter a bit ,but a blank sheet isn't going to help.

It's /etc/X11/xorg.conf btw,but it will be a typo I think.

---

### Post by tseliot on 2006-10-22
> **Mortimer5 said:**
> There is absolutely NOTHING in the /etx/X11/xorg.conf file. Whenever I finish reconfiguring it says that it's saving a backup, so I've checked the backup and it's also blank.

it's etc and not etx

anyway you can try this:
boot in RECOVERY MODE from the GRUB Menu (select it using your keyboard) almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

Type:
```
reboot
```

On next reboot the Xserver should work fine


NOTE: if the problem is not solved try using "vga" instead of "vesa" and try again.

---

### Post by Mortimer5 on 2006-10-22
Yes, etx was a typo, but it seems that I wrote it in wrong on the laptop as well. False alarm - the file ISN'T blank. Now I feel like a moron. I'm going to try rebooting in recovery mode and if that doesn't work I'll find the solution to this problem that I read earlier involving the modification of the configuration file and see if it works.

---

### Post by bulldog on 2006-10-22
> **Mortimer5 said:**
> Yes, etx was a typo, but it seems that I wrote it in wrong on the laptop as well. False alarm - the file ISN'T blank. Now I feel like a moron. I'm going to try rebooting in recovery mode and if that doesn't work I'll find the solution to this problem that I read earlier involving the modification of the configuration file and see if it works.

We all make mistakes,don't worry :D 

Hope you get it to work,that's the important thing.

Succes

---

### Post by Mortimer5 on 2006-10-22
Well, thank you everyone! I reconfigured it in recovery mode, and it seems to be working now. I'm glad that's over!

---

