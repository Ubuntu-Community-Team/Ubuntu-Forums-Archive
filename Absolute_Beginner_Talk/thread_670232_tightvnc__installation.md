---
title: "tightvnc  installation"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by huntis619 on 2008-01-17
Hi all. I'm new to ubuntu. 2 weeks now. I installed ubuntu on my laptop and I love it. I'm still learning everyday. Before I installed ubuntu on my laptop, I was using tightvnc to remote access my desktop. The tight vnc is still installed on my desktop (windows xp pc) and I want to know how to install tightvnc on my ubuntu laptop. Will I be able to remote access my desktop from my ubuntu laptop? Also I asked this question before and didn't get a response. How can I use vlc media player to access my video files on my desktop from my laptop? Totem movie player will play the files from my desktop but the vlc media player. Please help

---

### Post by cecure on 2008-01-17
Ok lets start with tightvnc.   
Go to terminal and enter:
```
sudo apt-get install tightvncserver xtightvncviewer
```

to set your password for your vncserver enter:
```
vncpasswd
```

To start the server use the command```
tightvncserver
```, it will create a remote desktop at :1.

To view a remote desktop at the terminal enter:
```
xtightvncviewer
``` 
and follow the prompts.

Now for your vlc question, I need to know what type of video files you are accessing and how are you accessing them on your desktop with totem ?

hope this helps

---

### Post by huntis619 on 2008-01-17
Well first of all I have to apologize about not responding in a timely fashion. I'm sorry. I am totally new to this. When I followed your instructions a vnc server window opened in the top left corner.I'm not sure what do I do next.The desktop has iso files and mostly avi files also mkv files. When I open up my network and click on a avi file the totem movie player automatically comes up and starts playing.

---

### Post by cecure on 2008-01-17
First, there is no need to be sorry.  Everyone was new at this once upon a time and we are always 'new' at some aspect of linux, but we help each other along... beautiful isnt it?

Ok, so this time I will start with the video files.  Assuming that you have VLC installed in ubuntu then choose some random avi file, right click on it and go to properties.  Goto the tab that says open with and click on the dot beside VLC media player.  Now everytime you open any avi file it will open in VLC.  Just repeat the same procedure for the other file types.


As for VNC, I need some more information.  Is it the viewer you are trying to use ie are you trying to connect to a vnc server or are you trying to be the vnc server.

to test vnc try this, it will make you both server and client:

from a terminal window enter:
```
vncserver
```

This starts a server on your computer

then
```
tightvncviewer
```
enter ```
localhost:1
```
in the first prompt and your passwd in the second.

this should open your current computer in vnc

good luck

---

### Post by huntis619 on 2008-01-17
sudo apt-get install tightvncserver xtightvncviewer
[sudo] password for steven:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
tightvncserver is already the newest version.
xtightvncviewer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
steven@steven-laptop:~$ vncpasswd
Password: 
Verify:   
steven@steven-laptop:~$ tightvncserver
xauth: (argv):1:  bad display name "steven-laptop:2" in "add" command
Found /usr/share/tightvnc-java for http connections.

New 'X' desktop is steven-laptop:2

Starting applications specified in /home/steven/.vnc/xstartup
Log file is /home/steven/.vnc/steven-laptop:2.log

OK I don't know what I did wrong.  I have a desktop with all my audio/video files. Right now I access it by going to places > network > windows network > name of network > name of desktop > name of shared folder > audio/video file. When I open the audio/video file totem movie player opens. Yes I did try right click > properties > open with vlc player but it didn't work. When I opened the vlc media player under places the network was not listed.Also remember the desktop is what I'm trying to access from the laptop. The laptop has ubuntu, the desktop is windows

---

### Post by cecure on 2008-01-17
Alrighty, sorry if I got you confused.  

To get a remote desktop connection to your windows PC.
In a terminal in ubuntu run the command ```
xtightvncviewer
```
In the left corner of your screen a box will open that says "VNC Server: "
In that box enter the name of your server (you may have to look at your windows server configuration to determine its name) and press enter.
Another window should appear that prompts you for the password you use for your tightvnc on windows.
Once you press enter, a window should appear in ubuntu that has windows running in it.


As for the videos I would like you to see if you can open one video file in vlc and then we can work from there.

Go to places > network > windows network > name of network > name of desktop > name of shared folder and right click on an avi file, on the menu that comes up go to 'Open With' another menu will come out and then click on 'VLC Media Player'.  If this doesn't work tell me how far along it does work ie can you get to the Open With menu and VLC simply isnt there.

cheers

---

### Post by huntis619 on 2008-01-17
OK thank you I got the tightvnc working. I still can't get the vlc media to work. Well its installed but it does not show any of my network (desktop files). Again thank you for the help with the tightvnc. Also how do I THANK SOMEONE. So many people have helped me in the past 2 weeks and I would like to let it be registered that I appreciate yours and their help.

---

### Post by cecure on 2008-01-17
Have you been trying to open the files from within VLC?  If so when I say to browse to the files from the filemanager.  As for thanking someone I am not exactly sure.

Good luck

---

### Post by Skylive on 2008-03-27
Hi,

I'm sorry if I hijacked this thread, but I'm having problems with Tightvncserver. Could someone give me the instructions to wipe all traces of tightvnc, so that I can start anew?

Otherwise, I currently have the following errors in my logs and I can't connect to my server. I'm using Xubuntu 7.10. Could someone help me to troubleshoot? I'm really new at this. Thanks! Log:

** (x-window-manager:5886): WARNING **: The display does not support the XRender extension.

** (x-window-manager:5886): WARNING **: The display does not support the XRandr extension.

** (x-window-manager:5886): WARNING **: The display does not support the XComposite extension.

** (x-window-manager:5886): WARNING **: The display does not support the XDamage extension.

** (x-window-manager:5886): WARNING **: The display does not support the XFixes extension.

** (x-window-manager:5886): WARNING **: Compositing manager disabled.
** Message: Querying Xkb extension
** Message: Your X server does not support Xkb extension
** Message: This build doesn't include support for XF86Misc extension
** Message: Querying Xkb extension
** Message: Your X server does not support Xkb extension
Xlib:  extension "RANDR" missing on display ":1.0".
Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".
The application 'xfce-mcs-manager' lost its connection to the display :1.0;
most likely the X server was shut down or you killed/destroyed
the application.

(xfce4-terminal:5885): Gdk-WARNING **: GdkWindow 0x1400048 unexpectedly destroyed

(xfce4-terminal:5885): Gdk-WARNING **: GdkWindow 0x140003d unexpectedly destroyed

(xfce4-terminal:5885): Gdk-WARNING **: GdkWindow 0x1400047 unexpectedly destroyed

---

