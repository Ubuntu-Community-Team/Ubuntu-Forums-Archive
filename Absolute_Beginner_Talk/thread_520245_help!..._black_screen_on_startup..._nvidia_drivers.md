---
title: "help!... black screen on startup... nvidia drivers"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by papermoon on 2007-08-07
well, stupid me went on "enable desktop effects". it told me i needed to install nvidia drivers. OK no problem. WHATS THE WORST THAT COULD HAPPEN?... well when i reboot i get a black screen right after the ubuntu logo.... and now i have no access to ubuntu :(
help?

---

### Post by overdrank on 2007-08-08
> **papermoon said:**
> well, stupid me went on "enable desktop effects". it told me i needed to install nvidia drivers. OK no problem. WHATS THE WORST THAT COULD HAPPEN?... well when i reboot i get a black screen right after the ubuntu logo.... and now i have no access to ubuntu :(
help?

HI using the keys all at the same time ctrl,alt,F1 and this will bring you to the terminal then login. Then use the command 
```
sudo dpkg-reconfigure -phigh xserver-xorg 
```
Answer the question and hopefully this will get you to the desktop, :KS

---

### Post by papermoon on 2007-08-08
i used all 3 keys at the same time and nothing happened... :|

---

### Post by overdrank on 2007-08-08
> **papermoon said:**
> i used all 3 keys at the same time and nothing happened... :|

Ok try those keys just after the grub loads and hopefully this will bring you to the terminal.

---

### Post by papermoon on 2007-08-08
i did it just after grub loaded and a DOS - like terminal appeared but then as soon as everything finished loading, it just switched to a black screen like before :(

---

### Post by overdrank on 2007-08-08
> **papermoon said:**
> i did it just after grub loaded and a DOS - like terminal appeared but then as soon as everything finished loading, it just switched to a black screen like before :(

Ok have you tried to boot into recovery mode and try to configure there?

---

### Post by papermoon on 2007-08-08
nope but ill try that now and get back to you

---

### Post by papermoon on 2007-08-08
ok i did it in recovery mode...
when it asked the driver to use i slected "nv" (i read that that was the fix in another thread on the forum) and switched the resolution to 1280 x 1024
BUT it didnt send me to the desktop... it just stays there in the dos like screen... O_O

---

### Post by igknighted on 2007-08-08
> **papermoon said:**
> ok i did it in recovery mode...
when it asked the driver to use i slected "nv" (i read that that was the fix in another thread on the forum) and switched the resolution to 1280 x 1024
BUT it didnt send me to the desktop... it just stays there in the dos like screen... O_O

You need to reboot and boot normally, recovery mode is just the terminal

EDIT: Selecting 'nv' is not a fix, it is reverting to the old 2d drivers.  To get the 3d drivers working, can you tell use what nvidia graphics card you have and which driver you used (10.XXX or 96XX or 7XXX).

---

### Post by overdrank on 2007-08-08
> **papermoon said:**
> ok i did it in recovery mode...
when it asked the driver to use i slected "nv" (i read that that was the fix in another thread on the forum) and switched the resolution to 1280 x 1024
BUT it didnt send me to the desktop... it just stays there in the dos like screen... O_O

After the configuration you will need to reboot
```
sudo shutdown -r now
```

---

### Post by igknighted on 2007-08-08
> **overdrank said:**
> After the configuration you will need to reboot
```
sudo shutdown -r now
```

recovery mode you are always root, no need for sudo.  Plus I prefer the simpler "reboot" command... its more logical, especially for new users ;).

---

### Post by overdrank on 2007-08-08
> **igknighted said:**
> recovery mode you are always root, no need for sudo.  Plus I prefer the simpler "reboot" command... its more logical, especially for new users ;).

Thanks I will remember that! :popcorn:

---

### Post by papermoon on 2007-08-08
ok ill do that now
i have a geforece fx 5500 and i used the driver that downloaded automatically when i tried to enable the "desktop effects" 

what if i want to play games like counter strike using wine? would it work or would i have the same driver problem?

---

### Post by overdrank on 2007-08-08
> **papermoon said:**
> ok ill do that now
i have a geforece fx 5500 and i used the driver that downloaded automatically when i tried to enable the "desktop effects" 

what if i want to play games like counter strike using wine? would it work or would i have the same driver problem?

HI that I cannot answer as I don't use wine or play game but you can search for you card in the forums and maybe find some help. :(

---

### Post by igknighted on 2007-08-08
> **papermoon said:**
> ok ill do that now
i have a geforece fx 5500 and i used the driver that downloaded automatically when i tried to enable the "desktop effects" 

what if i want to play games like counter strike using wine? would it work or would i have the same driver problem?

You need to use the official nvidia driver (which is what "desktop effects" tried to download in the background).  Assuming you got booted up OK, go into synaptic (or adept if you use KDE) and search for the nvidia-glx package.  Look at the details for each and find the one that is a 96XX series driver (the 10.XXX drivers have some rather serious bugs) and install that.  Then go to a terminal and run that dpkg-reconfigure command again, this time selecting nvidia and not nv.  Then reboot and hopefully the drivers work properly.  If they do not, fix it the same way as before (going back to nv) and we'll see what else might be the problem.

---

### Post by ronny_d on 2007-08-08
True: 'recovery mode' is the 'root' space, no sudo..., but: you cannot do much in that root space... but... IF, just if..., you could do some in that root space... then... damaging / handicapping / disabling / misconfiguring... -and so on- your Ubuntu system... is a severe and "realistic" risk. 


Remember: in Ubuntu 'sudo' is not for nothing there instead of 'root' / 'su' (super user / single user, but single user can be misleading as a term... so remember 'su' is ROOT!). 

sudo means 'superuser do' and is there.... to protect your 'root files' (the base of your entire well-functioning of your Ubuntu) from being harmed.  

sudo is especially for Ubuntu only 


If you now still want to "mess" in 'root'... 'su'... you i suppose have been warned now. Or maybe it is that you do not fully grasp then the *nix file system organization and WHY Ubuntu has 'sudo'... 


Just always anywhere in the system use 'sudo' in Ubuntu!

---

### Post by papermoon on 2007-08-08
okay i did it and it's okay, the desktop loaded, the only problem now is that it's 1024x 768 and i cant change it to a higher value... ill install the drivers you specified


1 other question, i noticed in the hard drive, ubuntu stores its files very differently to windows.... which folder is the equivilant to "program files" ,,,, if there is such a folder...

---

### Post by igknighted on 2007-08-08
> **ronny_d said:**
> True: 'recovery mode' is the 'root' space, no sudo..., but: you cannot do much in that root space... but... IF, just if..., you could do some in that root space... then... damaging / handicapping / disabling / misconfiguring... -and so on- your Ubuntu system... is a severe and "realistic" risk. 


Remember: in Ubuntu 'sudo' is not for nothing there instead of 'root' / 'su' (super user / single user, but single user can be misleading as a term... so remember 'su' is ROOT!). 

sudo means 'superuser do' and is there.... to protect your 'root files' (the base of your entire well-functioning of your Ubuntu) from being harmed.  

sudo is especially for Ubuntu only 


If you now still want to "mess" in 'root'... 'su'... you i suppose have been warned now. Or maybe it is that you do not fully grasp then the *nix file system organization and WHY Ubuntu has 'sudo'... 


Just always anywhere in the system use 'sudo' in Ubuntu!

Not sure how this is relevent to the thread... good advice though. The only reason the OP used recovery mode is because the terminal was not accessible with a normal boot due to a driver issue.  Also, sudo is in every distro.  You just need to add yourself to the sudoers file, which most distros do not do by default.  There are advantages and disadvantages to sudo, personally I prefer to use "su -" to work as a true root, but it's personal preference.  Theres a big thread on this in the Cafe at the moment if you want to throw your $.02 in there.

---

### Post by igknighted on 2007-08-08
> **papermoon said:**
> okay i did it and it's okay, the desktop loaded, the only problem now is that it's 1024x 768 and i cant change it to a higher value... ill install the drivers you specified


1 other question, i noticed in the hard drive, ubuntu stores its files very differently to windows.... which folder is the equivilant to "program files" ,,,, if there is such a folder...

Yes, it is very different.  There is no equivelent to "program files".  The actual program (binaries) are typically all in /usr/bin.  Libraries are usually arranged by program in /usr/lib.  Config files are typically in /etc for system wide configurations and in your home folder (as hidden files) for user specific settings.

I would hold off on changing anything relating to the screen resolution yet, because the nvidia drivers might (a) fix it for you, or (b) reset your changes if you do fix it and you'd have to change it again.

---

### Post by ronny_d on 2007-08-08
> **igknighted said:**
> Not sure how this is relevent to the thread... good advice though. The only reason the OP used recovery mode is because the terminal was not accessible with a normal boot due to a driver issue.  Also, sudo is in every distro.  You just need to add yourself to the sudoers file, which most distros do not do by default.  There are advantages and disadvantages to sudo, personally I prefer to use "su -" to work as a true root, but it's personal preference.  Theres a big thread on this in the Cafe at the moment if you want to throw your $.02 in there.

The terminal...? The graphical user interface / GUI was inaccessible due to the nvidia driver(s) installation: just a black screen only,  I then performed "the ancient" command startx ... though that was not what i meant (because in Ubuntu one would not need to know about such commandline issues since there was sudo, wasn't it?) to at least login and did pwd for to see any present working directory where i was in, although in Ubuntu commandline would have been no issue at all... And where in the system was i then? I reckoned the nvidia did not work. With sudo i changed it all back to the "original state", edited the file via gksudo (o yeah?), because if i remember well, i saw 'nothing had changed' what i had changed... and it all made me feel rather odd but of course. Had i entered the root desktop and "cd-ed" myself to my /home/myname and gave a startx?? Very funny. Understand what i mean with being in super user space in Ubuntu... Look at it for a while... Now: does nvidia work or doesn't it? I went to install Ubuntu on a whole different computer and without nvidia, left the other computer where i had "this nvidia adventure" alone though. Now i remember, when i installed the nvidia drivers back then and so forth, i had not yet made my 'themes' at the "ordinary" user desktop as i have now... in this (without nvidia) other installation (is this some hint?), well: what i want to say with that is... that "back then" when i cd-ed myself to /home/myname from root recovery mode black screen environment and made a startx... from, i checked with pwd, /home/myname and at least got the graphical interface, i know by now that i was not (!) where i 'thought' i was but i did not know by then... and anyway i forgot about nvidia until now because nvidia was not such a priority to me, but i am interested how the "nvidia black screen" adventure here at this thread will move on using root..., knowing how the root cd-ing to /home/myname (whatever name for your home) is functioning. That is why i say in Ubuntu 'root' / 'su' is not meant, but only sudo with apt-get and synaptic... (Or?) So i wonder about 'nvidia'... if it is the 'right' driver at all. Therefore once more i am however curious how this thread works out...

---

### Post by papermoon on 2007-08-08
> **igknighted said:**
> You need to use the official nvidia driver (which is what "desktop effects" tried to download in the background).  Assuming you got booted up OK, go into synaptic (or adept if you use KDE) and search for the nvidia-glx package.  Look at the details for each and find the one that is a 96XX series driver (the 10.XXX drivers have some rather serious bugs) and install that.  Then go to a terminal and run that dpkg-reconfigure command again, this time selecting nvidia and not nv.  Then reboot and hopefully the drivers work properly.  If they do not, fix it the same way as before (going back to nv) and we'll see what else might be the problem.

i did what you said and that give the same black screen error...

---

### Post by overdrank on 2007-08-08
> **papermoon said:**
> i did what you said and that give the same black screen error...

Hi and sorry to here. Well you at least know how to correct the issue. And have you consider looking at  comp-fusion and search if there is problems that can be solved on that graphics card?

---

### Post by papermoon on 2007-08-08
so this means that i won't be able to use 3-D apps with ubuntu on my pc?..... sigh....

---

### Post by overdrank on 2007-08-08
> **papermoon said:**
> so this means that i won't be able to use 3-D apps with ubuntu on my pc?..... sigh....

Well I cannot say but this thread does look promising.
[http://ubuntuforums.org/showthread.php?t=160247&highlight=geforece+fx+5500](http://ubuntuforums.org/showthread.php?t=160247&highlight=geforece+fx+5500)

Good luck!:popcorn:

---

### Post by r4ik on 2007-08-08
Long shot,
If you have an Intel integrated try,

[http://doc.gwos.org/index.php/Nvidia_Intel_Integrated](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated)

Good luck.

---

### Post by papermoon on 2007-08-08
so which drivers were loaded by default? before i clicked on the enable desktop effects? because with those drivers i was able to set the resolution to 1280 x 1024, now the max i can go to is 1024 x 768

---

### Post by overdrank on 2007-08-08
> **papermoon said:**
> so which drivers were loaded by default? before i clicked on the enable desktop effects? because with those drivers i was able to set the resolution to 1280 x 1024, now the max i can go to is 1024 x 768

You can check you xorg and see which driver is being used
```
gksudo gedit /etc/X11/xorg.conf
```
YOu can view the driver being used in the device section and then you can also add the resolution you want and here is a link to do that.
[http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution](http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution)
Good luck!

---

