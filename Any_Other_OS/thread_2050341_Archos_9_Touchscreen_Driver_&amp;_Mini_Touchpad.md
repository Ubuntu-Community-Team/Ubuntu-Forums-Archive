---
title: "Archos 9 Touchscreen Driver &amp; Mini Touchpad"
date: 2012-08-30
forum: Any Other OS
---

### Post by MarkL2012 on 2012-08-30
Hi Everyone,

I've been using Linux Mint for a while now and am happy to discover that the Maya version works 90% on my Archos 9. [COLOR="Blue"]However no one is helping me on their forums and since it's based on Ubuntu[/COLOR]. I'm hoping someone can help me here. I'd like to clarify that I use KDE as a Window Manager and I think it comes from Kubuntu.

There are 2 problems that I need help with and I'm aware of the tutorials, but they are outdated. At least the last time I went through them. 

Touchscreen (eGalax Touch - PS/2)
I've found the latest drivers on their website because they weren't in the Repos ([http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm](http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm)) and I've read through the documentation. However, I don't understand what I'm suppose to write where because it primarily deals with the USB interface but I know for a fact that the Archos 9 uses the PS/2 interface. I've Googled for tutorials but they are all outdated and the main problems are dealing with Xorg/Kernel versions. So, I am hoping someone who knows more about installing drivers from source and recompiling the Kernel or whatever I'm suppose to do, can give me a step by step guide. 

What I do know is that it will work because people got it to work with Ubuntu. Also I'm using the latest kernel in the repos and yes they are the same repos between Linux Mint 13 and Ubuntu.

Mini Touchpad (Same PS/2)
I would like to get this to work for compatibility reasons and it does work on GRUB but it doesn't work after that (somewhere between the boot menu and when X starts it fails). I researched this a bit and someone got it going by using evtouch but doesn't explain it. Not only do I have evtouch already installed with it not working but apparently it stops working again if you install the touchscreen drivers. So, my solution to this is to somehow record the input data that the mini touchpad gives when you touch it and use a program to convert it into relevant keystrokes. This will allow me to use it with accessibility options in KDE. However, I don't know of any programs to do that in Linux, I only did that a long time ago in Windows. 

What I do know is that, although it doesn't appear to work, it does, but the input data isn't understandable by Linux either with the touchscreen drivers installed or not. Also there is the problem that the Touchscreen and Touchpad share the same PS/2 interface.

I should be able to get these things working with your help and I would greatly appreciate any info, anyone can provide.

Here is the link too the post I made on the Linux Mint forums.
[http://forums.linuxmint.com/viewtopic.php?f=109&t=110554]("http://forums.linuxmint.com/viewtopic.php?f=109&t=110554")

Thanks for taking time to read this and sorry to anyone who doesn't like my bluntness. I'm frustrated that I can't get this done before college starts for me and my main PC is getting some hardware maintenance don't to it.

---

### Post by MarkL2012 on 2012-09-01
I was looking at the install instructions yesterday with a friend and I believe that I just have to install the [COLOR="Blue"]setup.sh[/COLOR]. However, I have on idea how to work the Terminal other than copying and pasting things into it. Also I'm presuming that any distro would be capable of making a kernel patch module because thats how all the other drivers are install, right?

So, please can someone tell or give me the exact line of commands I have to paste into the terminal to get this thing working.

Thanks

---

### Post by gordintoronto on 2012-09-01
Mint with KDE should be similar to, but more complicated than, Kubuntu. Have you considered trying Kubuntu?

I suggest you have a look at modprobe. It might be a lot simpler to load your driver than you think it is. In terminal: man modprobe

To exit from "man" press q.

---

### Post by MarkL2012 on 2012-09-04
Ok, I was right about running setup.sh but unfortunately it wasn't the latest version. A new version came out today and it installed flawlessly.

However, the mini touchpad and the touchscreen worked erratically and wouldn't let me calibrate it. So, I followed the instructions from the tutorials before and after much tinkering. The problem was enabling serial_raw at boot.

The tutorials and the sh script do it differently but this line has to be commented out. 

"echo -n "serio_raw" > /sys/bus/serio/devices/serio1/drvctl"

Both in "rc.local" and in the serial_raw file/script in "rcS.d".

What this does is it makes the mini touchpad into a normal touchpad (obviously without double tap or anything) and the touchscreen acts like a gigantic inverted touchpad.

I have no idea how to change the touchscreen's behavior and personally, at this point I don't really care. This is because I only ever used it to get to buttons faster on the screen than using the normal mouse (which by the way, the buttons **_do_** work).

If someone wants to get further on the Touchscreen issue I'm glad to try and help. I tried everything I could think of but still it refuses to work like it does under Windows 7.

Thankfully, there are ways to change the input from the touchscreen through uinput and evdev but I'm not going to do that for a while, yet.

Thank you _gordintoronto_ for trying to help me. You are the only one that did.

---

