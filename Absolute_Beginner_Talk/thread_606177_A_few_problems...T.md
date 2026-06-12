---
title: "A few problems...T"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by SamTyson92 on 2007-11-07
I've installed Linux (Ubuntu) about 5 times now and this time it finally worked!

But I have a few problems:
- When I boot into Ubuntu I see none of the booting text and it just stays black for about 2/3 minutes then loads the login screen, is there any way to change this?
- The restricted driver manager will not let me install the driver for my ATI Radeon Xpress 200M graphics card.
- I tried using the terminal to install the drivers but it wont let me type when it asks for my password! and copy and paste wont work.

And it also freezes sometimes, which used to happen before.

Please help ASAP because if I can't fix some of these problems I might just give up on Linux completely as it's never worked properly so far.

System Specs:
Intel Celeron M 410 CPU @ 1.46 GHz
512 MB RAM (getting upgraded to 1.5GB in a few days)
55 GB HDD (10 GB for Linux)
ATI Radeon Xpress 200M Graphics Card 128MB Shared Memory

---

### Post by aktiwers on 2007-11-07
for this:
> I tried using the terminal to install the drivers but it wont let me type when it asks for my password! and copy and paste wont work.

Just type it. It will register your typing, it will just not show anything (yes not even stars).

---

### Post by underdog512 on 2007-11-07
[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

This should help w/ ATi drivers.  Keep in mind that Nvidia drivers come w/ ubuntu out-of-the-box.  you don't even get that w/ windows.


the thing to remember when entering a password in the terminal is that you will not see ***** or anything for that matter.  Just type out your password and press enter.  as far as the copy/paste thing in terminal you can't use keyboard shortcuts ie. Ctrl-c and ctr-v.  

you have two options:

Edit > Paste

or

right-click > Paste





Not sure what to tell you about the boot screen but someone else in here should be able to help you with that.

---

### Post by ubnewbie2 on 2007-11-07
> **underdog512 said:**
> 

Not sure what to tell you about the boot screen but someone else in here should be able to help you with that.

Install startupmanager and set grub to use an appropriate screen size - I used 1024x768 16 colour.  This fixed it for me (and some others)

---

### Post by Paul820 on 2007-11-07
I have exactly the same card in my laptop. Do you have the restricted repositories enabled? Go to System-> Adminitration->Software Source and enable them, then update the list and you should be able to install the drivers.

If you install xserver-xgl, you will also get compiz fusion working. :) It's been fixed for our cards.

> Install startupmanager and set grub to use an appropriate screen size - I used 1024x768 16 colour. This fixed it for me (and some others)

That's exactly what i did, mine was set to 640x480 and it was taking nearly 3 minutes to boot. X was probably having trouble trying to figure out my screen resolution. Now it takes 24 seconds so give that a go.

---

### Post by jaybombalous on 2007-11-07
> When I boot into Ubuntu I see none of the booting text and it just stays black for about 2/3 minutes then loads the login screen, is there any way to change this?


I have not fixed this issue yet, so instead I did a 

```
gksudo gedit /boot/grub/menu.lst 
```

I am gonna take that back...

You do this instead after u do that ^^^

Find #defoptions and remove quiet and splash that is present on that line, then do this

```
sudo update-grub
```

Edit: I had no idea what I was thinking before, my mistake.

---

### Post by Stikky on 2007-11-07
Hey there,

I have an ATI card in my laptop and i didnt have any problems at all so I can't help you with that one..

The password will be registered, as a previous poster said; just type your pw and press enter, nothing will show but it should work.

I had the same boot problem, it took ages and it would go blank for like 3 minutes. In the short term, you can press "Ctrl + Alt + F1" (might be a different F key for you, was F1 for me) and it wil show you what it's actually doing. Obviously, this is less than desireable so I will tell you what I did, step by step:

1.) Open a terminal
2.) Type
```
sudo gedit /etc/usplash.conf
```
3.) Enter your password (as we discussed above)
4.) I dont have a Linux comp with me at the moment but it should have 3 lines, one will be a vertical resolution and one will be horizontal, should be clear which. Mine was set to 1208x1024 by default
5.) Change the resolution to the native res of your screen, if you dont know what it is, assume 1024x768
6.) Save the file
7.) Open another terminal
8.) Type
```
sudo update-initramfs -u -k `uname -r`
```
***Note**: Those are not inverted commas, they are "back ticks" or something, on the tilda key. Just copy and paste that if you can..*

9.) Enter your password and let it do it's thing
10.) Reboot, hopefully you'll see the splash screen and everything will boot faster, it did for me!!

Hope this helps, I didnt figure this out on my own, someone else told me how to do it in another thread so I can't take credit. Let us know if it's still not working, I prolly wont be able to help but smoeone else will!!

---

### Post by dhobbs on 2007-11-07
To make sure the boot up screen isn't trying to display at an improper resolution you should do the following

In a terminal type:```
sudo gedit /boot/grub/menu.lst
```
Near the bottom of that file you should see a line that looks similar to this```
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f03e3909-d374-4460-9f3b-ce9eaec282a8 ro quiet splash
```
If you see that 'splash' is there then that's fine, don't edit anything and just close the file.  If you see 'nosplash' change that to 'splash', save and close the file.

I'm assuming that because you are experiencing a slow startup that 'splash' is in the command and grub is trying to use a bad resolution.

To fix that we'll do a couple of things:
First, in a terminal type:```
sudo gedit /etc/usplash.conf
```
This file should look like this:```
# Usplash configuration file
xres=1280
yres=1024
```
It should match the resolution you use while in the GUI.  Edit that file to what you need, save and close.

Now you need to let grub know that it needs to use the updated resolution so we do the following:
Open a terminal and type:```
sudo update-initramfs -u -k `uname -r`
```
Please not that ` is not a single quote, it is a 'tick' on the same key as the 'tilde' - ~.  It is usually found in the upper left corner of the keyboard.

That command should produce output like this:```
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
```
To test out the boot splash just restart the system.

I hope this works, if not let us know.

---

### Post by Stikky on 2007-11-07
> **Stikky said:**
> I didnt figure this out on my own, someone else told me how to do it in another thread so I can't take credit.

And dhobs here was the one who told me how to do it in another thread :)

Haha.

---

### Post by SamTyson92 on 2007-11-08
It's all worked!
Well I had to install ubuntu again as I changed some settings I shouldn't but took all your advice and Linux Rules!

Go Linux!
Thanks Everyone

:lolflag:

---

