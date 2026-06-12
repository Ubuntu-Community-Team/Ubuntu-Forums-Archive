---
title: "Working iMac G3 8.04 with multimedia and iplayer"
date: 2009-02-02
forum: Apple Hardware Users
---

### Post by SlowerLearner on 2009-02-02
Installation of Ubuntu 8.04 on iMac G3 (slot) 400Mhz 10Gb HDD 512Mb RAM (upgraded)

The installation guide below has been designed to be as comprehensive as possible.  It is long winded, but as a complete newbie less than a year ago, I understand the need for more than 'just edit the xxxx file'.

Most of the ideas are not mine, so I have tried to remember where I got the info from and list the addresses.  This post is useful, however, because it does contain information not contained in the PowerPC Known Issues page ([https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)) or other threads I have seen, and it collects together information posted in a variety of places to complete a basic set-up, following installation.  

I am a not an expert, so there may be a number of items below that the better informed could  improve, but the actions carried out below have worked on my machine.  Before  reading this post, please read the PowerPC Known Issues wiki, as my solution  differs, and clearly other iMac G3s have responded differently to the installation of 8.04.

[www.ubuntu.com](www.ubuntu.com) and click on Support and then documentation to see the official Ubuntu 8.04 info.

The first useful thread is Easy Way to Install Ubuntu on iMac G3 ([http://ubuntuforums.org/showthread.php?t=405934](http://ubuntuforums.org/showthread.php?t=405934)).  The instructions contained here are very useful and form the basis of the initial installation.  There is also information available concerning an earlier version of Ubuntu at ([https://help.ubuntu.com/community/Installation/PowerPC](https://help.ubuntu.com/community/Installation/PowerPC)).  I carried out the following:

Used this page [http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/) to select Mac (PowerPC) and IBM-PPC (POWER5) alternate install CD.

I used the NTI CD & DVD make on my XP machine to burn an iso image of the resulting file.  To do this select 'Data', 'Data CD', 'File', 'Create Disc from ISO Disc Image File'.  Select your Ubuntu 8.04 download and burn at 4x speed for best results.

Changed the keyboard for a standard wired (Microsoft) English (UK) keyboard and a standard wired mouse (Asda own brand), both USB. Booted the iMac while holding down the 'c' key.  This enables you to boot from  the cd.  Plugged in my ethernet cable.  (Necessary for the post install activity).  At the prompt, pressed the tab key to show all the boot options.  You will see 'cli-powerpc' as one of the options.  Type cli-powerpc at the prompt.  The installation process should now commence.

At the appropriate points in the process carry out the following.  Just press return to move to the next item, or use tab or the cursor keys to move the cursor to the <continue> option.  There is also a <back> option:

Choose the 'entire guided' hard drive partition option, which will format and partition your hard drive ready to accept the new operating system (OS).

Choose a name for the computer.  Ubuntu is chosen by default, but you can change it if you want to.

Choose a username and password of your own making.

Enter proxy details.  If you are connecting through your own router at home, then you almost certainly won't have a proxy, so leave this blank and just press return.

Set clocks to UTC.

If the installation programme claims not to see the cd-rom press Alt F2 simultaneously and at the resulting prompt type:

```
modprobe ide-scsi
```

Return to the installation process by typing Alt F1.  You may need to go round the cd-rom detection process a second time.

If you make a mistake you can go back, and if it all goes horribly wrong, or you believe that you have made wrong choices, but don't know how to correct them, then you can just start again.  You aren't limited to the number of attempts you can make, so don't worry about making the wrong choice.

When the installation is finished the disc will be ejected, and you will be asked to press return to reboot the system.

As the system reboots, you will see 2 successive boot prompts.  Both will default to certain values.  At the first prompt you get the option to either boot from the cd, by typing c (ie start the installation again), or l to boot the installed system.  If you do nothing, the system will boot from the installed system.  At the second prompt, you have a number of options, some of which we will use later.  Again, if you leave it blank, it will default to the boot configuration set during the installation process.

When the system is rebooted you will need to login using the username and password you specifed.  Press return after each entry.  You will notice that no characters appear when you type your password.  Now type the following and then hit the return key after each line.  Enter your password when required, and type y followed by enter if you are invited to download more software.  Some of the processes below may take some time, depending on your download speed, RAM, etc.  It is beneficial to get your system up to date before installing the desktop graphics:

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

```
sudo reboot
```

The system will now reboot.  Login again.

Type the following:

```
sudo apt-get dist-upgrade
```

```
sudo reboot
```

The system will now reboot.  Login again.

Type the following, which installs the X server, required for the visuals, ie the desktop:

```
sudo apt-get install xorg xserver-xorg-dev
```

sudo reboot```

```

Following the reboot and login, type:

```
sudo apt-get install ubuntu-desktop
```

The desktop that you are installing is called Gnome.  If you are more adventurous you can investigate how to install a different desktop.

```
sudo reboot
```

You may now find that as the system reboots it will pass through the 2 boot prompts and arrive at a screen that states 'Loading.............', followed by a sudden shutdown.  The solution is not too difficult.

Reboot the machine by switching it off and then on again at the button.  At the second boot prompt, type:

```
Linux nosplash video=ofonly nofb
```

(You may not need all these, but that's not important right now).  The nofb item removes the framebuffer.  My original video problem appears to have been that the system could not find a valid framebuffer.  I found this out by typing startx at the prompt and reading the resulting error messages.  I found framebuffer information here [https://wiki.ubuntu.com/FrameBuffer](https://wiki.ubuntu.com/FrameBuffer)

Once your system reboots, type:

```
sudo nano /etc/yaboot.conf
```

You are now editing the boot configuration that the system defaults to at the second boot prompt.  Use the cursor keys to move about the file.  There are 2 lines in the file that start with the word 'append'.  To the end of each of these lines add the words:

```
nosplash nofb
```

The lines should now look like this:

```
append="quiet nosplash nofb"
```

Press the ctrl key and the letter o simultaneously

Press the return key

Press the ctrl key and the letter x simultaneously

Type the following to ensure that the correct boot config is used for subsequent boots:

```
sudo ybin -v
```

When the prompt reappears, type:

```
sudo reboot
```

The machine should now reboot without intervention.  If it doesn't, you may need other boot items such as video=ofonly, but my knowledge runs out at this point.

Once rebooted we need to finish the install by editing the /etc/X11/xorg.conf file.  (Note that the first 'X' in the file name is a capital letter).  In order to obtain something close to the correct entries for this file I first installed Ubuntu 6.06.1 on my iMac and copied the resulting xorg.conf file.  I have used the file in its entirety, and by a process of elimination removed the modules that either don't exist or don't work.  To remove a line from a file in Linux you only need to add a # at the start of the line.  This is a useful feature, as it allows you to restore lines later, if you have made a mistake by removing them.  To begin with, save your existing xorg.conf file, in case my instructions do not work and you wish to work with the original file.  Type:

```
sudo nano /etc/X11/xorg.conf
```

ctrl o

Now edit the file name to, say

```
/etc/X11/xorg.conf2
```

return

ctrl x

I have attached my own config file.  Those in the know will almost certainly have a better way of getting it onto your iMac, but this method worked for me:

Burn the file to cd as a text file.  The infromation on cdroms comes from here [http://ubuntuforums.org/archive/index.php/t-807976.html](http://ubuntuforums.org/archive/index.php/t-807976.html).  Type:

```
cd /media/
```

```
ls
```

You should now see all the media, ie cdrom0 or cdrom.  As appropriate, type:

```
sudo mount /media/cdrom#
```

(Where hash is the number identified when you typed ls, if a number is required)

```
cd /media/cdrom#
```

```
ls
```

You should now see the xorg.txt file you saved on the cd.  Type:

```
sudo nano xorg.txt
```

ctrl o

Edit the file name to:

```
/etc/X11/xorg.conf
```

Immediately preceeding the file name you may see an expression such as 'DOS Format' or 'MAC Format'.  If you see either of these descriptions hold down Alt and then press m as many times as necessary to remove these descriptions.  Once this is done:

return

ctrl x

```
sudo reboot
```

Your machine should now reboot with the full desktop display.  Login using your username and password.  If it doesn't, type:

```
startx
```

Look at any resulting errors, as you may be able to use these to modify the xorg.conf file.

The Known Issues Wiki (see address at top of post) also gives advice on editing a further file, if you have a blank screen.  Type:

```
sudo nano /etc/initramfs-tools/modules
```

Use the cursor key to go to the bottom of the file and add the line:

```
ide-disk
```

ctrl o

return

ctrl x

```
sudo update-initramfs -u
```

If you are up and running with a full desktop and have logged in, then there are some multimedia options that you may wish to install. These are mainly codecs that interpret video and sound and the software needed to decrypt your DVDs and also set the correct DVD region.  Set up of PowerPC multimedia is more dificult than for normal i386 computers becuase not, in particular, Flash, as used on iplayer and youtube is not avialbale for Linux PowerPC.  However, through the use of programme called Gnash and another 'get around', a great deal of flash content can be viewed, including youtube.  BBC iplayer programmes can also be downloaded for playback at a later time.  The PowerPCFAQ page has information and links for adding multimedia:

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

There is also help at:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

To set up some basic multimedia capability:

```
sudo apt-get install ubuntu-restricted-extras
```

```
sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) --output-document=/etc/apt/sources.list.d/medibuntu.list
```

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

```
sudo apt-get install libdvdcss2
```

```
sudo apt-get install ppc-codecs
```

```
sudo apt-get install libdvdread3
```

```
sudo apt-get install libdvdnav4
```

The regionset package that you may see referred to in Ubuntu documentation does not appear to be required by the libdvdcss2 decryption package, and it interfered with the playing of DVDs on my machine.

Some flash content can be viewed by one of the 2 following methods.  If Gnash doesn't work, try method 2.

1. Install gnash, which will work for some sites:

```
sudo apt-get install mozilla-plugin-gnash
```

2.  Install a handy downloader: 

Open browser

Right click on bar below the web address (Bookmark Toolbar) and select new folder.  

Entitle this:

Video Downloads

Go to:

[http://1024k.de/bookmarklets/video-bookmarklets.html](http://1024k.de/bookmarklets/video-bookmarklets.html)

Right click the:

All-In-One Video Bookmarklet

Select the arrow to the right of the 'Folder' dropdown and then select the arrow to the left of Bookmarks Toolbar, finally, select Video Downloads.  Press Done.

Go to youtube.com and use a hyperlink to select a video.  Go to the Video Download Download folder on the Bookmark Toolbar and select yor  new bookmark.  A new dialogue box will appear.  Left click the .flv Download Link and it will play in the browser window.  Check the bookmarklets page for more  advice and a 'how to' video. You can also save the video to your hard drive to play later.

I installed a media player called VLC.  It can handle a large variety of video formats, including playing DVDs:

```
sudo apt-get install vlc
```

Totem is the default media player, so when you put a DVD into the computer, it will launch Totem.  To play in VLC, just close Totem and open VLC.

The default dvd player can be changed if you wish.  The information on setting the default player comes from this link:

[http://ubuntuforums.org/showthread.php?t=844654](http://ubuntuforums.org/showthread.php?t=844654)

I have chosen Ogle as the defualt player, as I think it plays well, but you can use the default player instructions for any media player.

To begin with we will install and set up Ogle.  Open Terminal and type:

```
sudo apt-get install ogle ogle-gui
```

Ogle setup instructions come from this link:

[http://linux.die.net/man/5/oglerc](http://linux.die.net/man/5/oglerc)

Once Ogle is installed we need to set up the sound and fullscreen. (BTW to toggle fullscreen on and off while playing type f or F).  Type:

```
sudo nano /usr/share/ogle/oglerc
```

The Ogle config file just requires a couple of changes.  The config file contains options for comprehensive set-up.  Look for:

```
<audio>
<device>
<driver>oss</driver>
```

Change the driver from oss to alsa.

Look for:

```
<drc>no</drc>
```

Change no to yes.  DRC makes loud noises softer, and quiet sounds louder.

Look for:

```
<fullscreen>no</fullscreen>
```

Change no to yes.

ctrl o
Return
ctrl x

To make Ogle the default player, type:

```
sudo nano /etc/gnome/defaults.list
```

Look for:

```
x-content/video-dvd=totem.desktop
```

Change the line to:

```
x-content/video-dvd=ogle-gui.desktop
```

ctrl o
Return
ctrl x

Type:

```
sudo cp /usr/share/app-install/desktop/ogle-gui.desktop /usr/share/applications/
```

```
sudo reboot
```

When rebooted, open Terminal and type:

```
nautilus
```

In the resulting file broswer select [Edit], [Preferences], [Media] and in the [DVD Video] option select Ogle from the drop down list.

Close the file browser and Terminal.

If the above has worked, you will be able to insert a dvd a have it automatically launch Ogle and play in full screen.

If you want RealPlayer, the PowerPC FAQ page has good instructions.  RealPlayer allows live streaming of BBC radio content, amongst other things.  If you go to BBC iplayer and select the radio station of your choice and then 'listen live', the webpage will use RealPlayer to stream.

If you want to 'listen again' on the BBC, then this site will do it for you, via realplayer or helix plugin for Totem (I don't know exactly how it works, but it does):

[http://www.iplayerconverter.co.uk/](http://www.iplayerconverter.co.uk/)

I have also downloaded epiphany browser:

```
sudo apt-get install epiphany-browser
```

In theory, if you disable javascript, 'Edit', 'Preferences', 'Privacy', and then select a non-live radio programme from BBC iplayer, then you should get a screen asking you to enable javascript and offering to launch the programme in realplayer instead.  I get the screen, but epiphany is not linked to realplayer, so I can't get the programmes to start.  However, if someone knows how to make the link, then this will work.  (I already use this method on an old mobile IE browser and a more modern mobile Opera browser on a PDA). 

If you want to watch iplayer programmes, then you can download them (as opposed to streaming them) using the following technique.  You should be aware that this technique downloads programmes without the associated digital rights management (DRM), so the BBC makes attempts to prevent this method from working from time to time, and if you have qualms regarding the legal side, then you should avoid using it.  Open a terminal and type:

```
wget [http://po-ru.com/files/iplayer-dl-latest.tar.gz](http://po-ru.com/files/iplayer-dl-latest.tar.gz)
```

```
tar zxvf iplayer-dl-latest.tar.gz
```

```
cd iplayer-dl-0.1.14/
``` (or the actual version downloaded)

```
sudo apt-get install ruby
```

```
ruby setup.rb config
```

```
sudo ruby setup.rb install
```

```
cd bin
```

```
./iplayer-dl [http://www.bbc.co.uk/iplayer/theprogrammeyouwant](http://www.bbc.co.uk/iplayer/theprogrammeyouwant)
```  (taken from the BBC page you want to view)

The programme will now be downloaded in .MOV format and can play on Totem, VLC  or other players.

If the BBC offers podcasts of a particular programme, then go to the BBC podcast directory and copy the URL of the required programme subscription.  Open rhythmbox and select new podcast.  Copy the subscription URL into the required box, and the programme will be downloaded as MP3.  You can set rhythmbox for regular update of programme subscriptions.

---

### Post by cyberdork33 on 2009-02-02
Just a tip, you should put terminal output, or commands that you type into a terminal in 
[noparse]```
code tags
```[/noparse]

---

### Post by mkvnmtr on 2009-02-02
First class tutorial. Thanks it will help a lot of folks.

---

### Post by SlowerLearner on 2009-02-03
This is my first post.  I'll need to learn how to make subsequent posts more user friendly, but this post has been sitting on my computer for a month, and it was a waste just leaving it there, so I just posted it as text.

---

### Post by conal on 2009-02-10
Brilliant, Thanks SlowerLearner.

This will be very helpful. Ive just installed 8.04 on my iMac G4. It actually worked with the live install CD for me despite stating on the system requirements page that the alternate install CD should be used for systems with 256mb or less (I have just 256mb). Guess I got lucky on that one.

The one thing I could not figure out is how to use iplayer. I'm going to upgrade the Ram, then try the method you suggest. At the moment, just going on the iplayer site crashes the computer and I have to shutdown, but I think that is due to low ram.

I also could not get Totem-Gstreamer to work for playing DVD's but I kept it for the Firefox plugin and installed Xine with its own User Interface to play DVD's. This worked a charm. 
 
Good to see someone else breathing new life into old macs!

Conal

---

### Post by SlowerLearner on 2009-02-12
> **conal said:**
> Brilliant, Thanks SlowerLearner.

This will be very helpful. Ive just installed 8.04 on my iMac G4. It actually worked with the live install CD for me despite stating on the system requirements page that the alternate install CD should be used for systems with 256mb or less (I have just 256mb). Guess I got lucky on that one.

The one thing I could not figure out is how to use iplayer. I'm going to upgrade the Ram, then try the method you suggest. At the moment, just going on the iplayer site crashes the computer and I have to shutdown, but I think that is due to low ram.

I also could not get Totem-Gstreamer to work for playing DVD's but I kept it for the Firefox plugin and installed Xine with its own User Interface to play DVD's. This worked a charm. 

Conal

I didn't try the live CD!  The iplayer won't work directly from the BBC site, because flash is not available for the power pc (ppc) architecture of the iMac, so I think that at present the download method is the only real alternative.  I've been using VLC to play DVDs, but they're not perfect, so I'll try xine instead, thanks.

---

### Post by SlowerLearner on 2009-02-27
I've taken the hint about the code tags, and it looks a lot better now.  Thanks

---

### Post by treborsux on 2009-03-17
I would like to have the txt files he attached but the forum wont let me have them???  Says login when i am logged in or says i dont have access???  How come I cant have those attachments??

---

### Post by treborsux on 2009-03-17
This is what it says if I try to get attachment or veiw them or whatever???
WHY????? PLEASE

You are not logged in or you do not have permission to access this page. This could be due to one of several reasons:
You are not logged in. Fill in the form at the bottom of this page and try again. 
You may not have sufficient privileges to access this page. Are you trying to edit someone else's post, access administrative features or some other privileged system? 
If you are trying to post, the administrator may have disabled your account, or it may be awaiting activation.

---

### Post by treborsux on 2009-03-17
I have the yaboot.txt ok but please i need the xorg.txt

---

### Post by cyberdork33 on 2009-03-17
works fine for me.

---

### Post by SlowerLearner on 2009-03-17
I have just downloaded the attachments and pasted below.  Perhaps because I made the original post??

Xorg first:

# xorg.conf (X.Org X Window System server configuration file)

#

# This file was generated by dexconf, the Debian X Configuration tool, using

# values from the debconf database.

#

# Edit this file with caution, and see the xorg.conf manual page.

# (Type "man xorg.conf" at the shell prompt.)

#

# This file is automatically updated on xserver-xorg package upgrades *only*

# if it has not been modified since the last upgrade of the xserver-xorg

# package.

#

# If you have edited this file but would like it to be automatically updated

# again, run the following command:

#   sudo dpkg-reconfigure -phigh xserver-xorg



Section "Files"

	FontPath	"/usr/share/X11/fonts/misc"

	FontPath	"/usr/share/X11/fonts/cyrillic"

	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"

	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"

	FontPath	"/usr/share/X11/fonts/Type1"

	FontPath	"/usr/share/X11/fonts/100dpi"

	FontPath	"/usr/share/X11/fonts/75dpi"

	FontPath	"/usr/share/fonts/X11/misc"

	# path to defoma fonts

	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"

EndSection



Section "Module"

#	Load	"ic2"

	Load	"bitmap"

#	Load	"ddc"

	Load	"dri"

	Load	"extmod"

	Load	"freetype"

#	Load	"glx"

	Load	"int10"

#	Load	"type1"

	Load	"vbe"

EndSection



Section "InputDevice"

	Identifier	"Generic Keyboard"

	Driver		"kbd"

	Option		"CoreKeyboard"

	Option		"XkbRules"	"xorg"

	Option		"XkbModel"	"pc105"

	Option		"XkbLayout"	"gb"

	Option		"XkbOptions"	"lv3:ralt_switch"

EndSection



Section "InputDevice"

	Identifier	"Configured Mouse"

	Driver		"mouse"

	Option		"CorePointer"

	Option		"Device"	"/dev/input/mice"

	Option		"Protocol"	"ExplorerPS/2"

	Option		"ZaxisMapping"	"4 5"

	Option		"Emulate3Buttons"	"true"

EndSection



Section "InputDevice"

	Driver		"wacom"

	Identifier	"stylus"

	Option		"Device"	"/dev/wacom"

	Option		"Type"	"stylus"

	Option		"ForceDevice"	"ISDV4"

EndSection



Section "InputDevice"

	Driver		"wacom"

	Identifier	"eraser"

	Option		"Device"	"/dev/wacom"

	Option		"Type"	"eraser"

	Option		"ForceDevice"	"ISDV4"

EndSection



Section "InputDevice"

	Driver		"wacom"

	Identifier	"cursor"

	Option		"Device"	"/dev/wacom"

	Option		"Type"	"cursor"

	Option		"ForceDevice"	"ISDV4"

EndSection



Section "Device"

	Identifier	"ATI Technologies, Inc. Rage 128 RL/VR AGP"

	Driver		"ati"

	Option		"UseFBDev"	"true"

EndSection



Section "Monitor"

	Identifier	"iMac"

	Option		"DPMS"

	HorizSync	60-60

	VertRefresh	75-117

EndSection



Section "Screen"

	Identifier	"Default Screen"

	Device		"ATI Technologies, Inc. Rage 128 RL/VR AGP"

	Monitor		"iMac"

	DefaultDepth	24

	SubSection "Display"

		Depth	1

		Modes	"800x600" "640x480"

	EndSubSection

	SubSection "Display"

		Depth	4

		Modes	"800x600" "640x480"

	EndSubSection

	SubSection "Display"

		Depth	8

		Modes	"800x600" "640x480"

	EndSubSection

	SubSection "Display"

		Depth	15

		Modes	"800x600" "640x480"

	EndSubSection

	SubSection "Display"

		Depth	16

		Modes	"800x600" "640x480"

	EndSubSection

	SubSection "Display"

		Depth	24

		Modes	"800x600" "640x480"		

	EndSubSection

EndSection



Section "ServerLayout"

	Identifier	"Default Layout"

	Screen		"Default Screen"

	InputDevice	"Generic Keyboard"

	InputDevice	"Configured Mouse"

	InputDevice	"stylus"	"SendCoreEvents"

	InputDevice	"cursor"	"SendCoreEvents"

	InputDevice	"eraser"	"SendCoreEvents"

EndSection



Section "DRI"

	Mode	0666

EndSection

Yaboot next:

## yaboot.conf generated by the Ubuntu installer

##

## run: "man yaboot.conf" for details. Do not make changes until you have!!

## see also: /usr/share/doc/yaboot/examples for example configurations.

##

## For a dual-boot menu, add one or more of:

## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ



boot=/dev/hda2

device=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:

partition=3

root=/dev/hda3

timeout=50

install=/usr/lib/yaboot/yaboot

magicboot=/usr/lib/yaboot/ofboot

enablecdboot



image=/boot/vmlinux

	label=Linux

	read-only

	initrd=/boot/initrd.img

	append="quiet nosplash nofb"



image=/boot/vmlinux.old

	label=old

	read-only

	initrd=/boot/initrd.img.old

	append="quiet nosplash nofb"

---

