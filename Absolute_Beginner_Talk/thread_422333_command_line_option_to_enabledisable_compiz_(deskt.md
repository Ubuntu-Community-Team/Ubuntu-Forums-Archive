---
title: "command line option to enable/disable compiz (desktop effects)"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by jr0ck on 2007-04-25
Hello all,
I sure hope someone can help me. I have a Toshiba R15 tablet PC with Ubunut 7.04 (Feisty) installed. I got a script from a post elsewhere to have my screen automatically rotate 90 degrees when I switch my laptop to tablet mode. It works wonderfully and flips the screen back to normal resolution once I flip the lid back up. The only problem is that desktop effects (again, I'm using Compiz) doesn't work in portrait mode, so I have to disable it first, before rotating my screen. So, here's my question:

Is there a command-line option that is the equivalent of doing: System -> Preferences -> Desktop Effects, then enabling/disabling Desktop Effects? If there is, I want to add it to my screen rotation script so that Desktop Effects are disabled when switching to portrait mode, and re-enabled when going back to landscape. Thanks in advance for any help!

BTW, for those wondering what the script is, I got it from here:
[http://i-otto.blogspot.com/2006/09/toshiba-portg-m200-with-ubuntu.html](http://i-otto.blogspot.com/2006/09/toshiba-portg-m200-with-ubuntu.html)

---

### Post by viciouslime on 2007-04-25
"metacity --replace" will switch compiz off. Also, "compiz --replace" will switch it back on for when you flip the screen back :)

---

### Post by jr0ck on 2007-04-25
I think this may be just what I needed. I'll test it out in my script later tonight, hopefully, and report back. Thanks a bunch, I'll let you know!

---

### Post by jr0ck on 2007-04-26
Okay...I tried it and it ALMOST worked. If I put it in my script, it disables compiz but doesn't continue with the rest of the script. I entered the command into a terminal window to test it and it gives this error:

$ metacity --replace
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_on_all_workspaces"

And it won't continue from that error. It sits there as if waiting for me to type something else or some other option. If I do Ctrl C to kill it it then gives me a prompt back. So, in my script it just hangs because of that error. I have no idea what that error means exactly. Any ideas?

EDIT: Just wanted to add that if I disable Desktop Effects via System -> Preferences -> Desktop Effects and then I type in a terminal window:
$ compiz --replace
I get the following message:
/usr/bin/compiz.real: GLX_EXT_texture_from_pixmap is not supported by direct rendering context, trying indirect rendering context instead
/usr/bin/compiz.real: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
/usr/bin/compiz.real: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu
/usr/bin/compiz.real: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu
/usr/bin/compiz.real: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png

Isn't there any way to know what clicking "Enable Desktop Effects" is doing exactly? Whatever it is doing it works, I just need to know how to do it from the command prompt (for my script). Thanks again in advance for any help.

---

### Post by Lesterchakyn on 2008-01-14
*Bump*
Anything on this?
It should be great to have this option for suspend/hibernate scripts

Thanks!

---

### Post by lalitpatanpur on 2008-02-02
Think that I may have the answer for you:

I was trying to start a Java launcher from the menu and was having all sorts of issues, but finally worked them out with a shell script (my first).   I was trying to open JDarkRoom from the launcher, but compiz would leave the top and bottom bars.

I tried disabling compiz with a command line and had the same terminal freeze as yourself.   But then this finally worked:

metacity --replace ccp &

...followed by the commands you want.

Hope this helps.

---

