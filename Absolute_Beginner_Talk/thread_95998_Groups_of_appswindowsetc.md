---
title: "Groups of apps/windows/etc"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by duus on 2005-11-27
Hi.  I don't know what this is called or how to do it, but I like to have the following apps open together in these locations:

bundle 1: Java Coding) Have two xterms open on workspace 1, eclipse on workspace 2, firefox on 3, and my IM on 4.

bundle 2: LaTeXing) have emacs on 2 and my dvi viewer on 3, firefox on 4.

Is there a program that I can name these bundles and then just call the bundle?  I thought maybe that's what "sessions" would be under Preferences/Sessions but, if I'm right, I can't seem to make it work.

Thanks!

---

### Post by redactech on 2005-11-27
I tell you what I do 

I put each "bundle" in a virtual desktop (in gnome >> bottom right)

then I right click on virtual desktop and rename the desktop (instead of desktop 1, 2 or 3)

---

### Post by duus on 2005-11-27
[QUOTE=redactech]I tell you what I do 

I put each "bundle" in a virtual desktop (in gnome >> bottom right)

then I right click on virtual desktop and rename the desktop (instead of desktop 1, 2 or 3)[/QUOTE]

thanks.  that's not quite what I meant...i use the gnome virtual desktops and I like to spread across them...when i said "workspace" i guess i meant "gnome virtual desktop."

What I would like is to have one button (or script, or app, or whatever) that will open a set of apps and put their windows in certain virtual desktops.  Back when I used fvwm2 (a simplier time :) ) it was easy to use the command line to describe where you wanted an app to open w/r/t the virual desktop; then I would write a little script that just listed the apps and where i wanted to open them.  but uh i don't know how to do that with an arbitrary app or with the gnome virtual desktops.

Does anyone do this?  have one app that opens & places the 5 applications that they always use for a certain activity?

---

### Post by jrib on 2005-11-27
You may want to look into devilspie.  It will let you control where windows go when you open them.  There is a package of devilspie available in the repos (although the code has since been rewritten from scratch in the latest versions).  There is a [howto]("http://ubuntuforums.org/showthread.php?t=75749") on the forums so you can see the functionality it provides.  You may have to do some scripting so that running a single command will open all of those programs together.

---

