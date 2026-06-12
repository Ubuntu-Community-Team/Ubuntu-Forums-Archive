---
title: "How to set the resolution of the login screen?"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by NovaAesa on 2007-11-06
Hi all,

The problem that I am having is that the screen resolutions between my login screen and when I am logged in are different. I have my logged in resolution set to 1280 by 1024, but I think the login resolution is 1280 by 768 (which looks terribly ugly on my LCD).

So how do I change the resolution for my login screen to be 1280 by 1024?

ps. I did do a search on the forum, but other people only had problems where their login screen resolution was too high rather than too low.

---

### Post by ramjet_1953 on 2007-11-06
If you install start-up-manager

[COLOR="Red"]sudo apt-get install startupmanager[/COLOR]

You can then select basic screen resolutions, before any video card drivers are loaded.

This may do what you want.

Regards,
Roger 8)

---

### Post by akiratheoni on 2007-11-06
Hey, I have the same exact problem except my monitor goes up to 1680x1050. And the login screen resolution is 1280x800.

I installed the startup manager but the only resolution that appears is 1600x1200, 1280x1024, 1024x768, and 640x480. How can I change to 1680x1050?

---

### Post by ramjet_1953 on 2007-11-06
You can't, as it can only use native resolutions, as any additional video drivers are not loaded at this stage of booting.

Regards,
Roger :cool:

---

### Post by NovaAesa on 2007-11-11
Ok, I installed startupmanager and then ran it, but then ran into some problems. I set the Display resolution to 1280 by 1024, but the login screen is still at 1280 by 768 (or maybe by 800). Also, now my normal desktop resolution is also 1280 by 768. Trying to change my desktop resolution under System -> Preferences -> Screen Resolution does nothing.

What should I do?

---

### Post by Tony3286 on 2007-11-12
I don't know if this will help the Log in screen , but if its the splash screen , which comes up just prior to the login (And I've heard the wrong resolution is being entered by Gutsy install  this **MAY** work

You start with editing the splash file, first backing up the original just in case with:
sudo cp /etc/usplash.conf /etc/usplash.bak

Then edit it with:
gksu gedit /etc/usplash.conf

and change the resolution as
xres=800
yres=600

I would TRY this resolution first, You can always go back and try your correct resolution later.

Then type 
sudo dpkg-reconfigure -phigh usplash

Do it and reboot to see if there is any progress

Are you getting a splash screen PRIOR to the login? Its shows  the Ubuntu logo with an orange line going across. If thats not the problem then it may be the Xorg configuration file

---

### Post by joop905 on 2007-11-12
To fix the no boot splash I did the following

1) Change the resolution in /etc/usplash.conf to 1024x768
2) Add vga=791 to the kernel line in /boot/grub/menu.lst
3) sudo update-initramfs -u -k `uname -r`

---

### Post by joop905 on 2007-11-12
To fix the no boot splash I did the following

1) Change the resolution in /etc/usplash.conf to 1024x768

2) sudo update-initramfs -u -k `uname -r`

---

### Post by fermin on 2008-01-05
I had this same problem but i fixed it. I found more information on people with a similar problem in _[this thread]("http://ubuntuforums.org/showthread.php?t=593432")_ and found the solution _[in this other thread]("http://ubuntuforums.org/showthread.php?t=83973")_. I also posted my modified short version of the solution in the first thread.

---

