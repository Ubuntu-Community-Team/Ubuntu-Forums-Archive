---
title: "Ubuntu 6.10 forces me to use 1920x1440 @ 70"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by sc0undrel on 2006-10-26
[SIZE="4"]
First off, sorry for using such a big font, but I can't see it otherwise, without using a magnifying glass. No, my eyes are in excellent condition. It's just that every letter on the screen is twice as tiny as a flea.

Okay, when I first boot up Ubuntu LiveCD, this is what I see:
(I did NOT use a thumbnail, just to show you the pain I feel)[/SIZE]


[[IMG]http://img260.imageshack.us/img260/8316/problemscreensizeeu5.th.jpg[/IMG]](http://img260.imageshack.us/my.php?image=problemscreensizeeu5.jpg)



[SIZE="4"]1920x1440 @ 70Hz, This is unacceptable. How I'm supposed to install if it forces me to look at so small letters and uses a refresh so low that makes my eyes bleed?
And I can't change it, when I try to change it, the system locks up and I have to reboot. When I edit the xorg.conf file, then restart X, it makes no difference, the system still crashes.

The "sudo dpkg-reconfigure xserver-xorg" command is also no good, the system crashes, when I try to change my resolution to a more REASONABLE one.

When I install WinXP, it doesn't show off by setting the resolution sooooo high (and the refresh rate so low), that the first impression alone is as horrifying as hell. Why can't Ubuntu treat me so well? I really wanna use Linux, but can't even get the GUI working the way I would like it to work. =\

Help needed!!1!11oneoneeleven[/SIZE]

---

### Post by Henry Rayker on 2006-10-26
Well, a couple of pointers...

First, posting like this to make everyone "experience what you feel" is not only rude, but a great way to piss off the people you are asking for help. Don't punch the gift horse in the mouth. The text isn't so bad, but when I have to scroll the image halfway to the moon to read the text, it's getting ridiculous.

Secondly, this is probably a hardware issue. We'll need some information on your system. Video card and monitor should help out.

Third, Windows does the opposite for me...it always starts out with 600x800 at very most...

---

### Post by John.Michael.Kane on 2006-10-26
Have you bothered to install the OS? you can't make the screen adjustment you  need using the live cd.


And your image has been thumb nailed so others can just click on it to see what you mean.

---

### Post by sc0undrel on 2006-10-26
> **Henry Rayker]
First, posting like this to make everyone "experience what you feel" is not only rude, but a great way to piss off the people you are asking for help. Don't punch the gift horse in the mouth. The text isn't so bad, but when I have to scroll the image halfway to the moon to read the text, it's getting ridiculous.[/QUOTE]

I'm very sorry about that, I really didn't want to be rude in the first place, but it just made me so angry that with almost every Linux distro I try, year after year, even with different monitors, it's just so devastating to see this problem over and over and over again.

[QUOTE=Henry Rayker]
Secondly, this is probably a hardware issue. We'll need some information on your system. Video card and monitor should help out.[/QUOTE]

*sigh* ... please take a look at my signature, it's all there. =)
Graphics card: ATi Radeon X1900XTX
Monitor: Viewsonic P227F CRT 21"

[QUOTE=Henry Rayker]
Third, Windows does the opposite for me...it always starts out with 600x800 at very most...[/QUOTE]

Well, I could live with that. AT LEAST I don't have to use a magnifying glass to read text on the screen. =\


[QUOTE=SD-Plissken said:**
> Have you bothered to install the OS? you can't make the screen adjustment you  need using the live cd.

I had pretty much the exact same problem with Ubuntu 6.06 a while ago, so I don't know if I should spend an another evening installing the distro, only to find out that I can not get the resolution right and end up having to delete all the Linux partitions and the bootloader, and to wake up with bleeding eyes in the morning.
I don't know, should I do that? =)

---

### Post by localuser on 2006-10-26
I think you had a problem with your monitor in 6.06 didn't you?  About a month ago.

What kind of monitor are you using?

{Edit] Nevermind, I just saw the bottom of your post which lists your hardware.

---

### Post by amorris.math on 2006-10-26
I didn't find your post to be rude.  I find it rude when people on a forum take offence to something that is not offensive or rude.

---

### Post by John.Michael.Kane on 2006-10-26
Is this a largescreen LCD,and what model/manufacturer. It seems that Xorg is autodetecting your res,and using the optimal settings.

At the veryleast you should do a test install,and install your proper drivers,and edit your xorg to include to needed info.

---

### Post by Henry Rayker on 2006-10-26
One thing you could try is to edit the xorg file and remove the resolution in question. Sure, it may not allow you to change the refresh immediately, but it would be at a smaller resolution. I think that's a moot point, however, if you can't restart the session (ctrl alt backspace). It's worth a shot.

Also, amorris.math, did you see his post prior to a moderator editing it? The image was full screen and caused the text to go all the way across prior to wrapping around. This is, indeed rude. If you are asking someone for help, you should try to make the situation as comfortable for the person as possible. Especially in a situation like this (where the help is coming from complete volunteers).

sc0undrel: I'm sorry for having not read your sig...a lot of times sigs are full of nonsense and the like...that combined with the way everything else was formatted, I just overlooked it.

---

### Post by sc0undrel on 2006-10-26
[QUOTE=SD-Plissken]Is this a largescreen LCD,and what model/manufacturer. It seems that Xorg is autodetecting your res,and using the optimal settings.[/QUOTE]

No, not a lame LCD, my friend.
It's one badass CRT that goes up to 2048x1536. I'm sort of a gamer, so I pretty much don't like LCDs, becase of their very poor response times and afterglow. And their locked resolutions/refreshrates, which limit the framerate. ](*,)

[QUOTE=SD-Plissken]At the veryleast you should do a test install,and install your proper drivers,and edit your xorg to include to needed info.[/QUOTE]

Alright, I'll give it a try. =)


Henry Rayker: That's okay. I also often overlook other users' signatures. :mrgreen:

---

### Post by sc0undrel on 2006-10-26
WHY does it have to be like that?!

I installed Ubuntu. After booting into it, the resolution was still 1920x1440. I used the "sudo dpkg-reconfigure xserver-xorg" command, and answered all the questions. Then I did a reboot.

Upon the next boot, it didn't go past the bootscreen.
I can't get into the GUI shell. And I'm much too depressed to even try the fscking command line.

I don't know, I really like the Ubuntu philosophy and everything about open-source software, but with this neverending resolution problem, I just can't enjoy it.

Yet again I have to fall back to m$ wind0ze warez, for now. =\
Or perhaps I'll try it in Vmware Workstation (although it lags like HELL in it).

---

### Post by localuser on 2006-10-26
Are there driver differences between the AMD64 iso and the x86 version?

---

### Post by ethan961 on 2006-10-26
Ouch. Im scared as hell to install Ubuntu now that I frequently read the forums. But that's my problem, I'll install it anyways now that I'm so fed up with M$.

---

### Post by Henry Rayker on 2006-10-26
Doesn't Edgy have a bug with the X server or something? You may want to try 6.06 (Dapper Drake)...this is assuming you were trying edgy (6.10)

Edit: second offense for not reading the sig...

---

### Post by sc0undrel on 2006-10-26
[QUOTE=ethan961]Ouch. Im scared as hell to install Ubuntu now that I frequently read the forums. But that's my problem, I'll install it anyways now that I'm so fed up with M$.[/QUOTE]

Word! I'm also fed up with m$. Though I'm also fed up with this resolution problem. So I'm in front of a dilemma.

Anyway, good luck with the Ubuntu install, hope get everything working! :)

[QUOTE=ethan961]Doesn't Edgy have a bug with the X server or something? You may want to try 6.06[/QUOTE]

Dunno about the bug. I have 6.06 also burned to a CD, but I have the exact same problem with it. So no good reason to fall back to 6.06, I suppose.

---

### Post by RudolfMDLT on 2006-10-26
Hi!

Dude, it takes 30 min max to install Ubuntu, granted you already have partitioned your drives. On a machine like yours... 20 min!

You've been on this tread 2 hours. Please install the OS. From there people can help you with concrete config files. Now it's just a case of poking in the dark and hoping something works. 

it's just a simple reformat if it doesn't work. 

I won't be able to help though as it's almost 00:00 this side of the globe.

Anyhow, good luck.

Cheers,

Rudolf

---

### Post by John.Michael.Kane on 2006-10-26
Under xorg you may look for these. this xorg is just an example

Edit the lines in bold to fit your monitor needs. also make sure your drivers are installed correctly first.

[B]HorizSync       30.0-85.0 
   VertRefresh     50.0-160.0
  # 1024x768 @ 85.00 Hz (GTF) hsync: 68.60 kHz; pclk: 94.39 MHz
    Modeline "1024x768_85.00"  94.39  1024 1088 1200 1376  768 769 772 807  -HSync +Vsync[/B]
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82815 CGC [Chipset Graphics Controller]"
	Monitor		"DELL M782"
**	DefaultDepth	24** change to 16 [COLOR="Red"]you can change it back if you need to[/COLOR]
	SubSection "Display"
		Depth		1
		Modes		**"1024x768_85.00"** "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection


modeline generator [http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php)

---

### Post by localuser on 2006-10-26
> **ethan961 said:**
> Ouch. Im scared as hell to install Ubuntu now that I frequently read the forums. But that's my problem, I'll install it anyways now that I'm so fed up with M$.

No worries.  There are many many very happy Ubuntu Linux users who have minor if any problems.  Don't get me wrong, there are bound to be some issues simply because of the larger user and developer base for Windows.

Unless you have an unusual piece of hardware, then you will more than likely be able to run Ubuntu with minor problems.

---

### Post by Christmas on 2006-10-27
I don't know why your system crashes when you try to change the screen resolution, but you can try and edit the /etc/X11/xorg.conf file and set the maximum resolution at the value you want it to use. For example, if you want to use 1280x1024, then edit it and instead of something like:
```

...
# here are other options for different depths
...
       SubSection "Display"
		Depth		24
		Modes		"1920x1440" "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```
Put:
```

SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```
This way it will use the maximum, that's 1280x1024.

---

