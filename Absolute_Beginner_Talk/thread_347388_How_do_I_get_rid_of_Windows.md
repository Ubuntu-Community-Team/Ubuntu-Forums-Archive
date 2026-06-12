---
title: "How do I get rid of Windows?"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-01-27
I need your opinion on this. I have been expecting to completely switch to Linux as soon as possible so that I can completely get rid of Windows.

[B]
The obstacles[/B]

1. Lack of recognition
Whenever I want to download an application, screensaver, or whatever, most of the time, there is no love for Linux! I was scrolling the window down when I was browsing the Cashflow101 Game page and the game was only for Windows and Mac. Wow. Like... Wersdaluv??
Oh well. One day, we'll get more love.

2. Lack of Knowlege about Linux
Among the things that I am having a hard time with are the use of the command-line, the new way of installing things, and having a hard time relating to what Linux Experts say.

3. My laptop and my peripherals don't seem to be fully supported by Linux
I can't find drivers for my laptop and my peripherals. No USB device works with my Linux OS.

4. My schedule is tough and studying more about Linux makes it tougher
I guess, solving this problem is up to me and me alone

5. Maybe, just maybe, Linux is not mature enough
I don't know...

**The Driving Forces**
1. I love the Open Source Philosophy
I do everything for what I believe in.

2. Linux is growing faster and faster
Yes, there is so much to improve with Linux but its improvement is getting faster and faster and faster...

3. I want to get rid of Windows as soon as possible!

**The Questions**
1. What do I do to get rid of Windows ASAP?

2. How soon is ASAP?

---

### Post by al1b1 on 2007-01-27
To get rid of windows is fairly easy. Just open gparted and overwrite the windows partiton with the linux file format and reboot. When to destroy windows can only be your choice but i doubt i ever will as my school uses only windows programs and i hav to be able to read their files  :(

---

### Post by ashmew2 on 2007-01-27
HI , I think you should not switch completely switch to Linux but keep a dual booting system between XP and Ubuntu because Many people consider WIndows to be the only OS around and many games which work on Windows do not work on Ubuntu (not even with emulators like Wine or Cedega).
Although there are alternatives for almost everything on Linux that runs on WIndows but sometimes it just wont work.As far as themes are concerned , u can get a LOT themes by visiting : [www.art.gnome.org](www.art.gnome.org)
For the command line , ull get used to it gradually and if u dont understand anything , please ask!! :)
For the laptop and peripherals , Everything that works in Windows SHOULD work on Ubuntu.Could you be a bit more specific in this case ?

CONCLUSION : I would recommend a dual booting system if you want to play games normally until something stable is made/released....Well those are just my ideaz..

---

### Post by r4ik on 2007-01-27
We dont live in history or future, today is where we are.
if you want to make the move i'd say: green,green,green !
There are 228,432 people willing to help you.
Sufice je pence.

Good luck !

---

### Post by Pobega on 2007-01-27
Calling Linux immature is completely untrue, Linux isn't immature; It's just harder to get things working, since all of the drivers are created by community members who want to get their hardware working. If no one with strong programming knowledge has your exact hardware, don't expect to get it working because no one will have made drivers yet(At least that's how I understand it.)

To your lack of knowledge about Linux: You'll learn. Just lurk the forums a bit and you'll pick up little things, always play around with your terminal (**Never** as root though!), and never give up on it. You'll eventually learn to live without a GUI. When I first learned the terminal I thought it would be useless, but now I've learned that using the terminal I can mass move/delete/edit things faster than I ever could on Windows.

What is your laptop hardware, and what peripherals are you using? You could always run the command *lspci*, and figure out the exact name of your hardware; Then do a forum search for threads where other people had the same problem as you. You're likely to find at minimum 2~3 threads, just search your model number (For example, my lspci tells me my wireless is Intel Corporation PRO/Wireless 3945ABG Network Connection. So I would search the forums for 3945ABG, which is the model number)

Most programs you'll find online don't have a Linux version, this is true. But most of anything you could want would be in the repositories; In your terminal run > sudo aptitude install xscreensaver-data xscreensaver-data-extrawait for those packages to download then run> xscreensaver-demoVoila, you now have tons of screensavers to choose from.

---

### Post by Tomosaur on 2007-01-27
Just out of curiosity, have you actually tried using the LiveCD? This will give you a good idea of whether your hardware works or not. Generally speaking, Linux has far, far better hardware support than even Windows. In Windows, if you plug in a new device, it's likely that it'll ask **you** to provide a driver, or, if the device is supported natively (ie 'built in' to Windows), you may find that many of the features do not work. Linux, on the other hand, tends to have hardware support built right into the kernel, rather than relying on you to find drivers (ever lost a driver CD on Windows?). If you plug in your hardware, there's a good chance it'll work right away. Some devices require a bit of fiddling to get going, particularly wireless devices, but chances are, it'll work. These free drivers are normally of a very, very high standard, with the possible exception of graphics card drivers, which tend to provide only the basic functionality. If you're not a gamer or whatever, you're unlikely to notice, but if you're expecting full 3d acceleration, you're probably going to need to download the manufacturer's own drivers. NVidia has great support for Linux users, and provides drivers specifically for Linux.

As for the command line - it depends on what distribution you're using. Ubuntu, generally speaking, has many of the GUI tools available which negate the need to touch the command line, but I personally find it much easier and faster to use the command line than clicking around everywhere. It's just a matter of preference really. It's only reasonable that it'll take you time to learn how the command line works, but there's really no way around it. You don't HAVE to use it, but you may just grow to prefer it if you take the time to learn it.

Downloading and installing software is much, much easier than on Windows. If you want to download say, a new text editor on Windows, you have to open up your browser, go to a search engine, type in 'Text editor for Windows', then search for a download or site which allows you to buy one. In Linux, you just click 'Add/Remove Programs', search for text editors, and then click the ones you wish to download. Installation is automatic from then on. Very occasionally you may need to actually search the web for a program which isn't in the repositories. This is when users tend to face problems, because they don't understand why their program isn't in .exe format. It's just the way Linux works - we don't have .exe. We have .deb, or .rpm, or .bin, or .run. All of these, with the exception of .rpm, will work on Ubuntu. rpm files can be made to work, but they're not natively supported on Ubuntu (since they're intended for Red Hat distributions, whereas Ubuntu is based on Debian (hence .deb)). These work the same way as .exe files - you just run them and follow the instructions. Other times, you may need to compile a program, and this occasionally means satisfying the dependencies of that program. This is commonly referred to as 'dependency hell', and is pretty frustrating if you're not familiar with it. You're better off sticking to .deb files, or just using the repositories. It is still much easier, and quicker, than searching around the web for programs.

So, to conclude - switch when you're ready. Download the Ubuntu .iso, burn it, and boot from it. This won't cause you to lose Windows, just select the 'Start or Install Ubuntu' option from the menu, and you get to try Ubuntu out without commiting to installing it. Note that running Ubuntu from the LiveCD is not an indication of how fast Ubuntu runs when it is installed. Running from the CD is slow, and it WILL take a little while to start up programs etc. It will give you an idea of whether your hardware is supported though, and you can try out all of the software provided, and also get a feel for the Add/Remove system. You can also fiddle around with the command line and see what's what :)

You don't even have to get rid of Windows completely. It's probably a better idea to switch gradually. Just dual-boot, and you can select between Windows or Ubuntu upon startup. This will allow you to compare the two more fully, and see which one is best for you. In the end, it's entirely up to you, though we all hope you make the switch one day :)

---

