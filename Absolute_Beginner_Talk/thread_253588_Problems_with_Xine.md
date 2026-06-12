---
title: "Problems with Xine"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by sam sarnie on 2006-09-08
I'm having a probelm with xine.  I ran xine-check and got this:-
-----snip------

[ hint ] multiple xine executables found in your PATH
        I have found more than one occurance of 'xine' in your PATH:
        /usr/bin/X11/xine 
        /usr/bin/xine
        You have probably installed xine-ui more than once, or the
directory
        where you have installed xine occurs more than once in your
PATH.
        Technically, this is not really a problem, but it's probably 
        somewhat confusing, as it's not obvious, which xine you're
using.
        You should probably uninstall the copies that you don't use...
        Further tests assume, you're using /usr/bin/X11/xine 
        press <enter> to continue...

[OUCH!!] no xine-config on this machine.
        This means that xine-lib is either not installed
        or it is installed in a very unusual place.
        So you should probably install xine-lib before running 
xine-check...
        press <enter> to continue...

[ hint ] unable to determine plugin directory
        I could not determine your plugin directory. That would be much
easier
        if you had xine-config installed (see message above)... 
        Note that I could not check your xine plugins.
        press <enter> to continue...
I've tried removing and re-installing but get the same message.  How can i remove it totally and start again when it says i have allready removed it?
Please help!

---

### Post by Kobalt on 2006-09-08
Hello,

First of all : how did you install xine : via Synaptic, apt-get or aptitude ? 
Have you tried selecting "complete deletion" (the last option in the list of Synaptic when you click on the program box) ? 

Cheerios !

---

### Post by sam sarnie on 2006-09-08
Thanks for replying:
I tired the complete removal with synaptic but when i re-instsll it still says there is 2 xines in /usr/bin/X11/xine and /usr/bin/xine.  Also it says xine-config is not installed but i can't find it to download it.

---

### Post by deb on 2006-11-02
I am also having the same problem as sam sarnie with xine. After loading xine configs and almost everything related to xine including libdvdcss2, xine is unable to play DVD. xine-check still finds multiple executable and xine config in my PATH. 

Though Totem is working the picture quality is not good and I like xine a lot.

PLEASE HELP!_ somebody :(

---

