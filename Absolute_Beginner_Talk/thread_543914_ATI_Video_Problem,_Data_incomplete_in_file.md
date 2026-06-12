---
title: "ATI Video Problem, Data incomplete in file"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by TALLandNcharge on 2007-09-05
I've been trying to install 7.04 today and I just keep running into problems.  I'm working on my notebook which has a ATI X1400 card in it.  I've been following the steps of the stick "ATI X**** Cards".  I got to step 7 (sudo aticonfig --initial) and it gave me and error.  It says;
Data incomplete in file /etc/X11/xorg.conf
                      At least one Device section is required.
Data incomplete in file /etc/X11/xorg.conf
                      At least one Device section is required.
aticonfig: Parsing the configuration file failed.
The above error message are reproted from XFree86 and may assist you in diagnosing the problem with your configuration input file.  Try use -f option to generate a new configuration file.

Please, I am a Linux beginner and I have no idea what in the world this thing is talking about.

---

### Post by SOULRiDER on 2007-09-05
Theres probably a problem in the xorg config. Reconfigure it by typing:
```
sudo dpkg-reconfigure xserver-xorg
```

If you have any questions just ask, dont worry about it ;)

---

### Post by TALLandNcharge on 2007-09-05
> **SOULRiDER said:**
> Theres probably a problem in the xorg config. Reconfigure it by typing:
```
sudo dpkg-reconfigure xserver-xorg
```

If you have any questions just ask, dont worry about it ;)

Alright, I did that went through alot of stuff and not sure what I chose.  But when I got to the resolutions, I chose the 1440 x 900 and everything seems to be working now.  How do I know if I chose anything wrong during that whole setup of the xorg config?

---

### Post by WebSiteGuru on 2007-09-05
It will come up with the display error. I know I did it about a dozen of time before I got my video card working correctly.

---

### Post by SOULRiDER on 2007-09-05
If somethign went wrong youll probably notice it. In any case, you can reconfigure xorg again so dont worry about it.

---

### Post by MWRMWR on 2008-02-14
> **SOULRiDER said:**
> Theres probably a problem in the xorg config. Reconfigure it by typing:
```
sudo dpkg-reconfigure xserver-xorg
```

If you have any questions just ask, dont worry about it ;)
Hi, I just re-built my PC with Edubuntu (latest release as of Dec 2007),
I got to this stage wherein I'm stuck on 800x600 and am struggling to install the latest linux ATI for my X1800 XT card
 {Clever the way the OK and Cancel buttons have to be guessed at as they are just below bottom of that screen size  - good testing ATI !).

Any way, I go this far and followed the *sudo dpkg-reconfigure xserver-xorg* dialogue.
This went on in the usual obscure *nix way until it hit a screen headed *Configuring xserver-xorg* and banging on about the choice of pc101/2/4/5 or macintosh keys.
Well, I can go through the options, but what I CAN'T cope with is the fact that there is an OK box at the bottom but no way  (*enter* or *click* say) to proceed it just hits the buffers. Game Over
[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

[COLOR="Sienna"]**HELP ME Please for this immediate problem**[/COLOR]
...I can't even understand if this panel is supposed to be some kind of information or
an editing window; it seems to be an in-terminal window process, but I cannot easily revert to the terminal command line - except by using reset command from menu - and then I'm left with the hanging process.

[Also, any outline on WHY this ridiculous procedure has to be followed
 - can't ATI have put in something to reconfigure  my xserver]

Mark

---

### Post by MWRMWR on 2008-02-14
OK, somehow the ESCape key helps move on.

Phew!  Still no idea what's going on. So, Back to the aticonfig --initial problem

maybe I can edit the wretched config file with some settings I find by Googling about.

> mark@xUbuntu:~$ sudo aticonfig --initial -f
Data incomplete in file /etc/X11/xorg.conf
	Device section "Configured Video Device" must have a Driver line.
Data incomplete in file /etc/X11/xorg.conf
	Undefined Device "(null)" referenced by Screen "Default Screen".
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Data incomplete in file /etc/X11/xorg.conf
	Device section "Configured Video Device" must have a Driver line.
Data incomplete in file /etc/X11/xorg.conf
	Undefined Device "(null)" referenced by Screen "Default Screen".
Segmentation fault (core dumped)

I'll be back when I make some progress.

---

### Post by 9000 on 2008-05-06
any progress?

---

