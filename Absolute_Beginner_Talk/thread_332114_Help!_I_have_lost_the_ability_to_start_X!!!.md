---
title: "Help! I have lost the ability to start X!!!"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by blore123 on 2007-01-05
Help me!

I have been compiling and installing various new things onto Ubuntu (I have Breezy Badger and Kernel 2.6.12-9-386) - but I'm a new user and do not know what conflicts with my system and what's kosher. Consequently, when I started using online repositories, I installed a few things (can't remember what) and now on bootup the splash loads ok but only goes into runlevel 3 - startx just results in a screen full of warnings and although the OS is clearly working, I'm stuck in text mode! worse still, 'init 5' just hangs the system. What shall I do? (Tell me what you need from the system if you need more info and I'll type it on this thread for you)

---

### Post by macogw on 2007-01-05
Ubuntu doesn't use init +#, as far as I know (and what an ex-Ubuntu long-time FC user tells me).  That's a RH convention.  try
sudo /etc/init.d/gdm start

---

### Post by gunksta on 2007-01-05
Ubuntu, and Debian, both uses runlevels....at least they did before Upstart, but this may change in the future, I don't know.

Based on what you have told us, there is no way to help you, without just guessing wildly. Fortunately, you can help us -- to help you! I want you to boot your computer in Linux. When it is done trying to boot, I understand you are logged in at the command prompt.

I would like you to post the contents of .xsession-errors here on the forum. To see it from the command line use:

less .xsession-errors

There will be a lot of stuff in there. Post the first 20 lines. We'll tell you if we need more.

--andy

---

### Post by Sasa_Ivanovic on 2007-01-05
if you have ever modified file /etc/X11/xorg.conf, then return it's backed up version.

---

### Post by blore123 on 2007-01-06
thanks, I think I must have since I wanted Freeciv and it was complaining about X11 and xlib files. How do I restore these files, this OS is so new to  me that I never made any backups myself - does it make any itself?

---

### Post by ajmorris on 2007-01-06
Yes it backs up the files automatically. In the same folder where the file is located should be the same file with i tilde at the end.

E.g.
xorg.conf~

---

### Post by blore123 on 2007-01-08
Ok! Great! Now how do I restore that file (being new I do not know what linux uses for replacing a file in text-based mode) - sorry to the guy who wanted 20 lines of my error file, I'm going to post that to you soon. Oh, one more thing, how do I read the upper lines in runlevel 3 (it just scrolls downwards and chops the top off and so at present I can only really give you the bottom 20 lines :( - sorry)

---

### Post by blore123 on 2007-01-08
Ok - that's it. I do not like this one bit. I thought Linux was supposed to be *more* stable than Windows. Having found the cp -i file1 file2 command and then rebooting, ir still just sat there and refused to startx. Now I have bought a big DVD of a newer Ubuntu from Linux Format (with Fedora on the flipside) - so I'm starting again, I guess you guys can help me again as soon as I get stuck with this, but I believe bigger media *should* mean more repositories that actually work with Ubuntu.

Sorry if this is wasting your time, but I'm really going have to format that HDD now.

Thanks to all who replied.

---

### Post by confused57 on 2007-01-08
Have you tried?:
 ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

I've never had to use this, but I've seen it suggested by other posters.

---

### Post by blore123 on 2007-01-09
Thanks, I'll store that one, but now I'm using Edgy Eft Ubuntu and things are going nicely for me, so I don't need it myself at the moment.

I do really appreciate all this help though - thanks :)

---

