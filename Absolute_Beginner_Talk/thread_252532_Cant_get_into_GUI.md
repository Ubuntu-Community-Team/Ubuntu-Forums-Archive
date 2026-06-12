---
title: "Cant get into GUI"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by dolphinsonar on 2006-09-06
So, i recently installed a package called "Gnome Audio" and it asked if I would like to remove some files, and I blindly clicked yes without reading.  I restarted my computer and nothing came up but the prompt that I normally get when I am using terminal.  The little

username@computername:~$

I got scared, but then remembered my ubuntu live cd, which if you are having the same problem and reading this, KUDOS for remembering it also.  Maybe you are on another computer, anyway, I went to [http://psychocats.net/ubuntu/]("http://psychocats.net/ubuntu/") and there was my problem on the homepage.  I will copy it so you can use it to, if you get locked out of your graphical user interface, or it is gone:

Its called " no graphical login ":
[URL="http://psychocats.net/ubuntu/nox"]
http://psychocats.net/ubuntu/nox[/URL]

Troubleshooting X

Sometimes new users, expecting a graphical environment after installing Ubuntu, end up at a black screen with some white text that has a login prompt. When they log in, they see this: username@ubuntu:~$

I haven't experienced this myself, but I've seen it happen to other new users, either because they accidentally did a server install... or Ubuntu just did something funky.

Do you have a graphical environment installed?
The first step requires you to have a software repository. In most cases, if you're connected to the internet, the commands given will use your internet connection. If you don't have an internet connection but do have the Ubuntu Alternate Installer CD, insert it in your drive and type

sudo apt-cdrom add

This will add the CD as a software package source since you can't get packages from the internet.

To make sure you have a graphical environment installed:

sudo aptitude update
sudo aptitude install ubuntu-desktop

If you didn't already have it installed, you'll notice Ubuntu downloading and installing a whole bunch of packages, either from the internet or from your CD.

If you did have it installed, you'll simply be told ubuntu-desktop is already the newest version.

Run the graphical environment
Now that we have it installed, let's use it:

sudo /etc/init.d/gdm start

This should get you to a graphical login screen. If it says it's starting the GNOME Display Manager but after ten seconds or so... it doesn't actually appear to start, try pressing Control-Alt-F7, which should get you to the graphical login screen.

You have a graphical environment, but it won't show the way I want it to
Well, what if you get a graphical environment you can't see? It's a black screen but your monitor's working, or you get that the monitor signal is out of range, or the screen resolution is just too low for your tastes.

Well, then press Control-Alt-F1 and try this:

sudo dpkg-reconfigure xserver-xorg

This will pop up a text-based graphical "wizard" that will ask you questions about your keyboard, your mouse, your graphics card, and your monitor. Answer the questions as best you can. If you don't know the answer to a question, just go with the default and press Enter.

When you're done, press Control-Alt-F7 to get back to graphical mode and then Control-Alt-Backspace to reset the X server (so your changes can take effect).

Next steps
In a lot of cases, these steps will get you all straightened out. If not (for example, if you are still unable to reach your optimum screen resolution), look here for other possible solutions.

Other variations
If you're using Kubuntu, it's the same deal--just replace ubuntu-desktop with kubuntu-desktop and replace sudo /etc/init.d/gdm start with sudo /etc/init.d/kdm start

If you're using Xubuntu, it's the same deal--just replace ubuntu-desktop with xubuntu-desktop. sudo /etc/init.d/gdm start will stay as is.

---

### Post by fk4n on 2006-09-23
life saver!!!:-({|=

---

