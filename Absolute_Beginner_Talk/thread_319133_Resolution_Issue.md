---
title: "Resolution Issue"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by Stephen47 on 2006-12-15
I am trying to get a resolution problem fixed. In System>preferences>screen resolution the only choice I have is 1280 x 1024. My LCD panel supports 1650 x1080. When I went to edit the
/etc/X11/xorg.conf file the only resolution listed was 1680 x 1050 so now what do I do

---

### Post by ddtrust on 2006-12-15
please post your xorg.conf "monitor" and "screen" sections here, maybe there's still something wrong.

---

### Post by Stephen47 on 2006-12-15
here it is:
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050"
	EndSubSection
EndSection

---

### Post by ZERO_SHIFT on 2006-12-15
Did you install your graphic drivers?

---

### Post by ddtrust on 2006-12-15
I think you should try to use some good online modeline calculator to add modeline setting to your monitor section. Maybe that helps?

---

### Post by Stephen47 on 2006-12-15
where might I find the graphic drivers?
any direction to find and explain what a modeline calculator is and how to add modeline settingss?

---

### Post by Kobalt on 2006-12-15
To add more resolutions avaliable you must enter this command line : 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then select the resolutions you want avaliable with the **spacebar**. Press Enter then restart X by pressing Ctrl+Alt+Backspace. 

And enjoy :)

---

### Post by Stephen47 on 2006-12-15
I did that but the only thing that happened was the screen went black then some scattered colors flashed the what looked like a snowstorm flashed and I had to log in and it rebooted with no change.

---

### Post by Stephen47 on 2006-12-15
I found a modeline calculator and entered 1080x 1050 @60Hz and this is what it said were the monitor parameters:
# 1680x1050 @ 60Hz,  65.04 kHz hsync
    Mode "1680x1050"
    DotClock    136.32
    HTimings  1680 1720 1856 2096
    VTimings  1050 1053 1056 1084
what does this mean and what do I do with it?

---

### Post by ddtrust on 2006-12-16
> **Stephen47 said:**
> 
I found a modeline calculator and entered 1080x 1050 @60Hz and this is what it said were the monitor parameters:
# 1680x1050 @ 60Hz,  65.04 kHz hsync
    Mode "1680x1050"
    DotClock    136.32
    HTimings  1680 1720 1856 2096
    VTimings  1050 1053 1056 1084
what does this mean and what do I do with it?


Hmm.. I wonder why it gave you resolution values 1680x1050 if your input values were 1080x 1050. Here's sample of my monitor section and how to use modeline value. I also tried to find the modeline calculator which I used, but I had no success.


```

Section "Monitor"
        Identifier      "SonyLCDTV"
        Option          "DPMS"
        HorizSync       28-100
        VertRefresh     43-75
        # 1360x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 84.72 MHz
        Modeline "1360x768_60.00"  84.72  1360 1424 1568 1776  768 769 772 795 -HSync +Vsync
EndSection

```

---

### Post by ddtrust on 2006-12-16
Here's pretty good guide to set correct resolution: [http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)

And here's the modeline calculator which I used:
[http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php)

---

### Post by Stephen47 on 2006-12-16
I am trying for 1680x1050 that was a typo in my previous post.

---

### Post by Stephen47 on 2006-12-16
bump

---

### Post by scxtt on 2006-12-16
i doubt there's any real use for modelines ... just make sure your "Monitor" section contains valid HorizSync and VertRefresh lines and it should sort itself out ...
```
Section "Monitor"
        Identifier      "Monitor"
        Option          "DPMS"
        HorizSync       28-100[color=red]*[/color]
        VertRefresh     43-75[color=red]*[/color]
EndSection
```[color=red]*[/color]=not sure what your values should be ...

---

### Post by Stephen47 on 2006-12-16
this isn't a monitor it a laptop lcd screen the only thing in my monitor section is :Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
grrr

---

### Post by scxtt on 2006-12-16
you're kidding, right ;)

same difference my friend, it's still a "monitor" ...

---

### Post by ddtrust on 2006-12-17
> **scxtt said:**
> 
i doubt there's any real use for modelines ... just make sure your "Monitor" section contains valid HorizSync and VertRefresh lines and it should sort itself out ...
```
Section "Monitor"
        Identifier      "Monitor"
        Option          "DPMS"
        HorizSync       28-100[color=red]*[/color]
        VertRefresh     43-75[color=red]*[/color]
EndSection
```[color=red]*[/color]=not sure what your values should be ...


You should check those values from your laptops manual. But if you use modeline values, those values are not necessary. Read the link I posted earlier, I think that might help you. :confused:

---

### Post by Stephen47 on 2006-12-17
call it what you will but there is nothing in my monitor section that lists horiz sync nor vertrefresh.

---

### Post by Stephen47 on 2006-12-17
call it what you  will there still is no horiz sync not vert refresh in my monitor section, as you can see from my post

---

### Post by scxtt on 2006-12-17
you type it in . . . :-k

---

### Post by joker81 on 2006-12-18
[http://packages.ubuntu.com/dapper/x11/915resolution](http://packages.ubuntu.com/dapper/x11/915resolution)

Try check this out, hope this help.

---

### Post by Stephen47 on 2006-12-18
Do you see the theme of this forum? "Absolute Beginner Talk"
Type it in where?
How do I install 915resolution? I have it saved on the desktop.

---

### Post by scxtt on 2006-12-18
> **Stephen47 said:**
> Do you see the theme of this forum? "Absolute Beginner Talk"
Type it in where?the file you brought up in your initial post, the file we've been talking about the whole time ...

---

### Post by Stephen47 on 2006-12-18
So I edit that file and just add those lines? Why a range when the refresh rate is 60

---

### Post by scxtt on 2006-12-18
yes - add them to /etc/X11/xorg.conf ... monitor will work refresh rate out ...

---

### Post by Stephen47 on 2006-12-18
Ok I'm lost again now I can't even find /etc/X11/xorg.conf. I did a search for it in search for files and no files were found anywhere. what is the command to edit a file like this? Sorry to seem so obtuse.

---

### Post by scxtt on 2006-12-18
do something like:

[indent]gksudo kwrite /etc/X11/xorg.conf[/indent]

and enter your password in the box that pops up, then add those lines to the "Monitor" section ...

note: use any gui txt editor you have for "kwrite" (i forget what it is in gnome) :p ... and if you use KDE, replace **gksudo** w/ **kdesu**

---

### Post by Stephen47 on 2006-12-19
Well I'm in a fine mess now. I typed in the Horizsync and VertRefresh values and now the display display I am in a DOS-like environment. how do I re-edit that file? If all else fails can I re-install Ubuntu over the current one?

---

### Post by ddtrust on 2006-12-19
> **Stephen47 said:**
> Well I'm in a fine mess now. I typed in the Horizsync and VertRefresh values and now the display display I am in a DOS-like environment. how do I re-edit that file? If all else fails can I re-install Ubuntu over the current one?

You should always, I mean ALWAYS, take a backup copy of your config files before you start editing it, like this:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

If you have done this, you can restore the backup file typing in terminal:

```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

;)

---

### Post by eXisor on 2006-12-19
lf you're still having this problem, try the howto I did in the link below. In my experience Linux sucks at autodetecting monitor modelines, so you have to do it yourself.

[http://ubuntuforums.org/showpost.php...99&postcount=2](http://ubuntuforums.org/showpost.php...99&postcount=2)

---

### Post by Stephen47 on 2006-12-19
I didn't back it up, is there a way to edit it in console mode or whatever they call the black screen? That link just takes me to the forum home page. What is the title of the thread?

---

### Post by Stephen47 on 2006-12-19
ok I am back in business. I edited the file and put it back to where it was and I now have a gui again. so I am going to press on. Any more suggestions?

---

### Post by Stephen47 on 2006-12-19
I developed a modeline using the advice given here: [http://www.ubuntuforums.org/showthread.php?t=174783&highlight=power+strip](http://www.ubuntuforums.org/showthread.php?t=174783&highlight=power+strip)
I entered it in my /etc/X11/xorg.conf file, rebooted and I am still at 1280x1024 with no options to change it to 1680x1050 what do I do now. This resolution is awful it distorts everything.here is a copy of the monitor section of my file:

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
#        HorizSync        60
#        VertRefresh      60
        Modeline "1680x1050@60" 65.520 1680 1728 1760 1840 1050 1052 1058 1080 -hsync -vsync
the Horizsync andVertRefresh are values I put in that caused the gui to not work.
Any help?

---

### Post by ddtrust on 2006-12-20
> **Stephen47 said:**
> I developed a modeline using the advice given here: [http://www.ubuntuforums.org/showthread.php?t=174783&highlight=power+strip](http://www.ubuntuforums.org/showthread.php?t=174783&highlight=power+strip)
I entered it in my /etc/X11/xorg.conf file, rebooted and I am still at 1280x1024 with no options to change it to 1680x1050 what do I do now. This resolution is awful it distorts everything.here is a copy of the monitor section of my file:

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
#        HorizSync        60
#        VertRefresh      60
        Modeline "1680x1050@60" 65.520 1680 1728 1760 1840 1050 1052 1058 1080 -hsync -vsync
the Horizsync andVertRefresh are values I put in that caused the gui to not work.
Any help?

Hmm... this gets interesting.. since you have the correct resolution on your screen section, I'm really starting to wonder what's wrong... Could you post the whole xorg.conf if there's still something wrong with the setup?

---

### Post by scxtt on 2006-12-20
> **Stephen47 said:**
> I developed a modeline using the advice given here: [http://www.ubuntuforums.org/showthread.php?t=174783&highlight=power+strip](http://www.ubuntuforums.org/showthread.php?t=174783&highlight=power+strip)
I entered it in my /etc/X11/xorg.conf file, rebooted and I am still at 1280x1024 with no options to change it to 1680x1050 what do I do now. This resolution is awful it distorts everything.here is a copy of the monitor section of my file:

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
#        HorizSync        60
#        VertRefresh      60
        Modeline "1680x1050@60" 65.520 1680 1728 1760 1840 1050 1052 1058 1080 -hsync -vsync
the Horizsync andVertRefresh are values I put in that caused the gui to not work.
Any help?if you used:

#        HorizSync        60
#        VertRefresh      60

when you had the X problem dropping you to a CLI, that makes sense -- doing it that way is **completely wrong** ... you supply a range, then the monitor is "smart" enough to report usable WxH options ...

there's no reason your laptop's manual shouldn't have the HorizSync and VertRefresh ***_RANGES_*** in it --- look there and use those values ...

---

### Post by ramjet_1953 on 2006-12-20
I'm not sure if you have fully explored the advice given about 915resolution.
I noted that you have an Intel graphics chipset.
If you have a look at the documentation file that comes with the 915resolution package, it shows you how to implement it, without having to modify any files yourself.
915resolution certainly solved my laptop widescreen resolution issue painlessly.

Regards,
Roger 8)

---

### Post by Stephen47 on 2006-12-20
I have 915 resolution sitting on my desktop I just don't know how to install it. Don't I have to run it every time I boot my computer? That seems to be what the documentation says.
As for the Range of refresh rate. I asked about that and got no response. Everything I look at regarding that says the rate is 60 I even called Dell and that is what they told me. Should I just put in an arbitrary range with 60 somewhere in the middle? 
I just talked with Dell again. The guy "Thomas" told me there is no range. 60 is the only valid refresh rate.

---

### Post by scxtt on 2006-12-20
DO NOT - i repeat - DO NOT just download a *.tar.gz, place it on your desktop and expect to easily install it ... that's what apt-get / aptitude are for -- no worries about dependencies ... do something like **sudo aptitude search 915resolution** and see if that package comes up (i know i've seen it, but have no use for it myself - and maybe just search for 915) ... install it that way and save yourself more headaches **sudo aptitude install 915resolution** ... tho i don't believe it should matter @ all if you use that ...

as far as the whole "60" issue, setting H and V rates to just "60" won't do crap for you ... as i said before - you give it a range (for them both) and it will use a value that corresponds to the monitor's allowable resolutions (640x480 @ 44, 1024x768 @ 56, 1280x1024 @ 60, etc - any resolution the monitor is SUPPOSED to do at a given rate -- think of it as being "built in", there's a little brain inside the monitor that says "hey, i do these resolutions - i just need someone (or OS) to give me the right range") ...

"60" might be the CORRECT rate for 1680x1050, but you don't specify just "60" in your "Monitor" section - no matter what Dell tells you ... as far as an arbitrary range, it would be better than "60" but there's NO REASON you can't get the correct range from your laptop's literature, online, or from "Thomas" ...

what make (dell?) and model laptop do you have?

---

### Post by Stephen47 on 2006-12-20
I have looked at the online documentation here: [http://support.dell.com/support/edocs/systems/ins6400/en/om/specs.htm#wp1054574](http://support.dell.com/support/edocs/systems/ins6400/en/om/specs.htm#wp1054574)
as you can see it only says 60 Hz for refresh rate. I have an Inspiron E1505 Core duo processor 1 GB RAM.
Thanks for the advice on the 915resolution.

---

### Post by Stephen47 on 2006-12-20
I put in some numbers for H and V rates and rebooted. Now in the screen resolution box in systen>preferences there are options for reolution that weren't there before. Unfortunately 1680x1050 isn't one of them. there are no choices in refresh rate but it has changed. Before it was 60 now it is 75. Is there really no solution to this problem?
I did  sudo aptitude search 915resolution and nothing happened just went back to the prompt.

---

### Post by scxtt on 2006-12-20
what "driver" are you using?  do a **cat /etc/X11/xorg.conf | grep Driver** and paste it in this thread ...

i really don't think 915resolution will help you out, since you don't have an Intel 915 chipset (i'm using Sabayon, but '915resolution' is still the same):
```
:> emerge -s 915
Searching...
[ Results for search key : 915 ]
[ Applications found : 1 ]

*  sys-apps/915resolution
      Latest version available: 0.5.2
      Latest version installed: 0.5.2
      Size of files: 20 kB
      Homepage:      http://www.geocities.com/stomljen/
      **[color=red]Description:   Utility to patch VBIOS of Intel 855 / 865 / 915 chipsets[/color]**
      License:       public-domain
```
```
Video type:
 integrated on system board
 
Video controller
 [color=red]**Intel 945 GM**[/color]
 
Video memory
 up to 128 MB of shared memory (with 256 MB of system memory) or 224 MB of shared memory (with 512 MB of system memory)
 
LCD interface
 LVDS

Video type:
 discrete video card 
 
Data bus
 PCI Express X16
 
Video controller
 ATI Mobility Radeon X1300 or X1400 or nVidia GeForce Go 7300
 
Video memory
 64 MB (X1300) or 128 MB (X1400 or GeForce Go 7300)
```

---

### Post by Stephen47 on 2006-12-21
Well I seem to have gotten myself in another situation here. I found this link: [http://kubuntuforums.net/forums/index.php?topic=5186.0](http://kubuntuforums.net/forums/index.php?topic=5186.0) which seemed to be just what I was looking for. I followed the advice given here: [https://help.ubuntu.com/community/i915Driver](https://help.ubuntu.com/community/i915Driver). I apparently answered the questions wrong when I tried to
"Make xorg use the i815 driver. I did this by executing "sudo dpkg-reconfigure xserver-xorg"  and answering all the questions"  When I rebooted I was back at the black command line screen apparently having answered the questions wrong. Let me say that I first ran the : sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup" command but as I mentioned in my last post after I ran the command the terminal just returned to the prompt. I assumed (bad assumption) it had been backed up so I ran
"sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf" but I was told no such file existed. Fortunately I had printed a copy of the Monitor and screen sections of my xorg.conf file. I edited the file but when I tried to save it I got a "permission denied" message. What do I have to do to edit this file and save it?
Thanks for your patience on this.

---

### Post by Stephen47 on 2006-12-21
I ran the grep driver command and here is what I got:
driver   "kbd"
driver   "mouse"
driver   "synaptics"
driver   "wacom"
driver   "wacom"
driver   "wacom"
driver   "vesa"

---

### Post by Stephen47 on 2006-12-21
Well I am visual in ubuntu again. I was able to edit my xorg.conf file. How do I know if the file has been backed up when I run: "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup" ?

---

### Post by riven0 on 2006-12-21
> **Stephen47 said:**
> Well I am visual in ubuntu again. I was able to edit my xorg.conf file. How do I know if the file has been backed up when I run: "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup" ?

Do a 

> cd /etc/X11 && ls -a 

That way you can view the files.

---

### Post by Stephen47 on 2006-12-21
ok I did that here is what came up:
steve@steve-laptop:~$ cd /etc/X11 && ls -a
.                        gdm         xorg.conf.20061212201357  Xresources
..                       rgb.txt     xorg.conf.20061212202919  Xsession
app-defaults             X           xorg.conf.20061212203430  Xsession.d
config                   xinit       xorg.conf.20061215202543  Xsession.options
cursors                  xkb         xorg.conf.20061215203028  Xwrapper.config
default-display-manager  xorg.conf   xorg.conf.20061220201528
fonts                    xorg.conf~  xorg.conf_backup
I assume the numbers refer to time and date. the Xsession notes are in different colors.
What does it all mean?

---

### Post by riven0 on 2006-12-21
> **Stephen47 said:**
> ok I did that here is what came up:
steve@steve-laptop:~$ cd /etc/X11 && ls -a
.                        gdm         xorg.conf.20061212201357  Xresources
..                       rgb.txt     xorg.conf.20061212202919  Xsession
app-defaults             X           xorg.conf.20061212203430  Xsession.d
config                   xinit       xorg.conf.20061215202543  Xsession.options
cursors                  xkb         xorg.conf.20061215203028  Xwrapper.config
default-display-manager  xorg.conf   xorg.conf.20061220201528
fonts                    xorg.conf~  xorg.conf_backup
I assume the numbers refer to time and date. the Xsession notes are in different colors.
What does it all mean?

Alright, here are your backups:

xorg.conf.20061212201357
xorg.conf.20061212202919
xorg.conf.20061212203430
xorg.conf.20061215202543
xorg.conf.20061215203028
xorg.conf.20061220201528

It looks like you've got quite a few, so it's probably safe to delete everything but the newest backups.

> cd /etc/X11 && sudo rm -r xorg.conf.20061212201357 xorg.conf.20061212203430 xorg.conf.20061215202543 xorg.conf.20061215203028 xorg.conf.20061212202919


To make sure you've still got one backup left

> ls -a 

EDIT: BTW, blue text means a separate directory and green text means an executable file. Light blue text usually means a symbolic link.

---

### Post by Stephen47 on 2006-12-22
I ran;"ls -a" and none of the xorg.conf backups showed up and I haven't deleted anything yet. also how come when I tried to use the backed up version I got a message that the file didn't exist? Also what does red text mean?

---

### Post by Stephen47 on 2006-12-23
I tried the changes suggested in the Kubuntu link I mentioned in post #42 and lost my gui again. So I re-edited the chnages and am back to square on. is there any hope for resolving this issue?

---

### Post by Stephen47 on 2006-12-25
I am now at 1680x1050

---

### Post by waldorf on 2006-12-27
Congratulations!

I have been having the same problem and I sympathize with the craziness I have just read you going through. 

Could you please tell us in a single post how you finally got to 1680x1050 - a would love to know.

---

### Post by Stephen47 on 2006-12-27
What I did was issue these commands in terminal:
sudo -v
then:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
sudo sh -c 'md5sum /etc/X11/xorg.conf > /var/lib/x11/xorg.conf.md5sum'
sudo dpkg-reconfigure xserver-xorg
put all three lines in terminal at once, answer the questions. if you don't know the answer use the default. the main one is to be sure the resolution you want is selected and no others.
the problem with this fix is that it is only session based. that is when you reboot you have to do it again. I haven't been able to find out how to make it permanent.

---

