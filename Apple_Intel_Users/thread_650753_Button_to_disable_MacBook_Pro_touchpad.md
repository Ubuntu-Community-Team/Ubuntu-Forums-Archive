---
title: "Button to disable MacBook Pro touchpad"
date: 2007-12-26
forum: Apple Intel Users
---

### Post by self-defence on 2007-12-26
Hi,

I was wondering if there is any way that I could setup my Ubuntu so that if I plug in my mouse or if I get a bluetooth mouse the touchpad is deactivated.
Or if that can't be done if I could just setup a button (like F12) to turn on and off the touchpad.

I know it's a stretch, but if anyone has got any ideas their welcome.

Thanks for the help and bye.

---

### Post by wh0rd on 2007-12-26
Here's a great tutorial to do just that:

[http://lifehacker.com/photogallery/Top-10-Gnome-Tweaks/2424591](http://lifehacker.com/photogallery/Top-10-Gnome-Tweaks/2424591)

---

### Post by self-defence on 2007-12-28
Cool thanks for the link. At least now the pad is inactive when I'm typing so thanks. :)

Bye

---

### Post by russo.mic on 2007-12-29
You could fairly easily write a simple script to do just with with synclient.

---

### Post by self-defence on 2007-12-29
You mean something in the line when I press F12 it runs a script that checks if pad is on or off and does the exacts opposite? Ok the first part I'm parity sure I know how to do and the last part also (what command to run if pad=0 ... synclient something=1 else if pad=1 synclient something=1) but I have no idea on exactly how I would do this.
Any suggestions?

Thanks for your help. :)

Bye

---

### Post by Arthur Archnix on 2008-01-21
I just posted about this here: [http://ubuntuforums.org/showthread.php?p=4177125#post4177125](http://ubuntuforums.org/showthread.php?p=4177125#post4177125)

I suppose the auto-disable might not work with a blue tooth device mouse, but you could always just create a second shortcut to disable the mouse, like <shift>F10 enables touchpad, <Control>F10> disables it. More info in the link above.

---

### Post by self-defence on 2008-01-21
Cool, thank you for the info.
It's exactly what I need. :)

Good night

---

### Post by freejonah on 2008-02-14
this is my first posting. I just got my first Macbook Pro dual booting with Ubuntu, and I love it. The only thing that has driven me crazy has been this Touchpad. I've been wanting to turn it off forever, so my friend showed me this forum, and I found your posting.

I added the line to xorg.config, and dropped a variation of your syndaemon command into my .tcshrc:

***/usr/bin/syndaemon -d -i 100000***

This disables the touchpad for about 27 hours ( a long time ) after you first stop typing. By the way, it looks like tapping on the big touchpad button reactivates it until the next time you type. That's a nice safety. 

Also, it seems like if you're really interested in kicking the touchpad out of the park for good, you can add this option to the synaptics driver:

***Option          "TouchpadOff"          "1"***

---

### Post by cyberdork33 on 2008-02-14
Make it automatic when plugging unplugging a mouse:
[http://linuxtidbits.wordpress.com/2007/10/27/switch-automatically-mouse-and-touchpad/](http://linuxtidbits.wordpress.com/2007/10/27/switch-automatically-mouse-and-touchpad/)

---

### Post by self-defence on 2008-02-15
Cool I'll give it a try when I get a few moments of spare time. For now the not active when typing thing seems to be working quite ok for me since I most had problems with the touchpad when I was typing.

Bye

---

