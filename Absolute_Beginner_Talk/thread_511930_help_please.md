---
title: "help please"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by hnoverian on 2007-07-28
this is my maiden question to the forum could anybody help me please my screen resolution is 1600*1200 while i can only use 1280*1024. i am a newbie linux could anybody tell me the commands or what to do, appreciate your great effort.:(

---

### Post by por100pre1 on 2007-07-28
Try first System> Preferences> Screen Resolution.

Let's see if that helps...

By the way, welcome to the forums.

---

### Post by hnoverian on 2007-07-28
yes i did this but my resolution is not on the list:(

---

### Post by por100pre1 on 2007-07-28
Next step: please read [this]("http://ubuntuforums.org/showthread.php?t=83973").

Hope that helps.

---

### Post by nichipet on 2007-07-28
What model computer/monitor are you using? If it's integrated Intel, you may need the 915resolution program, which you can get from Synaptic. There's also a command line program you can run, which is in the thread por100pre1 posted.

---

### Post by lambros on 2007-07-28
> **hnoverian said:**
> this is my maiden question to the forum could anybody help me please my screen resolution is 1600*1200 while i can only use 1280*1024. i am a newbie linux could anybody tell me the commands or what to do, appreciate your great effort.:(

Just to clarify: do you have an LCD-based monitor whose native resolution is 1600x1200 ?  And the problem is, presumably, when you choose a resolution in Ubuntu, the choices only go up to 1280x1024 ?

See if this helps:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

If not, post back here with any questions you have.

Lambros

---

### Post by hnoverian on 2007-07-28
my monitor is dell and i use nvidea x4000:(

---

### Post by KyleBrandt on 2007-07-28
Quick Fix:

1. Backup Xorg file: sudo cp /etc/X11/xorg.conf /etc/X11/xorgbackup.conf

2. Edit Xorg File: sudo nano /etc/X11/xorg.conf
Find Section Screen, there should be a bunch of resolutions under it, add yours and make sure you are keeping the same syntax as the others.  Exit and Save.

3. Restart the X server: Ctrl-Alt-Backspace, if it doesn't start properly, hit Ctrl-Alt-F2, restore your xorg file by sudo cp /etc/X11/xorgbackup.conf  /etc/X11/xorg.conf   (Make sure you don't get this backwards).  and run startx or restart the computer.  Then ask for more help

---

### Post by hnoverian on 2007-07-28
hi KyleBrandt i followed the instructions you gave me and finally i got the 1600*1200 but when i use it the screen tabs is hidden so i tried the refresh rate 55 mh but the system freezes and i have to restart it again and one more time . then i returned to my previous resolution but i got another problem in the tab above i found that leave button and the icon of the net and the icon of the volume are missing any help please:(

---

### Post by fistfullofroses on 2007-07-28
Everyone is giving easy ways to do this, but the real way I know of is somewhat faster. Once your computer boots into what would be the graphical environment press ctrl+F3 this will put you into a command line interface. From there feed the machine your user name and password. Then type **sudo -s** the $ on the screen should change to a # sign after you once again type your password. After this type **nano /etc/X11/xorg.conf** scrool down until you see a whole bunch of modes with resolutions. Delete all of the various resolutions given except for 1024x768 if that is the one you wish to use. When you are done press ctrl+o press enter then press ctrl+x and you will be back at your command line. press ctrl+F7, then ctrl+backspace. The graphical environment should restart in your requested resolution.

---

### Post by KyleBrandt on 2007-07-28
> **hnoverian said:**
> hi KyleBrandt i followed the instructions you gave me and finally i got the 1600*1200 but when i use it the screen tabs is hidden so i tried the refresh rate 55 mh but the system freezes and i have to restart it again and one more time . then i returned to my previous resolution but i got another problem in the tab above i found that leave button and the icon of the net and the icon of the volume are missing any help please:(

I'm sorry but I am having a little bit of trouble trying to figure out what your problem currently is now from your description.  To change the refresh rate you are going to want to make sure you use the correct horizontal and vertical sync rates from your monitor's manual in the xorg.conf file.  By tab maybe you mean the gnome-panel? (What would be the start bar in windows).  I have never have part of that cut off so I am not entirely sure how to fix that.  Are you sure your monitor and card support that resolution?

Also, maybe your monitor needs to be adjusted from the monitor itself after changing the resolution?  You would change placement and size of the screen from the adjustments on the monitor itself once you are in the new resolution.  This could be likely with a crt monitor.

---

