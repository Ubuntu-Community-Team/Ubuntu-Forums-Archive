---
title: "gcompris problem"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by ljpm on 2006-09-22
Hi all,

I am a complete noob so please go easy on the techno talk when trying to assist. (I just installed UBUNTU, and managed to get the video working, last week)

I am having a problem with gcompris. When I start the program my monitor gets an out of range error. I can hear gcompris running, I just can't see it. The error on the monitor is 

out of range
input 1 : DVI-D
53.5 kHz/85Hz

I have an ATI on board video card (Xpress 200 series).
A Sony SDM-HS75P

The video problem resolves itself when gcompris is force quit.

I am using the DVI cable.

Please help.
and thanks in advance.

---

### Post by ljpm on 2006-09-22
Bump

---

### Post by ljpm on 2006-09-25
sorry for bumping again but the activity in this forum pushes posts off the first page way to fast.

---

### Post by ljpm on 2006-09-25
Hi, its me again.

I just tried to run gcompris from terminal and got the following error.

** (gcompris:7438): WARNING **: config_file /home/*******/.gcompris/gcompris.conf
** Message: gcompris_set_locale ''


** (gcompris:7438): WARNING **: Requested locale '' got 'en_US.UTF-8'
open /dev/sequencer: No such file or directory
Opened audio at 44100 Hz 16 bit stereo, 2048 bytes audio buffer
__main__:1: DeprecationWarning: Module gnome.canvas is deprecated; please import gnomecanvas instead

EVENT
============================================================

Anyone able to help?

---

### Post by ljpm on 2006-09-25
I have figured out what the problem is. gcompris resets the screen resolution and the refresh rate when the program starts. Unfortunately the default, as well as secondary resolution, reset the refresh rate to 85Hz as well. my monitor has a max refresh rate of 75Hz and therefore shuts off. (I figured this out by hooking up my old CRT monitor.)

Still hoping someone can help solve this problem.  (I don't want to have to switch back to a CRT from my nice new LCD just so my daughter can play gcompris)

---

### Post by lduperval on 2006-09-26
Ha, I have a similar issue here. Whenever I start gcompris, X shuts down and I am brought to the login window. I am hoping someone has an answer also.

L

---

### Post by bulldog on 2006-09-26
If your talking of **gcompiz** I can tell you to uninstall it.

It's a part of Xgl/compiz for the Desktop.

But there are some major changes going on and you can't use gcompiz anaymore.

The packets you need are offline for the moment and all the tutorials to install compiz will be outdated I guess.

Take a look here to see more info.

[http://forum.beryl-project.org/index.php](http://forum.beryl-project.org/index.php)

---

### Post by lduperval on 2006-09-26
No, I am talking about gcompris ([http://www.gcompris.net](http://www.gcompris.net))

Since I think I found where the problem lies, I am going to start a new thread for this.

L

---

### Post by bulldog on 2006-09-26
> **lduperval said:**
> No, I am talking about gcompris ([http://www.gcompris.net](http://www.gcompris.net))

Since I think I found where the problem lies, I am going to start a new thread for this.

L

I see,my mistake.](*,) 

Have no experience with it,so can't help you.

---

### Post by bluefrog on 2006-09-26
for the coming back to login screen that was a bug, but it has been addressed, you must be using an old gcompris version (old as of a few months).

regarding the refresh rate sry don't know.

James

---

### Post by moma on 2006-09-26
Run gcompris in window mode.

$ [COLOR="Green"]gcompris --window [/COLOR]

or do not change the resolution
$ [COLOR="Green"]gcompris --noxrandr[/COLOR]

For other options
$[COLOR="Green"] gcompris --help[/COLOR]
--------------------------------------------------------------------------------

This is how to change the language from command line. Eg. Start gcompris in Norwegian language
$ [COLOR="Green"]LANG=nb_NO  gcompris --noxrandr[/COLOR]
I think you can change the language in gcompris settings too.

---

### Post by ljpm on 2006-09-26
Thanks, will try as soon as I get home.

---

