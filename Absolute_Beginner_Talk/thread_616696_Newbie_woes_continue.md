---
title: "Newbie woes continue"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by keno.mentor on 2007-11-18
Thanks to all you who keep trying to help me with these endless problems :(

I have now re-installed kubuntu after messing something up with the xorg thing.  I then used dpkg-reconfigure xserver-xorg to try to set the resolution to 1280x800.  Now it boots to a text based screen.  The weird thing is, the splash screen is always in perfect resolution (?)

Now what? *sigh*  I'm going to have to re-install again, aren't I?

Thanks to anyone who can help.

---

### Post by Scunizi on 2007-11-18
Reinstalls typically are not needed to fix the gui problems.  The system base is basically the same as Ubuntu with Gnome instead of KDE like Kubuntu.  However I think that the best way you might want to approach this is with live help that is Kubuntu oriented.. 

Since you have a text login screen you can install a text based IRC client.  After logging in type "sudo apt-get install irssi".  Now I don't know which terminal you use on a text login, however remember this, Ctrl+Alt+F2 through 6 are all terminals or tty's.  F7 is typically the GUI.  I mention this because when you load the IRC client it will take the entire screen and you'll need a way to get away from it to type commands into another terminal when receiving help in the IRC channel.

Now load irssi by typing.. ta da.. irssi.  Now you have to log into the right server.  Type /server irc.freenode.net.  It will buzz and whirr and give you something on the screen.  Now type /join #ubuntu for the ubuntu channel.  It's the most active.  You could also type /join #kubuntu or /join #desktop-effects.  In fact you can do all of these one right after the other.  To change which channel you're looking at use Alt+2 ro 3 or 4 etc.

Now if your original xorg worked and you want to get back to that point, look for the backup of it.  The system will typically create one for you.  type "ls /etc/X11/xorg* " to see a list of xorg files.  Or better yet change into that directory first by typing cd /etc/X11.   Now "ls" to get the directory.  You should see several xorgs.  Look for one that appears to be the original backup.  You can always look in the files and edit them by "sudo nano xorg.conf " or what ever the file name is.  Remember CAPS and small case make a difference.

---

### Post by fabiomb on 2007-11-18
can you explain more?

if you are in a terminal without graphics enviroment, maybe you have problems with xorg.conf file.

so, you can log in (user-pass in the terminal), or open another terminal (CTRL+F1/F2/etc) and log in

then you can reconfigure with the same 
dpkg-reconfigure xserver-xorg

if you want to see the xorg.conf and edit manually (it's dangerous)

you can type

sudo nano /etc/X11/Xorg.conf

maybe if you only change the video driver to "vesa" you can acces in graphic mode.

---

