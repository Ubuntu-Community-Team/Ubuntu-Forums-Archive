---
title: "Installing ubuntu server with Fluxbox GUI."
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by martinmanzana on 2006-08-09
I posted an earlier thread asking if ubuntu would run on a low resource laptop computer:

[Does ubunto work on a box with low resources?]("http://ubuntuforums.org/showthread.php?t=232935")

Someone suggested the best way to install it, would be to install a server version of Ubuntu and later try to install a low resource consumption GUI. They suggested Blackbox, Fluxbox and Icewm. I looked them up and decided to give fluxbox a try. Since I am a complete newbie to Linux, I was hoping someone would guide me throught the process.

I got an xubuntu desktop iso image downloaded and burned, but it never loaded on the laptop due to low resorces. I was wondering if I can use that since I already got it on a cd. Also My laptop does not have access to internet.

So, if anyone is up to it. Lets try to get ubuntu installed and running in this good for nothing piece of trash laptop :D . (It has given me a great headache](*,) . But I like to fool around with these things, its just fun!)

Thanks

---

### Post by GuitarHero on 2006-08-09
You are going to want to download and install the ubuntu server iso, not the xubuntu one.  Once thats installed you just need to install fluxbox on to the server install.

---

### Post by martinmanzana on 2006-08-09
Lets say I download the ubuntu server iso, burn it on a cdr, run it on my laptop. Will it install ubuntu correctly with 64mb of ram and no access to internet? I just don't understand the "server" part. Thanks

---

### Post by GuitarHero on 2006-08-09
The server part means theres no gui, which for you may be difficult.  Basically it installs and runs from the terminal.  Im not clear on how to install fluxbox so I cant give you detailed instructions.  I would say get on the #ubuntu irc channel on freenode network, search for a thread with a similiar problem, or wait here for someone with more server experiance.  Because its text based it should install on your machine with no problem.

---

### Post by CREEPING DEATH on 2006-08-10
I'd install Xubuntu using the 'alternate CD'
Also check out [Fluxbox]("https://help.ubuntu.com/community/Fluxbox"), [IceWM]("https://help.ubuntu.com/community/IceWM"), and [Openbox]("https://help.ubuntu.com/community/Openbox").  You seem to have the disk space for a full installation, DSL is designed for smaller hard drives (or no HD), but your RAM is lacking.  Good luck!

CD

---

### Post by bukwirm on 2006-08-10
You can install the server version from the Xubuntu CD - just select "server" from the first menu that comes up.

After it installs, you will have a *very* basic ubuntu installation - no gui at all, just the text based interface.

Type 'sudo aptitude' to open aptitude (a text-based package manager)

Search for the package "xserver-xorg" (by pressing the '/' key and typing the name) and install it.

Install debian-menu (package called 'menu')

Install fluxbox.

Install xterm.

You may want to install a display manager (xdm) to control who can log in to the desktop.

Install anything else that you want using aptitude.

There is a HOWTO about minimal installations somewhere on the wiki, I think. There is also one about fluxbox here: [https://help.ubuntu.com/community/Fluxbox]("https://help.ubuntu.com/community/Fluxbox")

---

### Post by Neobuntu on 2006-08-10
Just a few comments:

Installing Fluxbox is not a newbie thing (yet) with Ubuntu. It's at least not as easy as (K)(X)(Ed)ubuntu. Why? Because it not built out yet; like the others. The work has not been done. Still if you understand this, go for it. You're getting some good suggestions here. Fubuntu lives! Soon anyway.

Xubuntu likes at least 128MB RAM. I see you figured that out.

Having an ubuntu server (with what ever DM) has many advantages and in a word, is the way to go.

Oh, about your notebook. It's really good to keep these out of the landfill but it holds true, there's no substitute for better hardware. If you understand this too, then go for it. Bump up the RAM and if possible (without spending much) and you will see the biggest difference. A faster hard drive with also speed things along. With SOME old laptops, these things may be enough to make it like new, depending on your needs. Don't plan on watching hi quality video on old models.

DSL (Linux distribution) is perhaps the easiest way to go and there, you'll want to (eventualy) install it to hard drive (Frugal install) and program GRUB (menu.lst) to load it into RAM (with >= 64MB I think) with the command called "toram". It can work as if live from a CD but MUCH faster from the hard drive AND you can set it to save all your files, like a (regular) hard drive install. PLUS! You can update the new version with one file (using a wizard.) Do not do a Debian like install (of DSL), you might as well do Debian (or ubuntu) if you do that(basically).

Perhaps an old (unsuported,) (gasp) Windows 98SE; tweaked install and then dual booted with "fubuntu" (I call it) and/or DSL would be the best of all worlds on that box. Well, XP will run in 64MB RAM but you really have to tweak it and then there's dealing with their crap (which SO FAR can also be done.) :) 

What ever you do, don't pay any more for Windows!

You main limits are RAM and HD size and SPEED. By the way DSL is FAST that way, even on old systems. BUT it's different, and many like Windows 98(SE) better than DSL. With Kubuntu, I think most people like it better.

Did this help you?

---

### Post by Titus A Duxass on 2006-08-10
Do a server install as previously stated, press F6 when the options window appear after booting from CD. F6 will give more details about what is allowed, simply type "server" (without quotes) at the end of the line and press enter.

Follow the install procedure as usual.
Open /etc/apt/sources.list with your preferred editor.
Enable the universe repositories by removing the # from the beginning of lines that look like URLs.
aptitude update
aptitude upgrade
aptitude install x-window-system-core gdm icewm menu mozilla-firefox xterm 

That will give you IceWM, you can change to Xfce, or Blackbox by installing those as well.

---

### Post by Neobuntu on 2006-08-10
I also noted some cool menu and config editors, GRAPHICAL ones for icewm. But I haven't played with them (much.)

It wouldn't be a big deal to have both fluxbox and icewm both, on old systems. 

I like Fluxbox best but it might (for me) depend on the easy Kubuntu-like GUI helper programs, each has newly available. I want speed, and I feel a GUI can facilitate this.

---

### Post by DaBruGo on 2006-08-11
Hi,
 
I don't know if this helps, but I posted an article in here ( [http://www.ubuntuforums.org/showpost.php?p=903914&postcount=53](http://www.ubuntuforums.org/showpost.php?p=903914&postcount=53) ) about doing a server install (with Breezy 5.10) running fluxbox as the GUI on a 1gb USB memory stick.
 
After the initial server install, I made all the software repositories available by editing the sources.list file (In Breezy, I edited it with sudo vim /etc/apt/sources.list) then I went on the loading rampage (grin)
 
That's pretty much the steps I used to get it going. Maybe some of that info will help you out.
 
 
DAVE

---

### Post by Neobuntu on 2006-08-12
You might use Slypheed (I think sp?) for small email. 

Wait? Jusy use Internet email instead. See gmail.

---

### Post by bodhi.zazen on 2006-08-17
Fluxbox is fine for newbies.

---

### Post by kerry_s on 2006-08-17
If you don't have no internet and a computer has low resources, you should try DSL linux. It's only 50mb to download and all the work is done you just pop the cd in and install. [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by bodhi.zazen on 2006-08-17
Or Puppy

---

