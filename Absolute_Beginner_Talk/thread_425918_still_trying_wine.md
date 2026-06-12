---
title: "still trying wine"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by Psyclown on 2007-04-28
so its apperent that im becoming quite a regular on here. anyway... so im trying to install apps via wine... im running this experiment with itunes.. i run the exe and it says its insatlled.. but i have no idae where or how to get into it... its not in apps>wine>programs>itunes. and im stumped to find it anywhere else... any ideas?

---

### Post by Nythain on 2007-04-28
`/.wine/drive_c/Program\ Files/itunes possibly... in a nutshell in the hidden directory of ./wine in your home directory there should be another folder called drive_c or c_drive or whatever... then from there it should start to look a lot like windows

---

### Post by Psyclown on 2007-04-28
how do i show hidden directories.. cause like... wine isnt in my / folder

---

### Post by Nythain on 2007-04-28
in the terminal you and ls -a and it will show hidden directories (the ones starting with a .)... you can cd into then like typing cd .wine from your home directory... as far as getting your file manager/browser to show hidden files, it depends on wich one you use really... and .wine is in your HOME directory (/home/whateveruseryouare) usually represented with the ~ key (wich is what i meant to type in my original post but didnt hit shift), not root (/)

---

### Post by Psyclown on 2007-04-28
i have no .wine in my home directory... that a bad thing? i installed it fine and its on my apps

---

### Post by Psyclown on 2007-04-28
i however do hav a link to shell script enttled wine in my home directory

---

### Post by Nythain on 2007-04-28
try running winecfg in terminall, then seeing if you have a .wine directory in your /home/you... if not im at a loss, wine usually (note, ALWAY for me) sets up its windows file structure at ~/.wine/drive_c/ where it procedes to install any windows software you use it to install... like in my case /home/rune/.wine/drive_c/Program\ Files/Diablo\ II is where it installed diablo 2 at on my machine

---

### Post by Psyclown on 2007-04-28
haha heres me failing at wine

Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
danny@danny-desktop:/$ wine itunes.exe
wine: could not load L"c:\\windows\\system32\\itunes.exe": Module not found
danny@danny-desktop:/$ wine c:\\
wine: could not load L"C:\\.": Invalid handle
danny@danny-desktop:/$ wine c:\\programfiles\itunes.exe
wine: cannot find 'c:\programfilesitunes.exe'
danny@danny-desktop:/$ C:\\programfiles\itunes.exe
bash: C:\programfilesitunes.exe: command not found
danny@danny-desktop:/$ C:\programfiles/itunes.exe
bash: C:programfiles/itunes.exe: No such file or directory
danny@danny-desktop:/$ wine programfiles/itunes.exe
wine: cannot find 'programfiles/itunes.exe'
danny@danny-desktop:/$ wine itunes.exe
wine: could not load L"c:\\windows\\system32\\itunes.exe": Module not found
danny@danny-desktop:/$ wine itunes
wine: could not load L"c:\\windows\\system32\\itunes.exe": Module not found
danny@danny-desktop:/$
danny@danny-desktop:/$ /ihateyou
bash: /ihateyou: No such file or directory

---

### Post by Nythain on 2007-04-28
ok, a few of those seemed like they were trying... the module not found ones... are you trying to INSTALL itunes or run itunes... (guess now woudl be a good time to point out that i dont think itunes works very well under wine anyways, but i have check on newer versions)...

if trying to install itunes, cd to where you have the install exe located and type wine *whatever the exe is named*.exe

if trying to run itunes try typing in terminal, wine ~/.wine/drive_c/Program\ Files/itunes/itunes.exe and see what it says... the path might be wring, im not sure where itunes installs itself by default

---

### Post by Psyclown on 2007-04-28
danny@danny-desktop:/$ ~/.wine/drive_c/Program\ Files/itunes/itunes.exe
bash: /home/danny/.wine/drive_c/Program Files/itunes/itunes.exe: No such file or directory
danny@danny-desktop:/$ ~/.wine
bash: /home/danny/.wine: is a directory
danny@danny-desktop:/$ ~/.wine/drive_c
bash: /home/danny/.wine/drive_c: is a directory
danny@danny-desktop:/$ ~/.wine/drive_c/Program\Files
bash: /home/danny/.wine/drive_c/ProgramFiles: No such file or directory
danny@danny-desktop:/$ ~/.wine/drive.c/Program\ Files
bash: /home/danny/.wine/drive.c/Program Files: No such file or directory
danny@danny-desktop:/$ ~/.wine/drive.c/ProgramFiles
bash: /home/danny/.wine/drive.c/ProgramFiles: No such file or directory
danny@danny-desktop:/$

---

### Post by Psyclown on 2007-04-28
danny@danny-desktop:/$ ~/.wine/drive_c/Program\ Files/itunes/itunes.exe
bash: /home/danny/.wine/drive_c/Program Files/itunes/itunes.exe: No such file or directory
danny@danny-desktop:/$ ~/.wine
bash: /home/danny/.wine: is a directory
danny@danny-desktop:/$ ~/.wine/drive_c
bash: /home/danny/.wine/drive_c: is a directory
danny@danny-desktop:/$ ~/.wine/drive_c/Program\Files
bash: /home/danny/.wine/drive_c/ProgramFiles: No such file or directory
danny@danny-desktop:/$ ~/.wine/drive.c/Program\ Files
bash: /home/danny/.wine/drive.c/Program Files: No such file or directory
danny@danny-desktop:/$ ~/.wine/drive.c/ProgramFiles
bash: /home/danny/.wine/drive.c/ProgramFiles: No such file or directory
danny@danny-desktop:/$
  headache

---

### Post by Nythain on 2007-04-28
yeah, you are forgetting to throw a command in front of those... try type
```

cd ~/.wine/drive_c/

```
if it lets you there then type
```

ls -a

```
and tell me what it says... if it doesnt let you got to ~/.wine/drive_c, type
```

winecfg

```
basically the defaults should be fine for now, click apply or ok or whatever to close it and try
```

cd ~/.wine/drive_c

```
again and let me know if it exists then

---

### Post by Psyclown on 2007-04-28
[email]danny@danny-desktop:~/.wine[/email]/drive_c$ ls -a
.  ..  Program Files  windows

theres that but when i try to cd to it...

[email]danny@danny-desktop:~/.wine[/email]/drive_c$ cd ProgramFiles
bash: cd: ProgramFiles: No such file or directory
[email]danny@danny-desktop:~/.wine[/email]/drive_c$ cd program
bash: cd: program: No such file or directory
[email]danny@danny-desktop:~/.wine[/email]/drive_c$ cd programfiles
bash: cd: programfiles: No such file or directory
[email]danny@danny-desktop:~/.wine[/email]/drive_c$ cd Program Files
bash: cd: Program: No such file or directory
[email]danny@danny-desktop:~/.wine[/email]/drive_c$ cd .Program Files
bash: cd: .Program: No such file or directory
[email]danny@danny-desktop:~/.wine[/email]/drive_c$

---

### Post by Nythain on 2007-04-28
thats because linux doesnt default recognize spaces... and caps is VERY important too... this isnt windows anymore... you can use the \ to let linux know there's gonna be a space ahead like this
```

cd Program\ Files

```
when doing that, remember, the \ just lets linux know a space is coming up, it doesnt replace the space, that sill needs to be there

but at least we are on the right track with wine being where its supposed to be, and everything set up so far so good... do you remember the windows path of where itunes installed itself to???

---

### Post by Campingman on 2007-04-28
Why dont you install nautilus-open-terminal (in repositories).  You can then navigate to the folder right click and open terminal in the location you are.  Much easier than the cd command

---

### Post by Psyclown on 2007-04-28
ugh i got it./... no this [email]danny@danny-desktop:~/.wine[/email]/drive_c/Program Files/Itunes$ wine iTunes.exe
fixme:htmlhelp:HtmlHelpW HH case HH_INITIALIZE not handled.
err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
err:ddraw:DDRAW_Create Couldn't load WineD3D - OpenGL libs not present?
fixme:font:CreateScalableFontResourceA (0,"c:\\windows\\QTFont.for","c:\\windows\\QTFont.qfn",(null)): stub
fixme:font:WineEngAddFontResourceEx :stub
fixme:wintrust:WinVerifyTrust 0xffffffff {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x33eea0
fixme:wintrust:WTHelperProvDataFromStateData (nil)
fixme:wintrust:WinVerifyTrust 0xffffffff {00aac56b-cd44-11d0-8cc2-00c04fc295ee} 0x33eea0

---

### Post by Nythain on 2007-04-28
ok, first error is easily fixable, run winecfg, and in the audio section select emulation like it says i guess...

next problem i see is an directdraw/opengl issue... what video card are you running and do you have the correct drivers installed...

so far at least you've learned how to find and navigate to hidden files/directories... and correct (although kind of old school) get linux to recognize spaces...

and last but not least, at least we found out that you do have wine and itunes installed correctly... 

what does your xorg.conf look like??? we're gonna have to disect that during the whole video card drivers problem

---

### Post by Campingman on 2007-04-28
Hi Psyclown

Looks like it is telling you to run the wine config and set the sound and graphics options, have you seen these links on getting itunes to work with wine, may be of some help
[http://frankscorner.org/index.php?p=itunes6](http://frankscorner.org/index.php?p=itunes6)
[http://www.linuxforums.org/forum/wine/50229-working-wine-itunes.html](http://www.linuxforums.org/forum/wine/50229-working-wine-itunes.html)

---

### Post by Psyclown on 2007-04-28
ya see thats my problem... i do have somthing installed on my videocard because its running in a higher res than 640 wich was the only res it gave me before i tried to install drivers.. the second problem is that my second video card doesnt work.. its refresh rate may be to big for this monitor so im running the onboard video card

secondly.. [email]danny@danny-desktop:~/.wine[/email]/drive_c/Program Files/Itunes$ xorg.conf
bash: xorg.conf: command not found

---

### Post by Nythain on 2007-04-28
ok, xorg.conf is a configuration file for xserver... wich is pretty much your pretty graphical interface for linux... its located at /etc/X11/xorg.conf and is usually opend up with your text editor of preference... such as
```

sudo gedit /etc/X11/xorg.conf

```

but you should first try reading those two links posted, as they can probably provide you with more help now that i can since i havent ever run itunes with wine on linux... hell i havent ever run itunes period, so beyond getting wine installed and set up, im not gonna be much more help

---

### Post by Psyclown on 2007-04-28
so waht should i do with that thingy?

---

### Post by Psyclown on 2007-04-28
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Compaq MV740"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200"
	Driver      "fglr"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:5:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Xpress 200"
	Monitor    "Compaq MV740"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

---

### Post by iPirates on 2007-04-28
in ubuntu, you can just hit "ctrl h" to view hidden folders.
(kubuntu, click view, show hidden items).

not that it helps you anymore in your scenario, just thought i'd add that.

I'm at a complete loss when it comes to using wine, i'm still experimenting.

maybe try installing winetools?  it seems to make things easier for installing windows apps.

---

### Post by Psyclown on 2007-04-28
i would be happy to install winetools if i knew how

---

### Post by Nythain on 2007-04-28
ok, sorry to have abandond you but i need to get some sleep... have you read over those two links posted earlier, like i said they might be able to help more than me at this point.

from what i gather most of winetools got implemented into the more recent versions of wine, so you shouldnt really have to deal with installing it, but i dont know since i havent ever had to jack with them....

if anyone else has experience with itunes, or patience to help take over where im leaving off... thank you in advance... i must sleep now... sorry i couldnt help more

---

### Post by Campingman on 2007-04-28
What version of itunes are you trying to install? according to the wine application database people are having big problems getting version7 to run.  It does install though.
This page gives advice on which different versions (you have probably looked at this by now though). 

[http://appdb.winehq.org/appview.php?iAppId=1347](http://appdb.winehq.org/appview.php?iAppId=1347)
[http://appdb.winehq.org/appview.php?iVersionId=5774](http://appdb.winehq.org/appview.php?iVersionId=5774)

Have you managed to run wineconfig succesfully?

---

