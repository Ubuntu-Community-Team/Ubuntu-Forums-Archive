---
title: "problem with file permissions"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by keef247 on 2007-03-26
was trying to use a custom modeline in xorg.conf... well i deleted the line and i was playing with folder permissions before i think... so does this mean i've allowed my home to be accessed by any user?? i have no idea i just want to know how to fix it!

heres the error.

User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.

what have i done and how do i fix it!!!!
thanks!

---

### Post by annda on 2007-03-26
so, you managed to get your own home directory to be inaccessible to you...

boot into recovery mode, this will give you root privileges.

use this guide to set permissions straight:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

use chown and chmod on /home as specified in the error messages.

---

### Post by Arby on 2007-03-26
OK the error message is telling you what permissions that file 'should' have. The first thing is to find out what permissions it actually has at the moment. In a terminal try this command from within you're home directory ```
ls -la | grep dmrc
``` this will find that file in your home directory and show you it's permissions. On my system that command returns ```
**-rw-------**  1 richard richard   24 2007-03-22 10:34 .dmrc
``` The part in bold is the files permissions. r=read, w=write. 

try that command and see what the permissions of your .dmrc file currently are

Arby

---

### Post by keef247 on 2007-03-26
> **Arby said:**
> OK the error message is telling you what permissions that file 'should' have. The first thing is to find out what permissions it actually has at the moment. In a terminal try this command from within you're home directory ```
ls -la | grep dmrc
``` this will find that file in your home directory and show you it's permissions. On my system that command returns ```
**-rw-------**  1 richard richard   24 2007-03-22 10:34 .dmrc
``` The part in bold is the files permissions. r=read, w=write. 

try that command and see what the permissions of your .dmrc file currently are

Arby

got this mate

root@mypc:~# ls -la | grep dmrc
-rw-------  1 dave dave        26 2007-03-24 01:38 .dmrc

now what

---

### Post by keef247 on 2007-03-26
Bumppppp

---

### Post by keef247 on 2007-03-26
help me in here...
[http://ubuntuforums.org/showthread.php?p=2358422#post2358422](http://ubuntuforums.org/showthread.php?p=2358422#post2358422)
PLEASE!

---

### Post by taurus on 2007-03-26
```
ls -la /home
ls -la /home/dave
```

---

### Post by keef247 on 2007-03-26
root@mypc:~# ls -la /home
total 16
drwxr-xr-x  4 root   root   4096 2007-03-26 23:29 .
drwxr-xr-x 22 root   root   4096 2007-03-26 22:40 ..
drwxrwxrwx 48 dave dave 4096 2007-03-27 01:20 dave
drwxr-xr-x  3 root   root   4096 2007-03-26 23:29 davel

---

### Post by aysiu on 2007-03-26
Can you do the second part, too? ```
ls -la /home/dave
```

---

### Post by keef247 on 2007-03-26
```
dave@BIG-SHELL:~$ ls -la /home/dave
total 769752
drwxrwxrwx 48 dave dave      4096 2007-03-27 01:53 .
drwxr-xr-x  4 dave root        4096 2007-03-26 23:29 ..
-rw-r--r--  1 dave root           0 2007-03-24 05:34 1
drwxr-xr-x  3 dave dave      4096 2007-03-24 02:31 101MEDIA
drwxr-xr-x  2 dave root        4096 2007-03-24 05:41 .automatix
drwxr-xr-x  9 dave dave      4096 2007-03-26 22:20 .azureus
drwxr-xr-x 10 dave dave      4096 2007-03-27 00:45 Azureus Downloads
-rw-------  1 dave dave      7638 2007-03-27 00:53 .bash_history
-rw-r--r--  1 dave dave       220 2007-03-24 01:34 .bash_logout
-rw-r--r--  1 dave dave       414 2007-03-24 01:34 .bash_profile
-rw-r--r--  1 dave dave      2227 2007-03-24 01:34 .bashrc
drwx------  6 dave dave      4096 2007-03-25 11:56 .BitTornado
drwxr-xr-x  8 dave dave      4096 2007-03-25 15:26 .cedega
-rw-r--r--  1 dave dave      1070 2007-03-25 21:58 .cedegarc
drwxr-xr-x  4 dave dave      4096 2007-03-25 11:39 .clamtk
drwx------  4 dave dave      4096 2007-03-25 14:34 .config
-rw-------  1 dave dave 237780992 2007-03-26 04:59 core.5163
drwxrwxrwx  2 dave dave      4096 2007-03-26 07:00 Desktop
drwxr-xr-x  8 dave dave      4096 2007-03-27 00:17 dls
-rw-------  1 dave dave        26 2007-03-24 01:38 .dmrc
-rw-------  1 dave dave        16 2007-03-24 01:38 .esd_auth
lrwxrwxrwx  1 dave dave        26 2007-03-24 01:34 Examples -> /usr/share/example-content
-rw-r--r--  1 dave root           0 2007-03-24 04:10 .fonts.cache-1
drwxr-xr-x  4 dave dave      4096 2007-03-26 03:40 .frostwire
drwx------  5 dave dave      4096 2007-03-27 01:19 .gaim
drwxr-xr-x  3 dave root        4096 2007-03-26 22:49 games
drwx------  4 dave dave      4096 2007-03-27 01:53 .gconf
drwx------  2 dave dave      4096 2007-03-27 02:07 .gconfd
drwxr-xr-x  7 dave dave      4096 2007-03-25 13:13 .gdesklets
drwxr-xr-x 21 dave dave      4096 2007-03-26 03:32 .gimp-2.2
-rw-r-----  1 dave dave         0 2007-03-26 23:30 .gksu.lock
drwxr-xr-x  3 dave dave      4096 2007-03-24 01:40 .gnome
drwx------ 13 dave dave      4096 2007-03-26 21:14 .gnome2
drwx------  2 dave dave      4096 2007-03-24 01:38 .gnome2_private
drwxr-----  3 dave dave      4096 2007-03-25 15:26 .grapevine
drwxr-xr-x  2 dave dave      4096 2007-03-25 11:26 .gstreamer-0.10
-rw-r--r--  1 dave dave       143 2007-03-25 04:13 .gtkrc-1.2-gnome2
-rw-------  1 dave dave      1322 2007-03-27 01:53 .ICEauthority
drwxr-xr-x  2 dave dave      4096 2007-03-25 04:13 .icons
drwxr-xr-x  2 dave dave      4096 2007-03-26 07:07 Incomplete
drwxr-xr-x  3 dave dave      4096 2007-03-25 22:14 .java
drwxr-xr-x  3 dave root        4096 2007-03-25 14:34 .local
drwx------  3 dave dave      4096 2007-03-24 03:00 .macromedia
drwx------  3 dave dave      4096 2007-03-24 01:38 .metacity
-rw-r--r--  1 dave dave       295 2007-03-25 13:50 modeline
drwx------  5 dave dave      4096 2007-03-26 02:19 .mozilla
drwx------  3 dave dave      4096 2007-03-24 02:27 .mozilla-thunderbird
drwxr-xr-x  2 dave dave      4096 2007-03-24 05:28 .mplayer
drwxr-xr-x  3 dave dave      4096 2007-03-26 05:32 .nautilus
-rw-r--r--  1 dave dave     92937 2007-03-24 20:40 park.jpg
drwxr-xr-x  2 dave dave      4096 2007-03-26 02:08 .qt
drwxr-xr-x  4 dave root        4096 2007-03-26 23:14 .quake4
-rw-------  1 dave dave     68154 2007-03-26 21:14 .recently-used
-rw-r--r--  1 dave dave     30010 2007-03-27 01:20 .recently-used.xbel
-rw-------  1 dave root        1024 2007-03-25 06:53 .rnd
drwxr-xr-x  2 dave dave      4096 2007-03-26 06:21 Shared
drwx------  3 dave dave      4096 2007-03-27 00:28 .Skype
-rw-r--r--  1 dave dave        14 2007-03-26 05:06 steam_21.mst
-rw-r--r--  1 dave dave    551989 2007-03-26 05:06 steam_21.pkg
-rw-r--r--  1 dave dave    720200 2007-03-25 14:32 SteamInstaller.exe
-rw-r--r--  1 dave dave   1395712 2007-03-25 14:27 SteamInstall.msi
-rwxr-xr-x  1 dave dave   1269760 2007-03-26 05:06 SteamNew.exe
-rw-r--r--  1 dave dave         0 2007-03-24 01:40 .sudo_as_admin_successful
drwx------  3 dave dave      4096 2007-03-25 15:42 .supertux2
-rw-r--r--  1 dave dave    383140 2007-03-25 14:23 tahoma.ttf
drwxr-xr-x  2 dave dave      4096 2007-03-25 04:13 .themes
drwx------  4 dave dave      4096 2007-03-24 02:31 .thumbnails
drwxr-xr-x  2 dave dave      4096 2007-03-26 03:47 torrents
lrwxrwxrwx  1 dave dave        44 2007-03-25 15:26 TransGaming_Drive -> /home/dave/.cedega/Dot TransGaming/c_drive
drwxr-xr-x  3 dave dave      4096 2007-03-25 15:26 .transgaming_global
drwx------  2 dave dave      4096 2007-03-26 07:06 .Trash
-rw-r--r--  1 dave dave   6974002 2007-03-27 00:18 unreal.tournament_436-multilanguage.goty.run
-rw-r--r--  1 dave dave      2344 2007-03-27 00:15 unreal.tournament_436-multilanguage.goty.run.torrent
drwx------  2 dave dave      4096 2007-03-24 02:16 .update-notifier
-rw-r--r--  1 dave dave     18668 2007-03-24 02:10 us.png
-rw-r--r--  1 dave dave 649629696 2007-03-26 16:44 UTGOTY.iso
-rwxr-xr-x  1 dave dave   6225010 2007-03-25 22:47 ut-install-436.run
drwxrwxrwx  4 dave dave      4096 2007-03-27 01:30 .wine
-rw-------  1 dave dave       120 2007-03-25 14:11 .Xauthority
drwxr-xr-x  2 dave dave      4096 2007-03-24 04:56 .xine
drwxr-xr-x  4 dave dave      4096 2007-03-25 12:49 .xmms
-rw-r--r--  1 dave root         163 2007-03-25 12:18 .xorg-edit
-rw-r--r--  1 dave dave      1120 2007-03-27 01:54 .xsession-errors
```

---

### Post by aysiu on 2007-03-26
I'm not sure about all the other stuff, but .dmrc and .Xauthority (the usual culprits, especially the first one, given the error you got) look good to me in terms of ownership and permissions.

.xorg-edit looks a little fishy. The owner is *dave*, but the group is *root*. And you did say something about having edited the Xorg file earlier, right? I don't even have a .xorg-edit file in my home directory.

I'd say first try making sure you own everything in there: ```
sudo chown -R dave:dave /home/dave
``` Log out and log back in again. See if the problem is fixed.

If not, try just remove .xorg-edit altogether. I don't think that file should be there.

---

### Post by taurus on 2007-03-26
Also try

```
sudo chmod 755 /home/dave
```

---

### Post by keef247 on 2007-03-26
AMAZING your such a great help.it worked:D
but... what was the xorg-edit? can you paste me where it is or alternatively paste me the code with it removed...-that would be a great help! also do you know how i can fix my bootup resolution as this is how this all went wrong.basically my dell monitor a dh1226h apparently should do 1600x1200 @75hz max... it doesn't it only likes that in windows... so i have to run 70hz on ubuntu.. i then installed envy and automated ati drivers ... after rebooting and trying to sort the res out i only had the 75hz/60hz option... this is no good (currently having to use 60hz) because whenever i exit a wine app or bootup etc etc it goes back to 75hz and its half way across the screen aswell.
so how do i sort it? tried modeline well sorta (if u cud make me a xorg.conf out of the one below i could then add it and sort it out.as i've provided my monitor.i just can't get it to work. i want 1600x1200@70hz default for everything please! bootup/login/default basically!
please help me i've tried and tried so hard:(

Oh AND!!! can you check my 3d acel and ati drivers are installed properly... as i think they are but someone mentioned the fglx ? think thats what its called wasn't setup right in xorg it was set as ATI? envy did it all so i left it as it is? i've played css and cs1.6 in wine on opengl so far. havent tried direct 3d. cedega told me i'd failed 3d acel and oss tests...

EDIT: just ran cedega's setup tests... still saying 3d acel isnt working but alsa and oss now do:)


```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	FontPath     "/usr/share/fonts/X11/misc"
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
	Identifier   "DELL D1226H"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Monitor    "DELL D1226H"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
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

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection


```

---

### Post by aysiu on 2007-03-26
Unfortunately, I don't know a whole lot about ATI or refresh rates.

Just to clarify, though, for someone who *can* help you with this--are you talking about the resolution *before* you get to the login screen (you mentioned something about "bootup resolution"), or the resolution *after* you log in? Or both?

If you don't get any new replies, as I told you my PM, you can bump your thread every day or two. In the meantime, one of [these links](http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+ati+howto&btnG=Google+Search) may help you.

---

### Post by keef247 on 2007-03-26
i mean where it says login...
cheers will check.where is the bit you said doesn't seem right.the xorg-edit bit?

---

### Post by aysiu on 2007-03-26
> **keef247 said:**
> i mean where it says login...
cheers will check.where is the bit you said doesn't seem right.the xorg-edit bit?
I don't really have any experience here, but I found [this thread](http://ubuntuforums.org/showthread.php?p=2152831#post2152831) through a search, and you may find it helpful.

My points about .xorg-edit:
1. I didn't have that file in my /home directory, so it's clearly not an essential file
2. It was in the group *root*, but everything in your home directory should be in group *dave* with owner *dave*

---

### Post by keef247 on 2007-03-26
ok mate once again cheers for everything.i shall have a peruse...
i'll update the thread should i require any help.
cheers(Y)

---

