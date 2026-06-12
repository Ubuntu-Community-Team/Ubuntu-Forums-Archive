---
title: "Simple VNC Guide"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by x1101 on 2008-01-30
Between Reading a few different posts on different forums about this, here is a little guide I put together along with a few scripts, that will allow you to install vnc-server/viewer, and set them to run a second desktop on a virtual display (I use :2 because for some odd reason :1 was inaccessible, probably because of something I was doing while working on this). So here is the Install guide, and the scripts that I wrote to make starting the vncserver/client a breeze

To get a second desktop running on display 2 via vnc with re-usable sessions

1. Enable XDMCP (this might not be needed, I don't know)
System->Administratio->Login Window
     [Remote tab]
	make sure the Style field is not set to "Remote Login Disabled"
	click "Configure XDMCP" button
		make sure "Honor Indirect Requests" is checked

2. Install vnc4server 
Code:
sudo apt-get install vnc4server 

3. Set the VNC password (this again might be done differently)
Code:
sudo vncpasswd

4. Install xfce4 to use on second desktop (or pick Desktop Manager of 
your Choice)
Code:
sudo apt-get install xubuntu-desktop

5. Setup ~.vnc/xstartup
Copy this into your ~.vnc/xstartup
Code:
#!/bin/sh

# Uncomment the following two lines for normal desktop:
#unset SESSION_MANAGER
#exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
#xsetroot -solid grey
#vncconfig -iconic &
#xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &

#this might start xfce
xfwm4 2> /dev/null &
xfce4-panel 2> /dev/null &


6. Create a script to start the vnc4server
Copy this into a file and the chmod +x it

vnc4server :2 -name Test -depth 16 -geometry 1024x768

7. Integrate the above script into startup
System->Prefrences->Sessions
	[Startup Programs]
		"Add" button
	launch the above script, name and comment it how you like

8. Connect to your new work space!
vncviewer :2 (from your own computer)
		or
vncviewer (ipaddress):2 (anywhere else)


9. Enjoy

---

### Post by dgavenda on 2008-02-08
x1101,

First off, thanks for adding this documentation.  It does work.

I would like to be able to use the Xsession that is already being displayed on my LCD.  For example, if somebody IM's me and I vnc to that box, I want to be able to see that IM.  It works that way in ubuntu already.  

Any ideas how this is done?

Thx,
Dan

---

