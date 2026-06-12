---
title: "Problems with X"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by Zeikcied on 2006-10-25
I'm still rather new to the whole Linux thing, and I have a few questions (I have Kubuntu).

I downloaded the NVIDIA drivers (nvidia-glx), but I'm not sure how to use them.  I tried the command "sudo nvidia-glx-configure enable" but that ended up causing big problems with X.  (X said that the configuration was changed, and that if I thought it was wrong, to do a command that would update the md5 checksum, which I did.  After a reboot, X refused to start.  I figured out how to automatically reconfigure the config file for X, though.)  How should I go about enabling the NVIDIA drivers?  Is it safe to use that command again?

I have another question.  When I go to system settings, and go to the Display area, it gives the usual info.  The resolution and the refresh rate.  The refresh rate is set at 60Hz.  Though, in Windows XP, my monitor tends to like it if the refresh rate is set to 85Hz, or else it makes a loud screeching noise.  But, I can't change the refresh rate at this resolution (1024x768).  I was hoping the NVIDIA drivers would enable more refresh rates, but seeing as how I'm having trouble enabling those, I don't know what to do. :(

Oh, one other minor question.  Are there any GUI frontends for WINE that can be installed using Adept?  I can't find any.

---

### Post by podunk on 2006-10-25
The closest thing to a GUI that *I* know of for wine is the winecfg. I read something about 
winetools 
[http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/)
which is a graphical installer for windows programs under wine. But to me it sounds sort of buggy, and I don't have enough knowledge to cure bugs yet so I passed.

I followed the guide here to install my drivers and had no problems at all:
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

---

### Post by Dr. Nick on 2006-10-25
[Here]("http://www.geocities.com/aebcoat/xorgresproblems.html#When_nvidia-glx-config_enable_fails") is a link I made that may help some.

If the desired refresh rate isnt available then you need to edit xorg.conf or run the configure script 
[COLOR=#0000DF][B]sudo dpkg-reconfigure xserver-xorg

[/B][/COLOR][COLOR=#0000DF][COLOR=#000000]You can usually safely accept the defaults until[/COLOR][/COLOR][COLOR=#0000DF]** **[/COLOR][COLOR=#0000DF][COLOR=#000000]you come to the monitor configuration select[/COLOR][/COLOR][COLOR=#0000DF]**[COLOR=#000000] [/COLOR]**[/COLOR]**"medium"** not "simple"

You dont need to use the script to activate the nvidia drivers, you can do it manually in xorg.conf as shown in the link.
[COLOR=#0000DF][B]
[/B][/COLOR]

---

### Post by Zeikcied on 2006-10-25
Thanks for the responses.

I actually figured out the NVIDIA thing and the refresh rate problem myself.  I don't know what went wrong the first time, but enabling the NVIDIA drivers worked this time.  And I had to configure my monitor (it was detected as a generic) in order to get the correct refresh rate.

I must say that this is quite a smooth experience, despite a few problems here and there.  It's still better than my previous experiences with Red Hat 9 and Mandrake 9.2 years ago.

---

### Post by Zeikcied on 2006-10-26
Ok, one more thing.  I don't know if it is supposed to be this way, but every time I start X, it defaults back to the 60Hz refresh rate, even though I keep setting it to 85Hz (in administrator mode).  Is it supposed to do that, or is it a bug of some kind?  How do I make it stay at 85Hz?

---

### Post by Dr. Nick on 2006-10-26
Shouldnt do that, You can adjust the refresh rate in the file /etc/X11/xorg.conf 

Not exactly sure how exactly to do it off the top of my head though.

I went into that file and removed all resolutions i didnt want to force it to always pick the one I do want

---

