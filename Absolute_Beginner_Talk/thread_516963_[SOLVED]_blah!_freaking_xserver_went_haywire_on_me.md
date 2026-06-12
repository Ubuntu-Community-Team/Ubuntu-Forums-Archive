---
title: "[SOLVED] blah! freaking xserver went haywire on me!"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by S15_88 on 2007-08-03
Basically i've been runninng ubuntu with very few minor problems for a few months now and this is what happened!  but this is not my actuallll problem!  for some reason every time i resized video players the audio keeps playing but the video playback goes black. and this is in movie player, VLC and other video playback software, so i figured it had to be a video driver or xserver thing. 

 after downloading the driver for my Intel 945 and reading the readme/setup it was total chaos and to be honest i didn't really understand it!  so i decided to do:  sudo dpkg-reconfigure xserver-xorg and so i went through it and didn't change anything!  next time i restarted i got the crazy blue screen with crazy letters saying my xserver is not configured properly! so i ran the same command and rebooted and it went to my customized log on screen from before and i log in see the ubuntu welcome then get the white screen with cursor!  how can i get a terminal or command line to run that command again!  and can someone please explain how to properly configure the xorg file or at least point me to an article or how to.

thanks in advance for all the help!

Thanks, Alain

---

### Post by splintercellguy on 2007-08-03
Fall back to VESA driver with sudo dpkg-reconfigure xserver-xorg, that should get you back up and running. After that, can you post the output of lspci | grep VGA?

---

### Post by S15_88 on 2007-08-03
how do i fall back to the vesa driver if i can't enter the code anywhere? i don't get command line or terminal! i ahve it dual booted with vista, so it goes grub, boots, log on screen, then blank screen, where/how can i get some command line action goin? man i dunno why it went all crazy i had it on the vesa driver and 1440x900 resolution and everything was perfefct!  thanks for the reply though look forward to getting this resolved promptly!  i was just in vista and did ctrl alt right arrow! trying to get another workspace and it flipped my screen! ahha every time i boot into ubuntu my vista partition shrinks more and more! anyways back to xserver, let's get this pup working again!

Thanks, Alain

---

### Post by splintercellguy on 2007-08-03
Use the recovery mode or press Ctrl-Alt-F1.

---

### Post by S15_88 on 2007-08-03
k i'm gunna reboot brb!

---

### Post by S15_88 on 2007-08-03
this is no good i'm spiraling downhill big time and fast!  what happens in recovery mode is i get the command line and i type the command, do the whole setup then i reboot and go into recovery mode get the log on screen log in but white screen with cursor! then if i do ctrl + alt + baclspace top restart the xserver still same thing white screen after log on.  so then i rebooted into regular ubuntu and i got the error did the whole setup took alllll the default options and then reboot and same error message!

don't know if this error pertains to the xserver but i have splash and quiet commented out of boot.lst and when ubuntu boots everything has [ok] at the end except:

  * mounting local filesystems...
mounting: special device /dev/disk/by-uuid/7060BAA060BA6DOA does not exist [[COLOR="Red"]fail[/COLOR]]

---

### Post by splintercellguy on 2007-08-03
You could attempt to fall back to the old xorg.conf configuration. When reconfiguring X Server, some xorg.conf backup files should have been generated. Perhaps you could mv those files into xorg.conf?

---

### Post by S15_88 on 2007-08-03
just out of curiosity how would one accomplish that?  thanks for all the help already i just don't get why it went crazy like this and why it worked with all the default settings before and now it won't!  it seems like the main settings are the driver which i'm selecting vesa, the resolution which i've tried using the default and adding 1440x900 but neither did anything!  blah this just has me puzzled!  quick question though if i go into recovery mode and do:
 sudo nautilus and edit the boot.lst to include my previous ubuntu setup then reboot it will refer to the previous xorg.conf file?  shooot i totally didn't think of that earlier i'm going to give that a try!

Thanks, Alain

---

### Post by S15_88 on 2007-08-03
no dice on the nautilus needs a window to open adn the xserver won't allow the window to open, is there a program i can install in windows adn take my files i need from ubuntu and do a fresh install?? man this is so frustrating !!!

---

### Post by dasunst3r on 2007-08-03
Here's how you would go about moving one of the backup xorg.conf files.  Commands are in italics:
[list=1]
[*]Login to the console
[*]*cd /etc/X11* (/etc/X11 is where your graphical server configuration is located)
[*]*dir* (we would like to know what all is there)
[*]*cp {A backup file} xorg.conf* (Replace whatever is in the braces with a .conf file that you decide to recover from
[*]*/etc/init.d/gdm restart* (Restart graphical server)
[/list]
I notice that you did not tell us what video card you have.  Please tell us that so we can help you better.

---

### Post by S15_88 on 2007-08-03
that looks like good stuff i'll give that a try!  the card is in the first post actually haha but it's all good i'll let it slide, it's one of them Intel 945 EXTREME graphics haha an Nvidia wouldn't physically fit in my laptop, but it's all good cause i only use this for programming and work stuff, no gaming.  thanks for the help!

Thanks, Alain

---

### Post by perspectoff on 2007-08-04
I would also check your Horiz Synch and Vert Refresh settings for your monitor in the /etc/X11/xorg.conf file.

Ubuntu Feisty did not autodetect mine properly and my screen also went white.

In recovery mode, I logged in and then edited my xorg.conf file:

 sudo gedit /etc/X11/xorg.conf

I had to change the section:
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-90
	VertRefresh	50-120
EndSection

to:

Section "Monitor"
	Identifier	"KDS XF-7b"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-70
EndSection

And change:

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82945G/GZ Integrated Graphics Controller"
	Monitor		"Generic Monitor"


to

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82945G/GZ Integrated Graphics Controller"
	Monitor		"KDS XF-7b"

Obviously, I use a KDS XF-7b monitor, and I had to look up the monitor's Horizontal synch and Vertical Refresh specifications.

You would have to do the same for your monitor. 

Of course, this may not be your problem, but if you are grasping at straws....

---

### Post by S15_88 on 2007-08-04
ok i followed ur instructions dasunster3r, but i hate to break it to u i got a few errors adn some more chaos and since u led me down this path i'm hoping u have the answers, but i'm very grateful for your help! now i ahve my desktop back!  wrong resolution but i'll just manually add that to the xorg.conf file.  when i logged in i got a few errors:
> initial error failed to initialize HAL

> Cannot access ACPI events in /var/run/acpid.socket!
make sure the ACPI subsytem is working and the acpid daemon is running 

and i also have a few folders that are off the screen i can only see the very edge, is this because my previous resolution was 1440x900 and now it's 1024x768?  Also i thought this might add some comic relief to alll my troubles, my HD Temp display reads Hitachi the proper HD but says it's -1 degree celcius!  but the CPU temp is right, 46 degrees celcius.  and also it says i'm running on AC power, no battery present!

but other than that it's great and i sincerely appreciate all the help!

thanks, Alain

---

### Post by S15_88 on 2007-08-04
ok i changed my xorg.conf to have only 1440x900! and uncommented my previous ubuntu version from my menu.lstand  gave her a reboot and went into regular ubuntu and nooooo erros! full battery! HD Temp is back up to 45 degrees celcius although that was pretty cool when it showed -1 haha and wifi works too!

I would just like to thank everyone for their input and appreciate it greatly!  now that you've given me this all this knowledge surrounding my problem one day when someone else has this problem i'll be able to help them!  thanks alot guys and girls!


Thanks, Alain!

---

