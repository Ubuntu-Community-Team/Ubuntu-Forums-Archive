---
title: "Ubuntu Live CD MacBook Pro Graphics Issue"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by RobCon on 2006-12-31
Hi,

I wanted to try out Ubuntu so I burned a DVD of 6.10 earlier to use the live CD to get a sample. I'm now having a problem. Well, two really. One; I couldn't figure out how to boot from CD/DVD on my XP PC, so I gave up knowing that I could do it on my MBP. I did manage to do it and got to the intro menu. I selected to start the CD and a dialog box said something about the Linux kernal and started loading. After this though the screen goes all bad. It basically looks like an analogue TV signal that's out of tune; diagonal lines everywhere. The only things I can make out are the color scheme and the line of dots that meant to be a cursor. I tried safe graphics mode and different resolutions also but the exact same thing happens. My graphics card is the default one I suppose. I haven't changed anything about the machine since I bought it so they'd have to be.

If anyone knows what the heck I need to do to just use the DVD I'd be most grateful. Sorry if this is a simple enough problem. My experience with Linux began only about three hours ago.

Thanks.

---

### Post by NeoLithium on 2006-12-31
Well, I might suggest that you make sure you have the PPC Ubuntu disk for your macbook, and as for your windows PC, that might be why it didn't load, it would need either the x86 or x86_64 disk to load live.  As well, if it didn't TRY to run the disk on boot, you might want to enter bios with [ESC] when you start up; and see that it tries to boot from the CD Drive before it tries the hard drive.

Just a few simple suggstions that might help ya out :)

---

### Post by RobCon on 2006-12-31
Hey,

Thanks for replying. I didn't know to hold ESC during boot on my PC. I was trying every Function button instead. Anyway, I managed to boot it now but after selecting Start on the menu screen it's just stuck on the loading screen and not getting past it. It's possible that it's just taking a while since the PC is a little slow and the drive isn't making it's usual racket. I'll try again tomorrow when I can leave it for a while longer than I can at the moment.

About the Mac part. I was actually thinking that if I liked it that I'd most likely install it on my MBP since it's the much faster of my two units. Would I actually need the PPC version on an Intel Mac? I thought the PC version would work.

Again, thanks for replying. And so fast too.

---

### Post by NeoLithium on 2006-12-31
Ah, with the Intel of a Macbook, x86 version is what to use :)

---

### Post by hiadam on 2007-01-03
I have the same issue .. the Live Cd boots but the screen shows everything skewed in diagonal lines.  Haven't found a solution yet; maybe the live CD doesn't have the right drivers for this display.  If that was the problem then I could create a live CD with the correct drivers.  I'll post here if I find a solution.

---

### Post by RobCon on 2007-01-04
I'd appreciate that. Thanks.

---

### Post by simoncullen on 2007-01-06
Bump: Same problem here.  Macbook Pro, 17", 2.16Ghz .... Any help, Infinitely appreciated!

---

### Post by hiadam on 2007-02-02
I recently tried Knoppix 5.1 Live and found that its scripts deliver a working xorg.conf file.  So here's a few steps I followed to get X working correctly on my 20" intel Imac.

1)  Download the attached xorg.conf.txt onto a USB stick.  Rename it to xorg.conf  (simply remove the .txt extension).

2)  Boot Edgy Live CD.  At the initial prompt, hit F4 to change the resolution.  I chose the third  option from the bottom and that worked fine.  Then choose Safe Graphics mode and boot.

3)  When X launches (you'll see things in diagonal lines), type Ctrl+Alt+2 to get into Terminal 2.  You can actually choose any number between 1 and 6, X runs in terminal 7 so if you want to go back you can hit Ctrl+Alt+7.  You should now see a command prompt, something like 
```

ubuntu@ubuntu ~$
```

4)  Plug in the USB stick.  Since Gnome is running in the background, it will automount the USB stick somewhere in /media.  Give it a few seconds to mount (you'll probably see some text in your console while it's mounting) and then run the following:
```

$ ls /media
```

In my case, this showed me that the USB stick was at /media/usbdisk.  Now copy the xorg.conf.txt into your ubuntu system like so:
```

$ sudo cp /media/usbdisk/xorg.conf.txt /etc/X11/
```
If you are prompted for a password, it's "ubuntu".

5)  Xorg reads its configuration file at startup so you can get your fixed X several ways:
a)  Type Ctrl+Alt+F7 to get back to Gnome, then type Ctrl+Alt+Backspace (delete on the Mac keyboard) to reset X.
b)  Or restart X from the command line:
```

$ sudo killall gdm
$ sudo gdm start
```

I'm thinking of starting a How-to specifically for 20" imacs, so far there's not much out there.  We'll see how the next week goes.

---

