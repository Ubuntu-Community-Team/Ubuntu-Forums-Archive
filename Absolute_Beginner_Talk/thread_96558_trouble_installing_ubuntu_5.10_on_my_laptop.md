---
title: "trouble installing ubuntu 5.10 on my laptop"
date: 2005-11-29
forum: Absolute Beginner Talk
---

### Post by zwcp on 2005-11-29
Hi...

I'm new to this forum and linux in general, but none the less, I hope someone can help me...

Im trying to install ubuntu version 5.10 on my old Toshiba Satellite Pro 4220 XCDT laptop. Its got an 6 GB harddrive, 192 ram and 450 Mhz cpu.

Im using the installation CD supplied and shipped by ubuntu.

Heres the problem/s:

im using the basic setupmode and letting ubuntu guide me through the installation.
the process works fine up until we get to the point where it starts to instal the additional packages, right after it has installed the basic system...
After a while it comes up with af screen saying, that: "you havent got enough disk space for the installation, and would i like to continue anyways?".
According to the info on the CD case, it only requires 1.8 GB of disk space to install, and ive got 6 GB, so why does it write this?

I then press "continue" and move on, hoping to fix the problem later. The program runs the rest of the setup, and then finaly prompts: "remove CD to make sure the computer boots up from the harddrive where you installed the programs".
It shuts down and reboots starting up with the ubuntu logo, and show af list of the stuff its attempting to start up... everything gets an "ok" and the screen now changes again to the same type of oldfashioned screen used during the initial instalment.

The screens titel says: "installing packages", further down its says "preparing for installation" and theres a proces bar reading "0 %"....

and then it stops... nothing else happens... Ive tried to shut down the computer and start it up again, but it allways ends up the same way, with the same screen saying "installing packages" and the proces bar reading "0 %"...


What am i doing wrong and can anyone help me...

Kind regards

Anders from Denmark

---

### Post by ertai on 2005-11-29
Have you selected the whole drive to be used by Ubuntu? Because it really seems that you have too little space.

What you can try is install Ubuntu again and the devide the harddiskpartitions bij yourself. Make 1 swappartition as big as twice your memory and 1 partition that is as big as the rest of your harddisk. Set the type of this partition as 'ext3' and set the mountpoint to '/'. Then go on with the install and then it should work.

---

### Post by zwcp on 2005-11-29
[QUOTE=ertai]Have you selected the whole drive to be used by Ubuntu? Because it really seems that you have too little space.

What you can try is install Ubuntu again and the devide the harddiskpartitions bij yourself. Make 1 swappartition as big as twice your memory and 1 partition that is as big as the rest of your harddisk. Set the type of this partition as 'ext3' and set the mountpoint to '/'. Then go on with the install and then it should work.[/QUOTE]

hmm... as far as i now ive selected the whole drive... iet even says that if i choose the selection i made, it will delete everything, including previous partitions...

Could you explain how i can ber running out space, when the cd cover says, it only needs 1.8 GB og disk space...?

I'll try to do what you suggested and get back to you asap...

---

### Post by zwcp on 2005-11-29
[QUOTE=zwcp]hmm... as far as i now ive selected the whole drive... iet even says that if i choose the selection i made, it will delete everything, including previous partitions...

Could you explain how i can ber running out space, when the cd cover says, it only needs 1.8 GB og disk space...?

I'll try to do what you suggested and get back to you asap...[/QUOTE]


It works :D........

And i didnt even need to do a manual partioning thingy


But now ive got another problem... I cant set the rezolution to anything bigger then 800x600... I found something regarding this earlier, but now i cant find it any more... 

anyone?

---

### Post by atoponce on 2005-11-29
[quote=zwcp]It works :D........

And i didnt even need to do a manual partioning thingy


But now ive got another problem... I cant set the rezolution to anything bigger then 800x600... I found something regarding this earlier, but now i cant find it any more... 

anyone?[/quote] 
What video driver are you using to power the monitor? The generic VESA driver will probably work best for you as it sounds like you have older hardware. Are you sure the monitor is capable of getting a resolution higher than 800x600?

---

### Post by zwcp on 2005-11-29
[QUOTE=atoponce]What video driver are you using to power the monitor? The generic VESA driver will probably work best for you as it sounds like you have older hardware. Are you sure the monitor is capable of getting a resolution higher than 800x600?[/QUOTE]

The laptop is capable of using a rezolution higher than 800x600... ive had $win$ XP installed on it before where i used a 1024x768 rezolution

I dont know which driver im using... how can i find out?

---

### Post by atoponce on 2005-11-29
[quote=zwcp]The laptop is capable of using a rezolution higher than 800x600... ive had $win$ XP installed on it before where i used a 1024x768 rezolution

I dont know which driver im using... how can i find out?[/quote]

Can you output your /etc/X11/xorg.conf file?  I can help you better looking at that versus trying to explain it blindly.

---

### Post by zwcp on 2005-11-29
[QUOTE=atoponce]Can you output your /etc/X11/xorg.conf file?  I can help you better looking at that versus trying to explain it blindly.[/QUOTE]

how do I do that?

brand new here... sorry

---

### Post by Brunellus on 2005-11-29
[QUOTE=zwcp]how do I do that?

brand new here... sorry[/QUOTE]
open a terminal

execute this:

```
cat /etc/X11/xorg.conf > myconf.txt
```
then go to Places>Home.  in your home directory there should now be a file called myconf.txt.  Double-click it, and paste the textfile there into a post here.

---

### Post by zwcp on 2005-11-29
[QUOTE=Brunellus]open a terminal

execute this:

```
cat /etc/X11/xorg.conf > myconf.txt
```
then go to Places>Home.  in your home directory there should now be a file called myconf.txt.  Double-click it, and paste the textfile there into a post here.[/QUOTE]

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

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"i2c"
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"dk"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"Trident Microsystems Cyber 9525"
	Driver		"trident"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Standard Skærm"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Trident Microsystems Cyber 9525"
	Monitor		"Standard Skærm"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by atoponce on 2005-11-29
[quote=zwcp]...cropped...
Section "Device"
    Identifier    "Trident Microsystems Cyber 9525"
    Driver        "trident"
    BusID        "PCI:1:0:0"
EndSection
...cropped...[/quote] 
Change to:

```
Section "Device"
    Identifier    "Trident Microsystems Cyber 9525"
    Driver        "vesa"
    BusID         "PCI:1:0:0"
EndSection
```

Then restart X.

---

### Post by zwcp on 2005-11-29
[QUOTE=atoponce]Change to:

```
Section "Device"
    Identifier    "Trident Microsystems Cyber 9525"
    Driver        "vesa"
    BusID         "PCI:1:0:0"
EndSection
```

Then restart X.[/QUOTE]

okay... restart X????

and how do i change it?

---

### Post by zwcp on 2005-11-29
i guess i have to download and install a new driver, is that what you're saying?

---

### Post by atoponce on 2005-11-29
[quote=zwcp]okay... restart X????

and how do i change it?[/quote]

You have be root to edit the xorg.conf file.  Once edited you can restart X by either the "Ctrl+Alt+Backspace" keyboard shortcut or just restart your laptop.

---

### Post by atoponce on 2005-11-29
[quote=zwcp]i guess i have to download and install a new driver, is that what you're saying?[/quote]

No.  The vesa driver is included in Xorg as a generic driver for displays.  You just need to edit the file using:

```
sudo gedit /etc/X11/xorg.conf &
```

---

### Post by zwcp on 2005-11-29
[QUOTE=atoponce]You have be root to edit the xorg.conf file.  Once edited you can restart X by either the "Ctrl+Alt+Backspace" keyboard shortcut or just restart your laptop.[/QUOTE]

im sorry, but im not that experienced a Linux/computer user yet... 

Can you spell it out, like you were trying to explain it to a child? help me out a lot...

---

### Post by zwcp on 2005-11-29
[QUOTE=atoponce]No.  The vesa driver is included in Xorg as a generic driver for displays.  You just need to edit the file using:

```
sudo gedit /etc/X11/xorg.conf &
```[/QUOTE]


okay... I asumed that you wanted me to open up a terminal and enter the piece of code above, and that, that would open thingy that would enable me to edit the file...

Ive tried to do that, but i dont think it worked...

ive copy/pasted the text from the terminal screen in here below:

anders@D40A696B:~$ sudo gedit /etc/X11/xorg.conf &
[1] 9834
anders@D40A696B:~$ Password:
zwcp4700
bash: zwcp4700: command not found

[1]+  Stopped                 sudo gedit /etc/X11/xorg.conf
anders@D40A696B:~$ sudo gedit /etc/X11/xorg.conf &
Password:
[2] 9862

[2]   Stopped                 sudo gedit /etc/X11/xorg.conf
anders@D40A696B:~$

---

### Post by Brunellus on 2005-11-29
Do all the following in a terminal window:

[NOTE:  all of this needs to be done with sudo, which will ask you for a password.  when prompted, type your USER password.]

1) back up your xorg.conf file.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.backup
```

2) edit your xorg.conf file

```
 sudo nano /etc/X11/xorg.conf
```

(if you are running in the GUI, you can also use "gedit" instead of "nano" above)

3) make the changes as shown in [post #11](http://www.ubuntuforums.org/showpost.php?p=529992&postcount=11) above

4) save the new file.

5) Restart the X windows server by giving it a three-fingered salute.  Hit and hold (simultaneously) CTRL + ALT + BACKSPACE on your keyboard.  The screen will go black, and the Xwindows session will restart.  You should be seeing a GDM login screen.  Log in.

---

### Post by atoponce on 2005-11-29
[quote=zwcp]im sorry, but im not that experienced a Linux/computer user yet... 

Can you spell it out, like you were trying to explain it to a child? help me out a lot...[/quote] 
The vesa driver is a driver that is included with Xorg (the software that draws all the graphics on your monitor) by default.  You don't need to do any downloading or installing.  Just edit the text file from the "trident" driver to the "vesa" driver.

With that said, the xorg.conf file in the /etc/X11 directory cannot be edited by a regular user of the system.  You can't just open the file, and begin editing like you can in Windows.  Not this file, anyway.  The 'root' user, or a user with system administration privileges are the only ones who can edit this file.

Think of it like driving.  You can't drive a car until you reach the legal age, and receive a license.  You can't drive until you are given authority.  The same holds true for editing the file.  You must have the proper authority/permissions to edit the file.

The 'sudo' command from the terminal makes this possible.  Just type in the command I posted previously in a terminal to edit the file.  GEdit is a great text editor to edit in.  Once the file is edited, save it and reboot.

That *should *fix your crummy screen resolution.  Notice the emphasis on the word *should*.  :)

---

### Post by atoponce on 2005-11-29
[quote=zwcp]okay... I asumed that you wanted me to open up a terminal and enter the piece of code above, and that, that would open thingy that would enable me to edit the file...

Ive tried to do that, but i dont think it worked...

ive copy/pasted the text from the terminal screen in here below:

anders@D40A696B:~$ sudo gedit /etc/X11/xorg.conf &
[1] 9834
anders@D40A696B:~$ Password:
zwcp4700
bash: zwcp4700: command not found

[1]+  Stopped                 sudo gedit /etc/X11/xorg.conf
anders@D40A696B:~$ sudo gedit /etc/X11/xorg.conf &
Password:
[2] 9862

[2]   Stopped                 sudo gedit /etc/X11/xorg.conf
anders@D40A696B:~$[/quote]

Ah...  I forgot about that blasted ampersand when using sudo.  Don't use the "&" at the end of the command.  Sorry.  I should've known better.:oops:

---

### Post by zwcp on 2005-11-29
[QUOTE=atoponce]Ah...  I forgot about that blasted ampersand when using sudo.  Don't use the "&" at the end of the command.  Sorry.  I should've known better.:oops:[/QUOTE]

okay... im still trying to figure this out...

ive tried to copy/paste but when it asks me to write my password the buttons dont work... i cant type in my password... its really weird.

EDIT

okay this what ive copy/pasted in the terminal window:

```

anders@D40A696B:~$ sudo gedit /etc/X11/xorg.conf
Password:


```

it says "password", but i cant type anything....

---

### Post by jasay on 2005-11-29
The buttons do work, but nothing is displayed for added security.  Just trust it and type blindly.

---

### Post by Brunellus on 2005-11-29
your password isn't echoed, so that people can't read it over your shoulder.

clever, eh?

---

### Post by atoponce on 2005-11-29
So how is everything going zxcp?  Did you get it fixed?

---

### Post by zwcp on 2005-11-29
[QUOTE=atoponce]So how is everything going zxcp?  Did you get it fixed?[/QUOTE]

finally got into the file and changed it from "trident" to "vesa" just like I was told in a previus message...

But I still cant change the resolution. 
One thing did change though, the Hz changed to 61... 

Anybody got any other ideas?

---

### Post by zwcp on 2005-11-30
question: should i start a new thread regarding my problem with the resolution?

---

### Post by zwcp on 2005-11-30
[QUOTE=zwcp]question: should i start a new thread regarding my problem with the resolution?[/QUOTE]

just to get people up to speed, im using Toshiba Laptop Satellite Pro 4220 XCDT.

I've been searching the web to find a solution to my problem with the low screen resolution... 
For some reason i cant change my resolution to anything higher than, 800x600.
When i used $win$ XP i had set to 1024x780 or something like that...


I've found a website concerning more or less the same problem (I think), but my problem is that i'm a total newbie here...

Heres a link to the website: [http://qols.ph.ic.ac.uk/~ho1/toshiba-M35.html](http://qols.ph.ic.ac.uk/~ho1/toshiba-M35.html)

---

### Post by ed_d on 2005-11-30
ok, so you gone in and changed to the"vesa" driver, logged out and in, or better yet rebooted. Then you go to System>Preferences>Screen resolution, correct?
What is listed in the drop downs for the screen resolutions?

What **I** have done in the past is selected "expert" mode in the set up. You really dont have to be an "expert" to use this option, all it does for **me** is gives me the opportunity to see all of what is going on. Yo can still choose the "default" options while using Expert, but **I** feel it gave me more control on what was going on.

---

### Post by zwcp on 2005-11-30
[QUOTE=ed_d]ok, so you gone in and changed to the"vesa" driver, logged out and in, or better yet rebooted. Then you go to System>Preferences>Screen resolution, correct?
What is listed in the drop downs for the screen resolutions?

What **I** have done in the past is selected "expert" mode in the set up. You really dont have to be an "expert" to use this option, all it does for **me** is gives me the opportunity to see all of what is going on. Yo can still choose the "default" options while using Expert, but **I** feel it gave me more control on what was going on.[/QUOTE]

after changing to "vesa" the dropdowns gives me the choice between 800x600 and 640x480...

the freqeunzy (pardon my lousy english) it set to 61 Hz, and can not be altered.

hmmm.... When you talk about selecting expert mode, in setup, is that when you start from scratch and install ubuntu all over again?

---

### Post by ed_d on 2005-11-30
Correct.

I am confused as to why your not picking up the higher resolution as it is in your x11.con file.

And dont worry about grammer, I only speak 2 languages, english and bad english, and is mostly the latter.... :rolleyes:

---

### Post by zwcp on 2005-11-30
[QUOTE=ed_d]Correct.

I am confused as to why your not picking up the higher resolution as it is in your x11.con file.

And dont worry about grammer, I only speak 2 languages, english and bad english, and is mostly the latter.... :rolleyes:[/QUOTE]

;) hey as long as my mother doesnt see this, i'm okay (She's from England, and a school teacher)....

But this it really starting to get to me... i've read somewhere, not to get mad at linux for not working, so might just take it out on someone else at football practise later :rolleyes:

---

### Post by ed_d on 2005-11-30
Well, dont fret too much, youll work it out. Worst case is for you just to re-install it with expert mode. But I know someone will poo-poo that Idea and have you dig in a litte deeper. Your choice, and dont red card yourself at practice.

---

### Post by zwcp on 2005-11-30
[QUOTE=ed_d]Well, dont fret too much, youll work it out. Worst case is for you just to re-install it with expert mode. But I know someone will poo-poo that Idea and have you dig in a litte deeper. Your choice, and dont red card yourself at practice.[/QUOTE]

more like throw a flag... football, not soccer... ;)

---

### Post by ed_d on 2005-11-30
Assumed as you were across the pond, football=soccer, sorry. ;)

---

### Post by atoponce on 2005-11-30
[quote=zwcp]after changing to "vesa" the dropdowns gives me the choice between 800x600 and 640x480...

the freqeunzy (pardon my lousy english) it set to 61 Hz, and can not be altered.

hmmm.... When you talk about selecting expert mode, in setup, is that when you start from scratch and install ubuntu all over again?[/quote] 
Before you reinstall, try one last thing.  Edit the same xorg.conf file (be sure to make a backup), and change your vertical refresh and horizontal sync rates to the following:

```
Section "Monitor"
    Identifier    "Standard Skærm"
    Option        "DPMS"
    [FONT=verdana, arial, helvetica][SIZE=2]VertRefresh       50-110
      HorizSync          28-90[/SIZE][/FONT]
EndSection
```[FONT=verdana, arial, helvetica][SIZE=2]

If that doesn't work, I don't know what it could be.  I am not sure if there are multiple trident drivers that you might try instead of vesa.  I have Googled a bit, and haven't found anything pointing that direction.
[/SIZE][/FONT]

---

### Post by KermitJr on 2005-12-01
I was having trouble with several older video cards and a particular monitor and kept getting 640x480 no matter what I did for modes, etc.  

HOWEVER, when I went back one time and ran
```
sudo dpkg-reconfigure xserver-xorg
```
This is the easy way to edit xorg.

I entered the actually amount of RAM on the video card (one was 4096 and another 2048) and PRESTO! My Modes line worked as normal with or without monitor on boot.  (Number of MB * 1024)

Log out and ctrl-alt-backspace to restart xserver.

So try entering in the actual video RAM you have and that should hopefully fix your error.

If not, troubleshoot by looking for the actual error messages in the /var/log/X11/xorg[tab].log file.

Hope this helps!
KermitJr

---

### Post by zwcp on 2005-12-02
[QUOTE=KermitJr]I was having trouble with several older video cards and a particular monitor and kept getting 640x480 no matter what I did for modes, etc.  

HOWEVER, when I went back one time and ran
```
sudo dpkg-reconfigure xserver-xorg
```
This is the easy way to edit xorg.

I entered the actually amount of RAM on the video card (one was 4096 and another 2048) and PRESTO! My Modes line worked as normal with or without monitor on boot.  (Number of MB * 1024)

Log out and ctrl-alt-backspace to restart xserver.

So try entering in the actual video RAM you have and that should hopefully fix your error.

If not, troubleshoot by looking for the actual error messages in the /var/log/X11/xorg[tab].log file.

Hope this helps!
KermitJr[/QUOTE]

How do I find out what the amount of ram is on my videocard?

I tried configuring the vertical and horiz. refresh lines and it seems to have done something... First of all the Hz changed to 86 Hz and i kinda looks like the screen size has been altered, but im not sure...

---

### Post by zwcp on 2005-12-04
:S...

okay, i tried something else.... Found a site called Linux on Laptops Forums.... 

[http://www.linux-on-laptops.com/forum/showthread.php?p=343#post343](http://www.linux-on-laptops.com/forum/showthread.php?p=343#post343)

a guy there with the exact same problem on a slightly different machine running Kubuntu and not Ubuntu found a solution.... He'd copy/pasted his xorg.conf file into the message for others to benefit from... Before waiting for an answer I copy/pasted his xorg.conf file into mine, and hey presto, i got an error message and I am now reinstalling ubuntu again :D...

Cant make an omelet without breaking some eggs

---

