---
title: "Need a little help"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by doomedfire on 2008-03-30
I have several things i want to do.

1,Get my computer to be able to talk to my xfire friends. [DONE] 

2.Get my computer to be able to Connect to my Sansa view 8gb mp3 player

3. Use small words this is my first time using Linux and I'm thoroughly confused.

4. Get flash player to work so i can watch videos.

Thx in advance.

---

### Post by Dr Small on 2008-03-30
1.) I do not know if they have made Xfire for Linux, but if they have not, you could certainly try it in Wine.

2.) Have you tried connecting it to the computer?

3.) I think you ment, "Use small words" :D

Dr Small

---

### Post by Daveth on 2008-03-30
there is a plug-in for Pidgin and for Gaim which allows messaging to xfire friends- see here

[http://en.wikipedia.org/wiki/Xfire](http://en.wikipedia.org/wiki/Xfire)

You can find Pidgin or gaim in System/ admin/Synaptic package manager; the plugins are in the middle of the wikipedia page. Download the gaim...deb file for your version of Ubuntu, and right click and open with Gdebi to install it (by the looks of it) - probably an easier way which others may know

try altering the internal settings for your sansa, so it looks like a mass storage device

---

### Post by doomedfire on 2008-03-30
@Daveth: What do i do at :
[http://www.fryx.ch/xfire/](http://www.fryx.ch/xfire/)

deb file?

How do i edit internal settings?

@Dr small: I tried plugging it in nothing but having it charge, How do i install wine?

Got another question
4. Get flash player working to watch videos on youtube and veohhttp://ubuntuforums.org/editpost.php?do=editpost&p=4616652

Btw im running ubuntu 7.10

---

### Post by Daveth on 2008-03-30
if you go here

[http://gfire.sourceforge.net/snapshots/](http://gfire.sourceforge.net/snapshots/)

you will find this file

gaim-xfire_0.6.1~20071109-pidgin-2.2-gutsy1_i386.deb

download it, save it somewhere in your home directory. Then get Pidgin from the repository (system/admin/synaptic etc) and install that first. Then go to the downloaded file above, right click with the mouse, so you get a dialogue box, and find "properties" at the bottom. Open that tab and tick the box about allowing the program to execute, Then right click again and make for Open with Gdebi installer, and click on that. That should install the plugin for Pidgin. I think it is important to put Pidgin in place before the plugin, so do do this in the correct order.

For your mp3, you should have a settings menu somewhere- look for something that goes on about usb connections, and trying all the options- one should connect to your pc.

---

### Post by Daveth on 2008-03-30
assuming you are running Gutsy, of course! Just thought I'd check.

---

### Post by doomedfire on 2008-03-30
@daveth IT WORKED!! ty now then for my other 3 problems IF you dont mind still helping me :)

---

### Post by alzie on 2008-03-30
> 2.Get my computer to be able to Connect to my Sansa view 8gb mp3 player

According to a post at anythingbutipod.com gnomad2 should work with your player.  You can get gnomad2 using Synaptic Package Manager

I Hope this helps

[http://anythingbutipod.com/forum/showthread.php?t=25970](http://anythingbutipod.com/forum/showthread.php?t=25970)

---

### Post by doomedfire on 2008-03-30
When i opened Synaptic Package Manager i got this.

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

Thats new o.0 did i do something wrong?

EDIT: Fixed it with "Sudo dpkg --configure -a" in the terminal.

---

### Post by Daveth on 2008-04-02
my, you are getting good! 
Which web browser are you using then to watch flash stuff? Most have flash plug-ins. Head over to Synaptic (you know all about this now of course) and hunt out "flashplugin -nonfree" and install it. That should sort you out. 

Is your xfire messaging working then now???

---

