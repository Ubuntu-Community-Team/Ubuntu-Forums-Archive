---
title: "Linux Mint Helena LXDE PowerPC"
date: 2010-04-17
forum: Apple Hardware Users
---

### Post by linuxopjemac on 2010-04-17
[http://mac.linux.be/content/linux-mint-helena-lxde-powerpc](http://mac.linux.be/content/linux-mint-helena-lxde-powerpc)

---

### Post by conal on 2010-04-18
That is a brilliant plan. I have always wished for a PowerPC version of Linux Mint and LXDE is by far the best option for older macs! Good luck!

---

### Post by linuxopjemac on 2010-05-03
[http://mac.linux.be/content/linux-mint-lxde-debian-50-ppc-fact](http://mac.linux.be/content/linux-mint-lxde-debian-50-ppc-fact)

---

### Post by anurse on 2010-05-03
Congrats. This is wonderful to see!

---

### Post by linuxopjemac on 2010-05-03
:p

---

### Post by B_Free on 2010-05-03
We have had discussions about many fixes to Ubuntu and Debian "Lenny". I like the look of Mint. But is this just another version of Debian? I finally did get Lenny on my iMac 266 to work thanks to you and oswaldkelso. Thank you! But (there is always a but) only to find that most of the software (OpenOffice) crashes. The thought of a light weight (any) version would be great. The original reason I looked into Linux was as a way of recycling. To promote it through our small recycling effort here in Arizona. 
My question to you is "Can we make the old, old Macs just a lean web surfing, video watching machine?" Just the base system with Firefox and appropriate plugins.

---

### Post by linuxopjemac on 2010-05-04
This version of Mint is based on Debian. In fact, it's pure Debian with some programs form Mint to make it look better and to make it Mint (like to have the fortunes in a shell and to have the more user friendly Software manager and Mint update). I have to disappoint you on the video part. Flash is and will be problematic. Maybe in a next version of Mint, when I upgrade to Squeeze, I might have a better gnash for you. I can only hope for HTML5 in that respect, see the [article]("http://bexhuff.com/2009/06/html-5-versus-flash-flex").

Concerning Open Office. That should work, I tried it on my Pismo with Debian Lenny. You can also install Abiword....

---

### Post by conal on 2010-05-04
Will this work with a Lenny install that has been tinkered with a bit? (I have already installed LXDE, codecs, and some programs on my G3) What's the worst that can happen? Exploding Mac? 

I'd probably rather risk bugs than reinstall -  it took a long time to install Lenny!

cheers

Conal

---

### Post by linuxopjemac on 2010-05-04
I guess that if you run the script, you will end up more or less where you want to be, unless you installed a different kernel. It will only install more packages and then the mint specific programs. It will not change anything to your xorg.conf and stuff like that. It won't wipe out your home folder either.

---

### Post by conal on 2010-05-04
Brilliant, thanks. I'll give it a go tonight!

---

### Post by linuxopjemac on 2010-05-04
Can you post your xorg.conf file ? I like to publish it on my own site.

---

### Post by conal on 2010-05-04
Sure, I'm not near my G3 just now but I'll post it later.

Cheers

Conal

---

### Post by conal on 2010-05-04
My Mac is now minty-fresh thanks to your fabulous work on the linux mint script!

Below is my xorg.conf file. This one is different from the one I was previously using on this machine with Ubuntu 9.10 (which would not work with Debian Lenny):
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:lwin_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	BusID		"PCI:0:16:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync 58-62
	VertRefresh 75-117
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
EndSection

Section "Module"
	Disable "glx"
	Disable "dri"
EndSection
```

---

### Post by conal on 2010-05-04
Sorry, should clarify, the above xorg.conf file is for my iMac G3/400 DV running Debian Lenny (and now linux mint!)

Cheers

Conal

---

### Post by linuxopjemac on 2010-05-04
ok, nice to hear that it all worked out so well for you. You are the second happy, or should I say third (I was the first actually) Linux Mint LXDE PPC user. hehehe What I mean is the xorg.conf file for the iLamp. Thanks.
J

---

### Post by conal on 2010-05-04
Oh yeah, well at the moment I am back to using the iLamp without an Xorg.conf file. This works fine for me in 9.10 (except for the external monitor). I have made it generate an xorg.conf file using ```
sudo xorg -configure
``` so we can see the defaults:

```

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dri"
	Load  "dri2"
	Load  "extmod"
	Load  "record"
	Load  "dbe"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "HWcursor"           	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "UseFBDev"           	# [<bool>]
        #Option     "Rotate"             	# [<str>]
        #Option     "VideoKey"           	# <i>
        #Option     "FlatPanel"          	# [<bool>]
        #Option     "FPDither"           	# [<bool>]
        #Option     "CrtcNumber"         	# <i>
        #Option     "FPScale"            	# [<bool>]
        #Option     "FPTweak"            	# <i>
        #Option     "DualHead"           	# [<bool>]
	Identifier  "Card0"
	Driver      "nv"
	VendorName  "nVidia Corporation"
	BoardName   "NV18 [GeForce4 MX with AGP8X (Mac)]"
	BusID       "PCI:0:16:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

---

### Post by cedicon on 2010-05-06
Thank you for PPC Mint LXDE - I just installed it on my G4 iLamp. The only thing I had to do to get X working after the installer finished was add the "Option" "Flatpanel" "true" to the xorg.conf.

It will take me a few days to toy around with it but I'm already excited for the new desktop environment. Thanks in advance for your dedication to PPCs!


(PS. Also thanks for your help with the Wacom driver issue - I haven't resolved it yet - just saving it for a rainy day)

---

### Post by linuxopjemac on 2010-05-06
Cedicon: Can you post your xorg.conf file together with the specs of your mac in my [Linux Mint forum]("http://mac.linux.be/phpBB3/viewforum.php?f=16") please?

I am very delighted to see all these happy users.

---

### Post by conal on 2010-05-06
Right Cedicon, if all went well on your Lampy I'll give it a go on my one tonight!

My only concern is configuring the wireless as I've had trouble getting it working using ubuntu+lxde in the past - do you have any experience with that?

---

### Post by linuxopjemac on 2010-05-06
The problem you will face is that you don't have a nm-applet autostarted, what about you Conal ? I have to constantly, after I login:
```
sudo nm-applet
```
to then connect wirelessly (PCMCIA b43 module and firmware extracted with b43-fwcutter; WPA2 router). It works well though, no probs.
BTW Conal, why switch to Mint on the iLamp ?

---

### Post by conal on 2010-05-06
It's been a while but I think that was the problem. Maybe I'll leave it for now - my wife and kids prefer things to "just work!" 

Why switch to mint on the iLamp? Well, I have a small partition for OS X, a small one for Linux, and a big shared partition for media.

Currently I have ubuntu on the linux partition, however due to the CD/DVD automount problem I ended up installing Kubuntu as well, as someone else had posted they had no mount problem with Kubuntu. It worked!  But my linux partion is now full to bursting.

As I had such good experiences with Debian on my G3 (no mount problems etc) I had been meaning to do a reinstall with Debian on my iLamp. This would give me the excuse to do that, plus I could install mostly everything I need with the handy mint script - and it will look pretty too.

Conal

---

### Post by linuxopjemac on 2010-05-06
If it works now, I wouldn't change it. Unless you think Debian runs better. I would be interested to know this, as you have them both running now. I think you have a better chance of everything working out of the box with Debian. Debian, is an unpolished diamond. I polished it.

---

### Post by conal on 2010-05-06
Can't say I notice a performance difference, the real benefit with Debian is the lack of bugs. Also Ubuntu installs a lot of stuff I don't need, and getting all the mulitmidia & codec stuff working on Debian was easier.

---

### Post by natgab on 2010-05-11
> **linuxopjemac said:**
> [http://mac.linux.be/content/linux-mint-lxde-debian-50-ppc-fact](http://mac.linux.be/content/linux-mint-lxde-debian-50-ppc-fact)

Hi,

Just saw this post and like the idea of a Debian w/ Mint.  I have previously used Debian Lenny since I have a G3 iMac & Pismo and of course they have the video problems.  Does this work like Mint and have codecs & non-free software preloaded? Right now I went back to OS X only on my G3 iMac.  Might want to try again or is Lucid 10.04 any better for the video on the trouble maker computers? :P

Still haven't installed 10.04 on my Hackintosh in my sig, since its my main computer. I will wait for more bug fixes.

thanks

---

### Post by linuxopjemac on 2010-05-12
I did not install non-free video codecs. You migt want to add them yourself.
[http://debian-multimedia.org/](http://debian-multimedia.org/)

Linux Mint Debian runs pretty smooth. I don't have a solution for the lack of flash. I will start experimenting with H.264 in the future. I think a browser like midori with h.264 support would enable us to watch some video on youtube in an html5 applet I read somewhere. I will digg into this in the future, as x264 is the codec and it's in the debian multimedia repository.

---

### Post by conal on 2010-05-12
I installed the Debian non-free codecs. 

On my G3 iMac I have to download the Youtube videos anyway in OSX because they wont playback in any browser- it's just the same in Linux Mint - I download them then play them back. - no loss there! there are several plug-ins for Firefox for downloading these videos - I don't know about Epiphany or other browsers.

One big advantage for me with Linux on my G3 is that VLC (and all other players I have tried) can't handle playing back videos downloaded from the BBC Iplayer and similar sites under OS X.   However the same videos play back perfectly under Linux Mint using Totem. 

This means I can watch the programs that I pay my TV license for, without having to upgrade my hardware. So 1-0 to Linux!

---

### Post by linuxopjemac on 2010-05-12
It would be great if we could come up with some browser for PPC which allows us to watch H.264. That would be great. I am reading the whole internet about it lately.

---

### Post by shawnhcorey on 2010-05-12
The latest version of Firefox and Chrome will display H.264...if you have the codec.  However, the codec is propriety and, like Flash, not likely to be available for PowerPCs.

---

### Post by linuxopjemac on 2010-05-12
what about this then?
[http://tinycorelinux.com/forum/index.php?topic=5904.0](http://tinycorelinux.com/forum/index.php?topic=5904.0)

Midori is in the repository, just like the gstreamer things.

also nice
[http://mso-chronicles.blogspot.com/2010/03/html5-youtube-now-in-fedora.html](http://mso-chronicles.blogspot.com/2010/03/html5-youtube-now-in-fedora.html)

---

### Post by natgab on 2010-05-13
> **linuxopjemac said:**
> I did not install non-free video codecs. You migt want to add them yourself.
[http://debian-multimedia.org/](http://debian-multimedia.org/)

Linux Mint Debian runs pretty smooth. I don't have a solution for the lack of flash. I will start experimenting with H.264 in the future. I think a browser like midori with h.264 support would enable us to watch some video on youtube in an html5 applet I read somewhere. I will digg into this in the future, as x264 is the codec and it's in the debian multimedia repository.

LOL, maybe Steve Jobs has a point.  Flash won't work on his old Macs. Yeah, its the 8MB video that does not help.  

I had Ubuntu running on my G5 dual 1.8GHz w/ a 128MB ATI video card.  That was able to play most video on YouTube with the Firefox script from GreaseMonkey.  But of course did not help if you went to an all-Flash website.

I think if you go to the "light YouTube" or the mobile version, they have built-in non-flash videos.  That might help for you testing.

---

### Post by wbar2 on 2010-05-14
Hey I installed this on my old iBook. Everything works better than in Lubuntu (mostly power settings). I have the same nm-applet issue. For some reason, I just logged in and now have two!

But, the main issue is that I'm not getting any sound or sound options at all. I go to the GNOME ALSA mixer and there is nothing in the window. If I go to the Volume Control in the menu, it gives me this error:

```
No volume control GStreamer plugins and/or devices found.
```

Do you know how I might be able to get it to detect my soundcard (I think that's the issue)?

---

### Post by linuxopjemac on 2010-05-14
Please post questions regarding Mint in [this forum]("http://mac.linux.be/phpBB3/viewforum.php?f=16&sid=497b5a5528b3457c5a4c83d55536dfe9") next time. The forum you post in is Ubuntu.

I will copy and paste your question there.

---

### Post by B_Free on 2010-05-16
What advantages does Mint have over other distributions of Linux, other than being much more attractive?

---

### Post by linuxopjemac on 2010-05-17
Well, Mint for Intel processors is basically Ubuntu with all the codecs installed. My version of Mint LXDE PPC is Debian Lenny with all its goodness, a better looking GUI and the Mint tools. Mint has its own apt system, its own update programs and so on. If you like Debian Lenny with a lightweight desktop manager LXDE, you will certainly like Mint LXDE PPC. I am very happy with it, just like other people they told me. My personal experience is that is is faster than Lubuntu 10.04. And what I like about it, you don't have those bugs like automount which does not work, orinoco driver which does not seem to work in Ubuntu, things like that. Also suspend works out of the box. All in all a pretty looking, useful OS. It's not as updated as 10.04. it uses an older kernel and older programs. But the programs also work of course. I find the basics more important. It has to all just work. I don't need the newest Open Office for example. I hope I was clear enough.

---

### Post by B_Free on 2010-05-18
So where would you download this Mint Edition for the PPC? Is Firefox available?

---

### Post by linuxopjemac on 2010-05-18
In Debian Lenny I don't think you have firefox, but Iceweasel, which is basically the same as firefox.

There is not a real downloadable installer for Linux Mint LXDE (yet). You have to install some sort of Debian system (minimal installation). From there you can download an installer script to convert the system into Mint.

For a manual you go [here]("http://mac.linux.be/content/mint-lxde-debian-lenny-ppc").

If you insist on firefox, you can google, this is an example:
[http://deviceguru.com/adding-real-firefox-to-debian-lenny/](http://deviceguru.com/adding-real-firefox-to-debian-lenny/)

---

### Post by mikcarroll on 2010-12-30
Mint is too much hassle it's way easier to go for Xubuntu. More community=more support.

---

### Post by linuxopjemac on 2010-12-30
Sure, if I see who is always posting answers on PPC related issues...

---

### Post by claudiney on 2011-05-17
> **conal said:**
> Sure, I'm not near my G3 just now but I'll post it later.

Cheers

Conal

hi guys, sorry to bother, but i am trying to install ubuntu ppc11 on ilamp and i am getting a black screen...can you guys post the instructions for installation from the beggining?

thanks

ps, i am new to all this, but like to learn...

---

### Post by conal on 2011-05-18
Funny, the 11.04 live (desktop) cd just worked on my iLamp - wonder why yours didn't? Which version iLamp do you have (e.g. 1ghz?) and how much ram? Where do you get to when the screen is black? Past the first prompt where you can choose boot mode?

---

### Post by clarissa.w on 2011-06-02
Hi there

The webpage for [Linux Mint PowerPC]("http://mintppc.org") and [http://mac.linux.be]("http://mac.linux.be/") seem to be down.

Guess you are probably doing maintenance.

Could you respond when these sites are online again?

Thanks.

---

### Post by linuxopjemac on 2011-06-02
They are online again. Sorry for the inconvenience. Once in a while, software needs to be updated you know :)

---

### Post by linuxopjemac on 2011-06-03
We are having trouble with our server, it crashes very often lately. As of next week we will be running mintppc.org and mac.linux.be on a new server, which will hopefully be more stable. The old server only functions well as a fan...

---

