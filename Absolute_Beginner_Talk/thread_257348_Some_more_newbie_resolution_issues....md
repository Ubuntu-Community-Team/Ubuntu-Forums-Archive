---
title: "Some more newbie resolution issues..."
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by mon_m on 2006-09-14
So I recently installed the latest distro of ubuntu, and everything appears to be working great except for a small resolution issue I have with the computer.  I should probably say I haven't touched anything linux since redhat 7, and even then it was brief, so my linux knowledge is as limited as it can be.

Under System > Pref. > Screen Res., I'm only given the options 640x480 and 800x600.  Just trying to figure out why I can't get this thing up to 1024x768.

I'm running ubuntu 6.06.1 on an old gateway m305 laptop with integrated graphics, "Intel Corporation 82852/855GM"

Driver's seem good... and there's nothing in xorg.conf that caught my attention as to why it wouldnt work right, as all the entries display 1024x768.

I'm not so sure if this is a common problem or not, but any help at all would be greatly appreciated, thanks.

---

### Post by Najand on 2006-09-14
Try to run:
```

sudo dpkg-reconfigure xserver-xorg

```
in terminal.
Continue to hit "Next" until when you get to the place you can select different resolutions, select suitable ones.
(Key Binding: SPACE button, Move Using ARROW KEYS and go to the next page using ENTER.)

---

### Post by mon_m on 2006-09-14
Thank you for the help, but I tried running through it a couple times and the only thing that ended up changing was my max refresh rate, which I can now access 75hz instead of just 60hz.  I tried to disable every resolution except for 1024x768 and it still wouldnt change anything... Any other ideas?

---

### Post by Najand on 2006-09-14
Can you copy and paste your /etc/X11/xorg.conf here? I can help you edit it then.

---

### Post by mon_m on 2006-09-14
Sure thing:

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-50
	VertRefresh	43-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by Najand on 2006-09-14
Hmm, Sounds fine to me. It is set to be "1024x768", did you restart your computer after editting it?

---

### Post by mon_m on 2006-09-14
Yes, I tried a couple times actually :(

---

### Post by Najand on 2006-09-14
What about restarting your X using Ctrl+Alt+backspace?

---

### Post by mon_m on 2006-09-14
Nope, still nothing, the only thing that ever changes from editing the xorg.con file and restarting is just the refresh rate, used to be a max of 60, then 75, now its maxing out at 72.

---

### Post by Darklighter137 on 2006-09-14
What kind of a graphics card do you have?  I have a recent ATI card, and Ubuntu does the same thing to me when I run the LiveCD.

---

### Post by mon_m on 2006-09-14
> **Darklighter137 said:**
> What kind of a graphics card do you have?  I have a recent ATI card, and Ubuntu does the same thing to me when I run the LiveCD.

Graphics card is integrated, some intel chipset.  I'm running an old Gateway M305 laptop, so it really isn't anything special.  But...  if you're running the live CD, I was pretty sure it would definately do that to you since you can't reconfigure the xorg.conf file?

---

### Post by Najand on 2006-09-14
Hmm, actually reconfigure the xorg.conf file is possible in Live CD too, but next time you boot, you have to reconfigure it again. Don't you have any problem when using live CD?

---

### Post by mon_m on 2006-09-14
I had the current problem when I was using the LiveCD, so I thought that fulling installing Ubuntu would fix it.

---

### Post by Najand on 2006-09-14
Hmm, well... If you have a computer nothing installed on it, it worth doing that... But if you have windows, installing Linux on it will cause the Windows Boootloader to be overwritten by  Grub (Linux's Boot loader) and then it could not be fixed, removing Grub and restoring Windows Boot Loader is not an easy job. So it depends if you wanna risk or not.

---

### Post by mon_m on 2006-09-14
I already formatted the entire HD, mbr and all...  Ubuntu is the only thing on this HD, should I reformat again?

---

### Post by Najand on 2006-09-14
If you have reformatted it... Then try to install again and see what will happen? Installation of Ubuntu just takes 20 minues.

---

### Post by mon_m on 2006-09-14
Ok, then I'll get back to you in a bit, thanks for the help bud.

---

### Post by Najand on 2006-09-14
No problem. Inform me about your progress...

---

### Post by smokeysaysno on 2006-09-14
Hey, I had a similar problem with my screen and It was solved in [this thread]("http://www.ubuntuforums.org/showthread.php?t=252115").  Hope this works for you

j

---

### Post by missmoondog on 2006-09-14
> **smokeysaysno said:**
> Hey, I had a similar problem with my screen and It was solved in [this thread]("http://www.ubuntuforums.org/showthread.php?t=252115").  Hope this works for you

j

that was already tried several times, as stated by op. 

having same issue on a dell dimension desktop with integrated i845 chipset. have gone through the dpkg-reconfigure at least a dozen times. nothing has worked. now, all of a sudden, it works at the stting i want 1024x768@75hz

now, hoping it sticks for good this time as this is at least the third time i've had to go through these changes.

did just install the 915resolution thing also, as a last ditch effort.

---

### Post by Darklighter137 on 2006-09-14
Thanks. ^_^

---

### Post by bodhi.zazen on 2006-09-14
Try changing> Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82852/855GM Integrated Graphics Device"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection
EndSection

to ```
Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82852/855GM Integrated Graphics Device"
Monitor "Generic Monitor"
**DefaultDepth 16**
SubSection "Display"
Depth 1
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection
EndSection
```

Restart X (Ctrl-alt-Backspace

If that does not work, what monitor are you using?

---

### Post by mon_m on 2006-09-14
ok, sorry I took so long to get back to you guys about this...

but, I reinstalled ubuntu, same issue.  just thought about trying a couple other distro's to see if i'd get the same problem, and an old version of mandrake came up with the same thing, and the lastest distro of foresight actually scared me when my screen flashed 100 times a second until i shut the computer off in an attempt to run it at 1024x768.

ive tried changing the bit depth a couple times already, nothing there.  im pretty positive at this point its not a driver issue, but possibly because my monitor is coming up as 'generic lcd monitor?'

i cant find very much info on it, its a 14.1in monitor for the gateway m305 laptop.  only thing i can find right now is a part number: 7004923

---

### Post by mon_m on 2006-09-14
Anyone have any idea if this is most likely the issue?  Or is there something else I should be looking at?

---

### Post by bodhi.zazen on 2006-09-14
It appears your monitor is not supported by X.

Here are some links:

[X resolution on a Gateway M305](http://www.gatago.com/linux/debian/laptop/14612975.html#2AEfA-2jL-7@gated-at.bofh.it)

There is a commercial driver available:

[Linux X - GatewayM305](http://www.webservertalk.com/archive241-2005-12-1311074.html)

---

### Post by mon_m on 2006-09-14
> **bodhi.zazen said:**
> It appears your monitor is not supported by X.

Here are some links:

[X resolution on a Gateway M305](http://www.gatago.com/linux/debian/laptop/14612975.html#2AEfA-2jL-7@gated-at.bofh.it)

There is a commercial driver available:

[Linux X - GatewayM305](http://www.webservertalk.com/archive241-2005-12-1311074.html)


So my only choices really are either, wait for proper driver support, fork out $40 for a sub-par performance driver, or buy a new laptop? :(

---

### Post by bodhi.zazen on 2006-09-14
> **mon_m said:**
> So my only choices really are either, wait for proper driver support, fork out $40 for a sub-par performance driver, or buy a new laptop? :(

Or use an external monitor.

---

### Post by mon_m on 2006-09-15
sorry to trouble you again bodhi, but i *think* i may have found a driver that would solve my resolution issue, problem is, i havent the faintest idea of how to install this thing.

[http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=922&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=922&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

---

### Post by charles.g.moore on 2006-09-15
> **mon_m said:**
> sorry to trouble you again bodhi, but i *think* i may have found a driver that would solve my resolution issue, problem is, i havent the faintest idea of how to install this thing.

[http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=922&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=922&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)
save the file
tar -xvzf filename
cd into newdirectory
sudo ./configure
sudo make
sudo make install

Im pretty sure that will do it, everyone agree???

---

### Post by bodhi.zazen on 2006-09-15
Good work mon_m !!!! :twisted:

This is a rpm. You can try to use alien.

Install alien via synaptic or the command line.```
sudo apt-get update
sudo apt-get install aptitude
sudo aptitude install alien
```

Then, according to the readme you need to install after shutting down X:

```
sudo /etc/init.d/gdm stop
sudo alien -k dri-I915-v1.1-20041217.i386.rpm
sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm start
```

[-o<

---

### Post by mon_m on 2006-09-15
Hey bud, I'm having some trouble with this line of code right here...  cannot locate the file, I don't think it's anywhere inside the .tar.gz that I downloaded.

> **bodhi.zazen said:**
> 
```

sudo alien -k dri-I915-v1.1-20041217.i386.rpm

```


---

### Post by mon_m on 2006-09-15
ok, sorry, I figured it out.

I went ahead and followed your steps bodhi, but I still can't get the resolution up to 1024x768, is there anything else I had to do besides restarting x after typing in those commands?

---

### Post by bt224 on 2006-09-15
I went thru the same thing, and the x-org deal was worthless. I'm trying to find where/how I changed my res. There was some coding that involved gedit, I just have no idea what/where it was. Someone help us!

---

### Post by mon_m on 2006-09-15
> **bt224 said:**
> I went thru the same thing, and the x-org deal was worthless. I'm trying to find where/how I changed my res. There was some coding that involved gedit, I just have no idea what/where it was. Someone help us!

Just curious, so you already tried downloading the linux drivers from the intel site too?

Also, are you using the exact same chipset as me?  82852/855GM Intel Integrated

---

### Post by bt224 on 2006-09-15
I wish I could give a great answer to that, but I have no idea. However, my frustrations were the same, and the scenario is the same. Mine was not a driver issue, and was not resolved by the x-org setup. I actually used gedit to add some lines of code, and from then on everything worked great.

---

### Post by mon_m on 2006-09-15
Hmm, I guess it's very possible I have the exact same issue... but I probably just misdiagnosed it or something.  All I know is that x server has some sort of conflict/issue with my specific chipset at 1024x768

---

### Post by bt224 on 2006-09-15
If need be, I can reboot into Windows and find that link. If you cannot get it to work, e-mail my gmail. It's bthompson224. I'll find it on there somewhere, altho I hate going back,

---

### Post by bodhi.zazen on 2006-09-15
> **mon_m said:**
> ok, sorry, I figured it out.

I went ahead and followed your steps bodhi, but I still can't get the resolution up to 1024x768, is there anything else I had to do besides restarting x after typing in those commands?

[list=number][*]Again,starting with the obvious, reboot.
[*]If that fails please re-post your xorg.conf (/etc/X11/xorg.conf).[/list]

---

### Post by mon_m on 2006-09-15
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	VideoRam	128000
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by bodhi.zazen on 2006-09-16
Try changing> Section "Device"
Identifier "Intel Corporation 82852/855GM Integrated Graphics Device"
Driver "i810"
BusID "PCI:0:2:0"
VideoRam 128000
EndSection

To
```
Section "Device"
Identifier "Intel Corporation 82852/855GM Integrated Graphics Device"
Driver "**i910**"
BusID "PCI:0:2:0"
VideoRam 128000
EndSection
```

Re-start X....

---

### Post by bodhi.zazen on 2006-09-16
You could also try SUSE. There are claims open suse has support for your configuration.

---

### Post by mon_m on 2006-09-16
Sorry, this is a really silly question, but I'm not sure how to just edit xorg.conf since it comes up with the whole insuffient permissions and what not.

---

### Post by bodhi.zazen on 2006-09-16
> **mon_m said:**
> Sorry, this is a really silly question, but I'm not sure how to just edit xorg.conf since it comes up with the whole insuffient permissions and what not.

Sorry....

```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by mon_m on 2006-09-16
Oops, sorry about that, didn't get back to you in time.

I figured out how to edit it, but it crashed x server when I tried to restart... so, I guess the last thing I can really do is wait for bt224 to send me that e-mail about altering some files.

If that doesn't work out, I guess I'll have to take up your idea about switching to SuSe :(

But either way, thank you for all the time and help bodhi, the ubuntu community is definately awesome. :)

---

### Post by bodhi.zazen on 2006-09-16
Best of luck....

I hope you learned something about Linux and I am sorry I was unable to get you up and running.

To restore your xorg.conf from the cli:

Log in.
```
sudo nano /etc/X11/xorg.conf
```

change back to "i810"

To exit type Ctrl-X, "Y" to save.

Re-start X; I assume you know how to do that !

---

### Post by mon_m on 2006-09-30
So, I've been scratching my head for the last two weeks about this problem... and I've come to the conclusion that the only way I can get around this is to buy a new laptop.

I really didn't feel a new thread was needed for this question, but  I skimmed the Ubuntu forums real quick in search of a thread that covered known hardware issues.

I couldn't find any thread like it, so I'm just curious if one exists that I don't know about.  Basically, I'm just looking for a thread on here that covers all known hardware issues when running Ubuntu - just to make sure that I don't have a similar resolution problem or anything with my new laptop.

---

