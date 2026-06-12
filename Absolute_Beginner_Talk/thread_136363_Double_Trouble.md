---
title: "Double Trouble"
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by Error_Msg on 2006-02-25
I was having problems using Xine in Xfce 4. Losing sound, freezing image, and error messages. One of them recommended to run xine-check, so I did. This are some of the diagnostics:
[ hint ] multiple xine executables found in your PATH
         I have found more than one occurance of 'xine' in your PATH:
         /usr/bin/X11/xine
         /usr/bin/xine
         You have probably installed xine-ui more than once, or the directory
         where you have installed xine occurs more than once in your PATH.
         Technically, this is not really a problem, but it's probably
         somewhat confusing, as it's not obvious, which xine you're using.
         You should probably uninstall the copies that you don't use...
         Further tests assume, you're using /usr/bin/X11/xine
         press <enter> to continue...
[OUCH!!] no xine-config on this machine.
         This means that xine-lib is either not installed
         or it is installed in a very unusual place.
         So you should probably install xine-lib before running xine-check...
         press <enter> to continue...
[ hint ] unable to determine plugin directory
         I could not determine your plugin directory. That would be much easier
         if you had xine-config installed (see message above)...
         Note that I could not check your xine plugins.
         press <enter> to continue...

All the other parameters and tests were [ good ].
So I started investigating  /usr/bin and found that there is a folder in /usr/bin/X11 which is a link to folder /usr/bin.
Another piece of info that may be relevant or not, is that in my Xfce 4 menu>Office, Evolution is listed twice.
I am quite sure that I did not install any of the two programs twice, at least not voluntarily or knowingly.
I used to run Hoary, but I upgraded to Breeze not too long ago.
Somebody clue me in please!

E_M

---

