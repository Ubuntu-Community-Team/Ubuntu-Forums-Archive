---
title: "KNetworkManager: 1-click enable/disable wireless?"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by UJoe4 on 2007-07-01
Hi:

Using Kubuntu Feisty, I'm accessing my wireless connection through KNetworkManager. But I'm getting tired of right-clicking on the KNetworkManager icon to bring up a pop-up menu, hovering on "Options", and carefully moving the mouse over and up to the top of the second pop-up menu every time I want to enable or disable wireless! Is there any way to either:

1) Move the KNetworkManager Enable/Disable wireless icons to a more convenient place, like the Quicklauncher or desktop; 

2) Assign keyboard shortcuts to these tasks; or

3) Write a script to do them automatically (which I could then create an icon for). Nothing I've found on the web has worked for me... It mostly seems to involve "echo -n [3 for off, 0 for on] > /sys/class/net/[my-device]/device/power/state", which always returns "echo: write error: Invalid argument".

"ifconifg [my-device] down" works to disable, but while "ifconfig [my-device] up" technically "enables" it, it doesn't automatically log on to my preferred network, which is what the KNetworkManager icon does. So assuming I can't move that "enable wireless" icon somewhere more sensible, how do I find out exactly what commands KNetworkManager is executing when I click on it?

Or of course any other ideas anyone might have. I don't have a hardware Wireless switch BTW.

Thanks!

---

### Post by UJoe4 on 2007-07-03
I didn't have any luck finding a one-click enable/disable wireless solution either in KNetworkManager or in GNOME's network manager, but I did manage to come up with a script that almost works:
> # Check if a temporary file exists
if test -e /somedir/iswirelessup  
then

# If yes, delete it and disable wireless
rm /somedir/iswirelessup
ifdown eth0
else

# If no, create it and enable wireless
echo > /somedir/iswirelessup
ifup eth0
fi
This works when I call the script from the terminal using "sudo", or from a root terminal (sudo -i). The problem is that when I put a launcher for it on my taskbar (which was the whole point), it doesn't work because as "myself" I don't have adequate permission to do whatever it is that "ifdown" and "ifup" do. So how do I either:

1) put an icon on my taskbar that will execute as root without having to enter a password each time; or

2) change it so that "myself" has permission to run ifup and ifdown?

---

### Post by UJoe4 on 2007-07-03
Followed some advice from an old thread and it's working now. I just had to add this line to the end of /etc/sudoers (of course, always be very careful when editing that file!):

myusername ALL=NOPASSWD: /somedirectory/myscript.sh

What that does is allow the user "myusername" to sudo the command /somedirectory/myscript.sh without entering a password (while still requiring a password when sudoing any other command).

So then put something similar to the script from the previous post in /somedirectory/myscript.sh, then put a launcher on your panel to call the command "sudo /somedirectory/myscript.sh", and that works. Single click on the icon to enable wireless and log on to the network, single click on the same icon to log off. All without a password.

Now the only thing left to figure out is how to display some sort of notification on the panel in case I forget whether I'm connected. (Like how network manager programs running in the system tray change their icon depending on whether they're connected or not.) I tried doing it this way: Have the icon on the panel point to (say) currentstatus.png, then have my script "cp connected.png currentstatus.png" when connecting and "cp disconnected.png currentstatus.png" when disconnecting. But of course that doesn't work because the panel doesn't refresh immediately, so changing the icon file won't translate into an actual change on the panel.

Anyone have any suggestions for this that don't involve a killall for the entire panel & desktop? I'm primarily using Xfce now, but I have all three desktops installed so ideas for KDE and GNOME are welcome too. Even if it's not something as nice as actually changing the icon, anything that makes a reasonably appropriate change to the panel immediately and can be called from a shell script would do. (I.e., run some sort of program that doesn't do anything except place an icon in the system tray, then the icon disappears when the program exits.)

---

### Post by UJoe4 on 2007-07-05
Found it. It's quite an ugly workaround, but it does what I wanted it to.

First get a program called "alltray" (sudo apt-get install alltray) which allows any GUI program to be "docked" to the system tray (the area on your panel where running applications like network managers put their icons, typically on the bottom right of the screen). Then in the script, right after enabling the wireless card, have alltray open any small-footprint application directly to the system tray, using whatever wireless-themed custom icon you want. (I chose mousepad, an even smaller application would be better.) Then, after disabling the card, have it "killall alltray" (or killall the application itself if you'll be using alltray for other programs too).

So now, clicking the "toggle wireless" icon will enable wireless and put the reminder icon in the system tray, and clicking the "toggle wireless" icon again will disable wireless and remove the system tray icon. All without the user ever having to know that the wireless reminder icon was actually a minimized copy of mousepad.

So, exactly what I wanted! Seems like a lot of work for something that I think should have been included in the GUI network managers to begin with, but anyway... Also, you have to make another change to /etc/sudoers so that you'll be able to launch the alltray application from your "sudo myscript.sh" icon: add *,env_reset,env_keep+="DISPLAY HOME XAUTHORIZATION"* to the end of the Defaults line. So the line would look something like:
> Defaults !lecture,tty_tickets,!fqdn,env_reset,env_keep+="DISPLAY HOME XAUTHORIZATION"
*(Edited: There's no space in the middle of "DISPLAY", that's just how the forum formatted it.)* Always keep in mind when editing the sudoers file that the slightest punctuation or spacing error can completely lock you out of your system, so be sure to back it up beforehand and be familiar with how to log in using recovery mode, just in case. Or use visudo, which I think won't allow the file to be saved if it's not formatted properly.

So the script will look something like this (works in KDE, GNOME, or Xfce):
> # Check if a temporary file exists
if test -e /somedir/iswirelessup 
then

# If yes: Delete it, disable wireless, remove tray icon
rm /somedir/iswirelessup
ifdown eth0
killall alltray
else

# If no: Create it, enable wireless, put icon in system tray
echo > /somedir/iswirelessup
chmod ugo=rw /somedir/iswirelessup
ifup eth0
alltray mousepad -i /somedir/myicon.png

fi
BTW, does anyone know what exactly it is that that sudoers line does? I assume it's to allow users other than your main user (such as root) to run GUI programs during your session. If that's not generally a good idea, any suggestions on a better way to accomplish the same thing?

---

