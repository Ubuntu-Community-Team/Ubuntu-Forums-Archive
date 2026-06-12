---
title: "Matrox G400 Resolution Issues Ubuntu 6.10"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by somar on 2006-12-27
I've been having some issues with my G400 Matrox card and Ubuntu 6.10. After the Ubuntu install, my only screen resolution options were 800 x 600 and 640 x 480.

I noticed similar posts on the Matrox Linux support forums, which Matrox unfortunately decided to close. :(  I tried to follow recommendations in the posts because I was having the same issues as other posters.  I  downloaded the matroxdriver_mga-x86_32- 4.4.1-installer.run script from [www.tuxx-home.at](www.tuxx-home.at) and followed the directions and recommendations on the website and on the now extinct matrox forum. After running the script, my screen appears blank and I am searching for a solution. It seems that X is not starting.


Thank you for your help,

MS

---

### Post by DSn0wMan on 2006-12-27
Did you try running this command?

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Jorge32 on 2006-12-27
> **DSn0wMan said:**
> Did you try running this command?

```
sudo dpkg-reconfigure xserver-xorg
```

try with that after installing the MGA driver, then it should works now the MGA, option, after selecting your monitor select the new resolution(s) and try with 
```
sudo /etc/init.d/gdm restart 
```
after this it should works, but be carefull because this will reboot to the user login part.
Good luck

---

### Post by somar on 2006-12-27
Thanks for your speedy reply.

> Did you try running this command?

Code:

sudo dpkg-reconfigure xserver-xorg


Yes I booted into GRUB ran Ubuntu in recovery mode.

Typed in the root pw at the prompt.

I also tried typing "startx" at the command line this made the screen go dark- rebooted.

I  typed the code you posted above in the quote and got into the Xserver window configuration.

I went through the configuration manager specifying what I thought was accurate for the graphics card.  When I get to the Resolution section none of the resolution options are checked and I don't know how to check them the options range from 
1920 x 1440 to 1280x1024. I clicked on OK to get to the next window.

After rebooting the machine I see some horizontal flashes on my screen but nothing comes up after 5 minutes.

MS

---

### Post by Jorge32 on 2006-12-27
To check them you need to select them with the arrows and click the space bar

---

### Post by somar on 2006-12-27
Hi Jorge,

If I've already run the mga script provided by tuxx-home.at will I need to run the installer again?


MS

---

### Post by Jorge32 on 2006-12-27
No, What I did was: I installed  the mga driver, and after that I tried changing the MGA (in the xserver-xorg configuration) to vesa (which I've read that worked out in the problem we had) os it accepted the new resolution but a little bit weird. So then (having the MGA driver installed) I selected again the MGA option, left everything as it was, and selected the new resolution ( in my case 1024x768 ), typed

sudo /etc/init.d/gdm restart

and entered as my user, then I selected from system>preferences>screen resolution the new resolution, closed it and it was working.

Hope this helps you!

---

### Post by somar on 2006-12-27
> try with that after installing the MGA driver, then it should works now the MGA, option, after selecting your monitor select the new resolution(s) and try with
Code:

sudo /etc/init.d/gdm restart




I selected the vesa option ( I also tried mga) in the configuration of Xserver.  No luck after the sudo /etc/init.d/gdm restart command for both cases.

On the Matrox support forum, there was mention of modifying the gdm.conf and xorg.conf files adding something like "ingoreABI" to each file.


MS

---

### Post by Jorge32 on 2006-12-27
I don't know about it  ("ignoreABI"), but what I told you worked for me, anyway I'll tell you my xserver-xorg configuration if this helps :

with these steps after entering xserver-xorg configuration :

**yes , mga, your video card (in your case I think it should appears something as: Matrox Graphics, Inc. MGA G400 AGP), ok**, PCI:1:0:0, ok, no, no, Your keyboard configuration, xorg, ok, pc105 (or your case), ok, ok, ok , lv3:ralt_switch , ok, yes, ok, ok, yes, yes, your monitor model, **then select the resolutions you wish and ok**, ok, advanced, your monitor ranges (usually leave them the way they are), yes, 24 (or the one you're looking for, ok, and that's all.

In bold the ones I think will help you, then
```
sudo /etc/init.d/gdm restart
```

then enter and go to screen resolution.

This information is the one of my configuration, some things could differ from yours, basically try looking at the ones refering video ( like the bold ones)

Good luck!

---

### Post by somar on 2006-12-27
Thanks again Jorge.

The only discrepancy I see is with the name of the card.  I don't have > ...Matrox Graphics, Inc. MGA G400 AGP) listed in the configuration. Everything else is the same.

Just to confirm, I ran the installer matroxdriver_mga-x86_32- 4.4.1-installer.run again, however this time I noticed an error:

```

./install.sh: line 122: g++: comand not found
ldd: ./confapp.bin: No such file or directory
Currently installed driver is the same as the installer file
X server driver not installed.

Messages are being logged in file /tmp/make.log

Compiling mtx.ko... done.

Currently installed kernel module is the same as the installer file.
Kernel module not installed.
```



Maybe the driver is not being installed correctly?

MS

---

### Post by Jorge32 on 2006-12-27
Maybe it isn't installed correctly,  look this is the thread I used when I solved my problem, maybe you could find a solution here.
[http://ubuntuforums.org/showthread.php?t=234078&page=2](http://ubuntuforums.org/showthread.php?t=234078&page=2), try with the second link in that thread, If I'm not mistaken it is there.
Good luck!

---

### Post by somar on 2006-12-28
Jorge,


Thanks for the link. After many attempts at what appeared to be a promising solution,  I'm giving up on the G400 configuration.

I've been working on my problem for 4 weeks now and I'm becoming frustrated with my first excursion into troubleshooting Linux.  I really don't want this to be the case and I am a very patient individual when it comes to problem solving.

Being a Linux noob, the endeavor was not an entirely futile as I learned how to:

mount a USB thumb drive from the command line
use VIM and Nano to edit files
use GRUB to boot into the command line
use the Knoppix and Ubuntu live CDs
run the Xserver configuration manager and configure settings
restart X and the GDM


However, it's time to move on to other options. 

There's a linux group that does install-fests in my area and I'm thinking of going to them for help.  I'm also considering buying an Ubuntu compatible graphics card to truly resolve the issue.

I appreciate all the help and guidance you've provided,

MS

---

### Post by euphro on 2007-01-18
I've had the same problem with a Matrox G400 card.  I solved my problem with the advice [here]("https://launchpad.net/ubuntu/+source/xserver-xorg-video-mga/+bug/58721"), in particular the forced installation of pjssilva's version of the Debian testing [xserver-xorg-video-mga_1.4.2.dfsg.1-1_i386.deb]("http://www.ime.usp.br/~pjssilva/xserver-xorg-video-mga_1.4.2.dfsg.1-1_i386.deb") package. via "$ sudo dpkg -i --force overwrite xserver-xorg-video-mga_1.4.2.dfsg.1-1_i386.deb".

I've found the same problem with Feisty (Herd 2) and have solved it with the fix above.

---

