---
title: "How to remove enlightened XFCE and get back XFCE"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by yb1011 on 2006-02-16
hey guys,
I followed this thread [here]("http://www.ubuntuforums.org/showthread.php?t=101066&highlight=xfce+enlightened") and somehow managed to screw everything up. I did the following to get enlightened XFCE

> I. Getting Enlightenment

This is the primary step, of course. To obtain Enlightenment, you've got a couple options; there 
are currently two versions available. First, you have available Enlightenment DR16, 
which is fairly lightweight, looks good, and is currently more stable than the other 
version, E17. E17 is heavier, looks pretty fine, but I've had bad luck running it. 
My suggestion is to go with DR16 for the time being; it crashes less often. To 
get DR16, ensure you have the Universe repository enabled .Open up Synaptic, 
find the package named "enlightenment" and choose to install it. Getting E17 
is slightly more complicated, but still easily achieved; to do so, may I suggest 
Aboe's Howto? Enlightenment also has several great utilities available for it, which 
are all available via Shadoi's repository (Covered in Aboe's howto).

II. Autostart

Mhancoc7 came up with this one. He's a genius for coming up with it; it's simpler 
than both my methods and works better than the next one I came up with, which 
is why I put it first. This one uses the stock XFCE setup, but makes a few slight
changes. Open up a terminal and type in

cd ~/Desktop

Which will bring you to the Desktop directory. once there, type in

mkdir Autostart

The directory Autostart is used by XFCE and runs any executables it finds in there 
on start up; hence the name. Once this has been completed, enter the directory 
by entering into the terminal

cd Autostart

and create a new file. It doesn't particularly matter what it's called, since XFCE 
will run any executable file in the Autostart directory. For this example, I chose
to call it starte. Put the following into the file:

#!/bin/sh

enlightenment &

and save it. Make it an executable script with the following:

chmod 0775 starte

Now, enter the following command into the terminal:

killall xfwm4 xfdesktop

Which will kill the XFCE window manager and the XFCE desktop manager; these 
both interfere with the proper functioning of Enlightenment. Log out and save 
session.

Now how do I remove this and get XFCE back? any ideas.Please suggest..

---

### Post by maitreya on 2006-02-16
rm ~/Desktop/Autostart/starte (or the filename that you used)
killall enlightenment
xfwm4&
xfdesktop&
exit

logout and select save. log back in.

---

