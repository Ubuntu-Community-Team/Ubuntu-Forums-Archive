---
title: "Need to start over"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by Stormweaver on 2007-04-16
Ok... We have had a train wreak here with the Server....

I need to back up to the beginning, and take things slowly.

I'm still learning alot about all of this, and I realize I have jumped the curve by going straight to this, but I need to get several things up and running as quick as possible as several of my friends are leaving for Korea for 2 years thanks to the AF.

Ok.. At the Moment I have a AMD64 Machine built to act as this server/router of sorts.

I need to dump the current Ubunbtu set up and start over it looks like, as it refuses to see the brand new Cisco Cert Linksys LAN card I put in to work with the onboard LAN for this purpose.


----------------------------------


The end product of what we are doing -

One Computer that does several functions:

1. First contact point of the internet to the rest of the house.

((Time Warner Cable - TWC)) => Modem => (The computer we are working on) => Linksys Router => Comps 1-3 on Ports 1-3 and Port 4 => Router 2 => Comps 4-6 on Ports 1-3 and Port 4 is the House VoIP (Phone)

Purpose is to:
A. Have something that handles Firewall/Security for the house in hopes of building a Network where the Computers actually see each other

B. Run a Teamspeak Server to act as a means of communication for the group of friend being scattered across the globe. -- It seems that you need direct net connection for this software to work well.

C. Be able to run World of Warcraft (As another access point, and handle issues of banking for the group.)

D. Run Software that otherwise needs ethier direct internet connection, or multiple port forwarding - We have a Role Playing Client Software that the leader of the group (myself) must have a couple ports forwarded to his comp but in doing so kills access for some reason to other computers in the house using same software to connect. -- The GM's software acts as a host or server, and all other players connect to this person which will be on this comp. (If you can help me figure out how to have port forwarding work on Computer 1 while the other computers still can run and use software - Then this becomes moot point as the server and Comp 1 all are at the same Keyboard/Mouse. I have a KMV switch set up for Server, Comp 1, 4-6; 4 - 6 are for comps being worked on here at the house as I normally work on and build Windows machines as my means of work. Getting into Linux has been my Horizon broadening project.

2. This Comp also needs to serve as the point at which we can diagnose issues of cable service:

     A. TWC expects to have 1 Comp hooked directly to the Modem when you are having connection issues and won't resolve internal issues of connection which they seem to think all connection issues are internal and never their hardware. With this comp I need to be able to test, report and save information on the incoming signal so that when it messes up I can just hand a tech the data and let them figure out their hardware. ((Our last 3 issues took 6 weeks to fix w/ the tech coming out and not really doing anything, just telling me I don't know how to build a network, use a router, cut and connector cables or anything else. -- I finally pointed out that I built the entire network here - Had all these computers accessing the net and that suddenly after 2 years it had just stopped working, and wasn't fixed with a restart of internal systems. Finally my Networking/CEH friend brought over his Linux Box and put it in the spot that I am wanting to put this one and was able to monitor and diagnose and report back to TWC what was happening at our end - later turning out to be the box the houses all hook to at the pole had gone bad. -- I would have him helping me fix my problems here right now, but A. I want to learn to do this myself, and B. He is in Cali right now with a Tiger Team testing and overhauling a network for a Mil Base out there. He won't be back here till approx Nov. of this year.))

3. This Comp will in time also help me with my tech work.

     I would like to be able to have the GUI desktop on there to work from, with the ability to use command line when needed -- Which the way Iarwain ben-adar (another user on the forums) tells me, the Terminal interface in the GUI acts as full Command Line access unlike the DOS prompt in windows which is only really a "pepsi one" of access.

So starting at the beginning

Would it be better to use 32 bit or 64 bit server for this given the above needs?

And once that is decided other then taking my disc burned from the Ubuntu site is there anyting special I need to do in the install of software to get us started in the right direction?

I need to do this one step at a time, with posts confirming that things have gone good... If anyone is willing to help me on this, I would be very thankful.

---

### Post by Happy_Man on 2007-04-16
Uh....I don't think it matters for you which version you use. All you have to do is install system and software.

---

### Post by Stormweaver on 2007-04-17
Ok I went ahead and am setting up to do 32 Bit server -- That way the issues of getting Wine to work for WoW won't be so hard...

Now before I pop this disk in - What do I need to do to make sure it assigned the on board LAN as the LAN thats looking for internet from the modem and the extra LAN card feeding out to the router??

I know that its some sort of server setting, but I don't know what or where for Linux.  PLEASE HELP!

Stormweaver

---

### Post by Stormweaver on 2007-04-17
Bumping in hopes someone will help me!

---

### Post by psusi on 2007-04-17
> **Stormweaver said:**
> 
The end product of what we are doing -

One Computer that does several functions:

1. First contact point of the internet to the rest of the house.

((Time Warner Cable - TWC)) => Modem => (The computer we are working on) => Linksys Router => Comps 1-3 on Ports 1-3 and Port 4 => Router 2 => Comps 4-6 on Ports 1-3 and Port 4 is the House VoIP (Phone)


Why have a pc be a router to the router?  Why not just plug the modem into the router and everything else into it?

> Purpose is to:
A. Have something that handles Firewall/Security for the house in hopes of building a Network where the Computers actually see each other

B. Run a Teamspeak Server to act as a means of communication for the group of friend being scattered across the globe. -- It seems that you need direct net connection for this software to work well.

C. Be able to run World of Warcraft (As another access point, and handle issues of banking for the group.)

D. Run Software that otherwise needs ethier direct internet connection, or multiple port forwarding - We have a Role Playing Client Software that the leader of the group (myself) must have a couple ports forwarded to his comp but in doing so kills access for some reason to other computers in the house using same software to connect. -- The GM's software acts as a host or server, and all other players connect to this person which will be on this comp. (If you can help me figure out how to have port forwarding work on Computer 1 while the other computers still can run and use software - Then this becomes moot point as the server and Comp 1 all are at the same Keyboard/Mouse. I have a KMV switch set up for Server, Comp 1, 4-6; 4 - 6 are for comps being worked on here at the house as I normally work on and build Windows machines as my means of work. Getting into Linux has been my Horizon broadening project.


The linksys router will handle any security and forwarding needed just fine.  All of this software should run just fine behind the router with the proper ports forwarded, and unless you were planning on running it on the server itself ( warcraft is for windows, not sure about your rpg ), it isn't going to help.  

> 
2. This Comp also needs to serve as the point at which we can diagnose issues of cable service:

     A. TWC expects to have 1 Comp hooked directly to the Modem when you are having connection issues and won't resolve internal issues of connection which they seem to think all connection issues are internal and never their hardware. With this comp I need to be able to test, report and save information on the incoming signal so that when it messes up I can just hand a tech the data and let them figure out their hardware. ((Our last 3 issues took 6 weeks to fix w/ the tech coming out and not really doing anything, just telling me I don't know how to build a network, use a router, cut and connector cables or anything else. -- I finally pointed out that I built the entire network here - Had all these computers accessing the net and that suddenly after 2 years it had just stopped working, and wasn't fixed with a restart of internal systems. Finally my Networking/CEH friend brought over his Linux Box and put it in the spot that I am wanting to put this one and was able to monitor and diagnose and report back to TWC what was happening at our end - later turning out to be the box the houses all hook to at the pole had gone bad. -- I would have him helping me fix my problems here right now, but A. I want to learn to do this myself, and B. He is in Cali right now with a Tiger Team testing and overhauling a network for a Mil Base out there. He won't be back here till approx Nov. of this year.))


Usually cable companies also require that single PC to be running windows or they will not support it, so having a linux server there won't help.  In the event that you actually need to call them, it is a simple task to unplug a windows pc from the router and connect it directly to the modem for the duration of the tech support call.  

> 
Would it be better to use 32 bit or 64 bit server for this given the above needs?

Really doesn't matter.  For simplicity sake I'd say go with 32bit.  

> 
And once that is decided other then taking my disc burned from the Ubuntu site is there anyting special I need to do in the install of software to get us started in the right direction?

I need to do this one step at a time, with posts confirming that things have gone good... If anyone is willing to help me on this, I would be very thankful.

I'm not quite sure exactly what you are asking.

---

### Post by Stormweaver on 2007-04-17
1. Why have a pc be a router to the router? Why not just plug the modem into the router and everything else into it?
     --- I want this computer to serve as the network hub for the house - I just don't have enough LAN cards to do it.  I'm wanting to build an internal network where the computers see themselves... right now, everyone has their own firewalls and security up making it where no one can see another user on the comp.  Now if someone can help guide me through setting it all up - The sure, we can stick it behind the router.


2. The linksys router will handle any security and forwarding needed just fine. All of this software should run just fine behind the router with the proper ports forwarded, and unless you were planning on running it on the server itself ( warcraft is for windows, not sure about your rpg ), it isn't going to help. 
     -- Again - We set up the port to forward to the comp where the host software is, and the others in the house could not log into it anymore.  More information on what I am doing wrong here might help, but I felt if the comp could get in front of the router I wouldn't have to forward the port to it.

3.  Usually cable companies also require that single PC to be running windows or they will not support it, so having a linux server there won't help. In the event that you actually need to call them, it is a simple task to unplug a windows pc from the router and connect it directly to the modem for the duration of the tech support call. 
     --- On this front - I've not had to deal with that before so long as I could ping and be pinged.  The big issue was being able to show the lack of data flow past the modem, which my friend just didn't use a windows box to do.. he said that over time I could learn to understand more about what I was looking at -- That is a goal for me, moving a Win PC to the modem isn't hard as I have to just move a jumper from Router to Modem, I more just didn't want that issue to start with.  Figured kill as many birds with one stone as possible.


Quote:
And once that is decided other then taking my disc burned from the Ubuntu site is there anyting special I need to do in the install of software to get us started in the right direction?

I need to do this one step at a time, with posts confirming that things have gone good... If anyone is willing to help me on this, I would be very thankful.  

I'm not quite sure exactly what you are asking.

----  Moot point - 32 Bit install is complete, now I need help configuring.

So here is where I stand currently -- I installed 32 bit Server -- Had it install the DNS and other option both -- Figured it couldn't hurt.  Now I need to install a GUI for it which is just remembering the command to install Desktop and then I need help setting up the second LAN card.

---

### Post by Happy_Man on 2007-04-17
for a gui:

```

sudo apt-get install ubuntu-desktop

```

---

### Post by Stormweaver on 2007-04-17
Update:

GUI is installing now.

I noticed while Command Line was starting up that an error is occuring.

Cannot Allocate Resource Region 3 ...... Can't see the rest it flashes too quickly... Is this something to worry about??


So where do I stand, do I need to configure the Router better or do I need to leave this PC in front of the router to do what I need/want to do?


Stormweaver

---

### Post by Stormweaver on 2007-04-17
Update: Ok Desktop installed - Automatix installed - Nvidia drivers and other stuff coming in now from Automatix.


I need to know what to do about where this machine will sit, and help configuring it.


Thanks!

Stormweaver

---

### Post by Stormweaver on 2007-04-17
Update:

Ok I got all but the Nvidia to come down.  The first go around with this machine - I used the 64 Bit version and when I used Automatix to pull down the drivers it did it without issue -- Now this is what I get:

```

!!SCRIPT OUTPUT END!!
[04/17/2007 - 21:04.12] - ERRORS OR WARNINGS WHERE REPORTED
[04/17/2007 - 21:04.12] - FATAL - Nvidia Driver - An apt-based error occurred and installation was unsuccessful
[04/17/2007 - 21:10.36] - !!Starting Automatix 1.1-3.3!!
[04/17/2007 - 21:11.01] - !!SCRIPT OUTPUT START!!
05:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package linux-restricted-modules-2.6.17-11-server

!!SCRIPT OUTPUT END!!
[04/17/2007 - 21:11.01] - ERRORS OR WARNINGS WHERE REPORTED
[04/17/2007 - 21:11.01] - FATAL - Nvidia Driver - An apt-based error occurred and installation was unsuccessful

```

So I need to figure out what to do to fix that.  Any help here?

Gonna go start on getting Teamspeak brought in and setup -- Hoping I can find a way to set this up so that the others outside the house can see and connect to it.

Stormweaver

PS --> Feel free to MSG me on MSN or Yahoo

---

### Post by Stormweaver on 2007-04-18
Update:

Well its 1AM here .....


I have the Teamspeak server up and running from behind the Router... So the need to set up the system to flow the incoming net onto the router is no longer needed.

I am still having video issues... I can't get the Nvidia drivers to start for anything.

I need to set up something of a script to run at start up or with double clicking on the main desktop... Need some help there.

Still don't know what I need to do to use this machine to protect our network or how to get one set up at this point that everyone can be seen on, any help there would be great as well!

Other then that, my wife's best friend is being induced to labor in the morning so I need to sleep before I have to get up at 4 AM.... I will update again through out the day tomorrow as I get more done on this beast... Anything that can be offered as aide or recommendation would be greatfully accepted.  Night to all!

Stormweaver

---

### Post by igknighted on 2007-04-18
> **Stormweaver said:**
> Update:

Ok I got all but the Nvidia to come down.  The first go around with this machine - I used the 64 Bit version and when I used Automatix to pull down the drivers it did it without issue -- Now this is what I get:

```

!!SCRIPT OUTPUT END!!
[04/17/2007 - 21:04.12] - ERRORS OR WARNINGS WHERE REPORTED
[04/17/2007 - 21:04.12] - FATAL - Nvidia Driver - An apt-based error occurred and installation was unsuccessful
[04/17/2007 - 21:10.36] - !!Starting Automatix 1.1-3.3!!
[04/17/2007 - 21:11.01] - !!SCRIPT OUTPUT START!!
05:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package linux-restricted-modules-2.6.17-11-server

!!SCRIPT OUTPUT END!!
[04/17/2007 - 21:11.01] - ERRORS OR WARNINGS WHERE REPORTED
[04/17/2007 - 21:11.01] - FATAL - Nvidia Driver - An apt-based error occurred and installation was unsuccessful

```

So I need to figure out what to do to fix that.  Any help here?

Gonna go start on getting Teamspeak brought in and setup -- Hoping I can find a way to set this up so that the others outside the house can see and connect to it.

Stormweaver

PS --> Feel free to MSG me on MSN or Yahoo

Ok, it looks like you are running the server kernel.  If you want the nvidia drivers, you havea  couple options.

Option 1) Install the generic kernel from synaptic/apt-get.  Then install the package nvidia-glx.  This will install the kernel and the linux-restricted package.  Unfortunately, there is no restricted package for the server kernel (as not many servers run 3d accelerated GUIs), and this is required to install the version of the driver from the repositories.  Now, using the generic kernel might have negative consequences for your server, or it might affect nothing.  I cannot tell you.  If you try this route and the server side breaks down, all you need to do is reboot into the server kernel again (grub will give you this option) and it should go back, but not have 3d.

Option 2) The first method is a work around to get the "easy" way to work, this will help you get 3d working with the server kernel.  The first thing you need is the package "linux-headers-server".  Next, you need to go to [www.nvidia.com](www.nvidia.com) and get the driver from their site.  Now, put it in your home folder.  Open a terminal and type
```
chmod +x NVIDIA....run
``` (fill in the real package name)

Now hit ctrl+alt+F1 to go to a terminal only.  You will need to login (you wont see you password being typed, but it is), then type these commands:
```
sudo /etc/init.d/gdm stop
sudo ./NVIDIA...run
```(again filling in the full filename of the driver installer)

Now an interactive installer will come up.  Basically just click OK, and it should do its thing fine.  Let it configure xorg.conf in the last step, and as long as there were no errors it should be ready to go now.  Type this in the terminal to restart the GUI:
```
sudo /etc/init.d/gdm start
```

You should see an NVIDIA splash screen before you get to the login screen.  If you don't, post back here and we can help enable it the rest of the way.  Also, if you do for some reason get errors during the install post them here as well.

---

### Post by Stormweaver on 2007-04-18
Ok we have hit errors... 

I brought down the pkg and put it in home folder.. I switched out to command line without issues, and stopped gnome.  Then ran the pkg and it kept giving me error along the line of:

You appear to be using a modular Xorg release, Nvidia installer is unable to determine the correct X libarary,
Please install the Xorg SDK/development pkg for your release.

It also tried to find some sort of interface both on the comp and on the web without success, then said it installed drivers but no change in how the display is running.  So what do I do??

Wow.. I'm learning so much, but still feel so stupid. LOL

If there is a way to post up all of what I saw, I have not found it as it seemed to be in the program.

Stormweaver

---

### Post by Stormweaver on 2007-04-18
Update: 

The graphics are still screwed up per last post.  But I will note that the Nvidia software seems to be in the system tools, but there is nothing there that I can change.  The graphics of just the GUI is choppy so I know we aren't quite set up right.

The Teamspeak has stayed up and running now for since last night.  So I must be doing something correct!

Now to get this thing ready to install WoW, which I will wait on till graphics and any other server set up issues are handled.


Stormweaver

---

### Post by igknighted on 2007-04-18
> **Stormweaver said:**
> Ok we have hit errors... 

I brought down the pkg and put it in home folder.. I switched out to command line without issues, and stopped gnome.  Then ran the pkg and it kept giving me error along the line of:

You appear to be using a modular Xorg release, Nvidia installer is unable to determine the correct X libarary,
Please install the Xorg SDK/development pkg for your release.

It also tried to find some sort of interface both on the comp and on the web without success, then said it installed drivers but no change in how the display is running.  So what do I do??

Wow.. I'm learning so much, but still feel so stupid. LOL

If there is a way to post up all of what I saw, I have not found it as it seemed to be in the program.

Stormweaver

Search for SDK and install the dev package for it if that is what it needs.  If you type "cat /etc/X11/xorg.conf" what does it say?  Could you post it here in code tags?

---

### Post by Stormweaver on 2007-04-18
```
stormweaver@Eye-of-the-Storm:~$ cat /etc/X11/xorg.conf
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
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
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
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:5:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection
stormweaver@Eye-of-the-Storm:~$ 

```

Sorry was trying to get that in... As to what its looking for, I am not entirely sure.

Figured I would get this up while I start working on the other part.

---

### Post by Stormweaver on 2007-04-18
Update before bed:

System is still running stable - I cannot figure out for the life of me what this thing is looking for from the above issue.  I don't know if I am looking for a library or a config file or what.  Also I noticed I am getting an error during boot that says something like "Cannot Allocate Resource to Region 3" or something of that ilk... If someone could tell me where that would be logged I will put a copy of it up here in code bracket.


So I am off to bed, to anyone helping with this - Please feel free to MSG me on MSN or Yahoo -- If I am at comp then I will work with anyone to get this taken of.

Stormweaver

---

### Post by Stormweaver on 2007-04-19
Hey guys, 

Just bumping this in hopes of finishing up with the problems here.  Nothing has changed since last night, but then I am just now getting sat down to it.


How do you search the repos for key word items such as SDK?


I am on my msgers if you have time to help.

Stormweaver

---

### Post by Stormweaver on 2007-04-19
Ok - Did a:

apt-cache search SDK

and got like 300 things that have SDK in them.. I don't know what I am looking for as far as this Xorg release thing is concerned... This is beginning to wear on my nerves.

I need to figure out what has gone wrong with the Graphics and get them fixed and up and running to spec so that I can go about installing the other things I would like to get up and running.

On top of things my Windows Box - Mobo bit the dust this morning... So I am now down to the server for the moment.

Stormweaver

---

### Post by Rotaj on 2007-04-19
As far as the graphics go, I would prefer that someone with more experience give the same suggestion. But "Envy"might help. It should be available though synaptic. I just don't know if it will work for the server version.

---

