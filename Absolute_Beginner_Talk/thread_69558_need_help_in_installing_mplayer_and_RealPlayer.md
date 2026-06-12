---
title: "need help in installing mplayer and RealPlayer"
date: 2005-09-27
forum: Absolute Beginner Talk
---

### Post by psylvester on 2005-09-27
i need to install mplayer. when i try to install i get this

root@ubuntu:/home/sylvu # sudo apt-get install mplayer-386
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mplayer-386


i tried to install Realplayer, I downloaded RealPlayer10.bin, I installed, and i can see 
RealPlayer10 in "sound & video". But when i click nothing comes up. 

I dont know why, When i installed RealPlayer, it said installation success. But this is the Problem...
Im new to linux, Please help me with RealPlayer10 & mplayer.

thanks.
Prashanth

---

### Post by ngms27 on 2005-09-27
You need to remove two files ending *.swf from the realplayer plugins directory.

Don't ask me why but it works!

JonnyT

---

### Post by psylvester on 2005-09-27
There is no  *.swf files in RealPlayer/plugins

root@ubuntu:/home/sylvu/RealPlayer/plugins # ls *.swf
ls: *.swf: No such file or directory
root@ubuntu:/home/sylvu/RealPlayer/plugins #

---

### Post by Wolki on 2005-09-27
[QUOTE=psylvester]i need to install mplayer. when i try to install i get this

root@ubuntu:/home/sylvu # sudo apt-get install mplayer-386
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mplayer-386
[/QUOTE]

You need to enable multiverse in Synaptic. [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by psylvester on 2005-09-28
hey, thanks. I have done all these things. But i Need to Add REAL player & Mplayer.
Should I add the repository Information on synaptic ? If so what will be the Link i should give for RealPlayer & Mplayer.
The One Other thing I needed is, I need Warning on my Messenger window, when a new message comes. Like in Normal MSN, when a new mesaages comes the window Blink (if the window is minimised). In Gaim, it doesnt happen, I wont know If any new message comes, cauz there is No blink.!
Thanks For your time. And If you can help me in this, I can install in other machines as well. Because, Once we know ,everything can be done in ubuntu, then there is No need to use windows.
Other thing is that, we are using application that need Internet Explorer 5.5 or above, Mozilla cannot be used. So, is there anyway, we can use these kinds Of applications ? Anyway, Let me try mozilla's Updated Versions.
Thanks a lot Dude.
p.sylvester

---

### Post by Wolki on 2005-09-28
[QUOTE=psylvester]hey, thanks. I have done all these things. But i Need to Add REAL player & Mplayer.
Should I add the repository Information on synaptic ? If so what will be the Link i should give for RealPlayer & Mplayer.[/quote]

You don't need to give a link, just check the checkboxes in the repositories window. The link I posted contains a graphical tutorial. After that, just search for mplayer in synaptic and install one that works with your processor. Don't know about real player.
> 
The One Other thing I needed is, I need Warning on my Messenger window, when a new message comes. Like in Normal MSN, when a new mesaages comes the window Blink (if the window is minimised). In Gaim, it doesnt happen, I wont know If any new message comes, cauz there is No blink.!

Is in Breezy, so wait a little. Or install the relevant libs in hoary: [http://ubuntuforums.org/showthread.php?t=39776](http://ubuntuforums.org/showthread.php?t=39776)

>  Other thing is that, we are using application that need Internet Explorer 5.5 or above, Mozilla cannot be used. So, is there anyway, we can use these kinds Of applications ? 

You can try running IE in wine, or if you're willin to spend a little money on it Crossover Office. It should work without problems in C.O., don't know exactly about wine.

---

### Post by psylvester on 2005-09-29
Regarding the Gaim Messenger; I did 
sudo apt-get install --reinstall libwnck-common
wget [http://ftp.cs.umn.edu/pub/ubuntu/pool/main/libw/libwnck/libwnck16_2.10.0-0ubuntu1_i386.deb](http://ftp.cs.umn.edu/pub/ubuntu/pool/main/libw/libwnck/libwnck16_2.10.0-0ubuntu1_i386.deb)
sudo dpkg -i libwnck16_2.10.0-0ubuntu1_i386.deb

Its working to an extend. But this is not what MSN is doing, When i did this, If my chat window is minimised, and a new message comes - the chat widown pops-up.
So, If its minimised it Popsup. Else IF any new messages comes - it will stay minimised, till next message comes.
In short , I wont know if any new message comes, cauz it will stay minimised.

In shot - I want that Flashing for new messages. :( 
Is there anyway...?

---

### Post by Wolki on 2005-09-29
[QUOTE=psylvester]In short , I wont know if any new message comes, cauz it will stay minimised.
In shot - I want that Flashing for new messages. :( 
Is there anyway...?[/QUOTE]

If you already followed the howto, i'm not sure what's wrong; it worked for me in hoary. Windows will "glow" in the task bar when they want to draw attention, it's a very nicely looking effect.

Hm.. did you enable the notification plugin for gaim? You can do that in the gaim settings, then enable "set URGENT window manager hint" or something similar.

---

### Post by psylvester on 2005-09-29
i have Done that as well.. Enabled Notification !! 
I dont know whats wrong . Is there any Other messenger which i can install.
Thanks.
P.sylvester

---

### Post by Wolki on 2005-09-29
[QUOTE=psylvester]i have Done that as well.. Enabled Notification !! 
I dont know whats wrong . Is there any Other messenger which i can install.[/QUOTE]

I doubt another messenger will help here since it's a Gnome problem. There are of course other messengers, but it depends on hich service you want to access.

Did you also enable the "URGENT" WM hint?

My suggestion would be waiting for Breezy where it will work out of the box (at least it did for me). It'll be out in ~14 days.

---

### Post by psylvester on 2005-09-29
Anyway, Now it popsup. Atleast now i can see the New messages. It doesnt Blink .
Im planning to Install new messenger later. Please let me know If any new messenger is available.

thanks a lot.
Prashanth

---

