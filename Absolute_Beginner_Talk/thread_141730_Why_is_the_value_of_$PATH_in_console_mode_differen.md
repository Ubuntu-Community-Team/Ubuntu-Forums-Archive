---
title: "Why is the value of $PATH in console mode different from the $PATH in xterm emulator?"
date: 2006-03-08
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-03-08
When in console mode (x-window-system is not loaded), 

root@myserver:~#echo $PATH

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11

However, when I'm in the window manager (fluxbox) and I  open a xterm window, my $PATH has a different value.

root@myserver:~#echo $PATH

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/ sbin:/bin:/usr/bin/X11

The difference is the additional space between the slash (/) and sbin. That causes /sbin to be missing from my PATH.

So any attempt to install package will give the error 

dpkg: ldconfig not found on PATH
dpkg: start-stop-daemon not found on PATH

What is causing the additional space between the slash (/) and sbin in the PATH only when in xterm emulator?

Any advice would be greatly appreciated.

Thanks.
PS. Happens on both machines I installed x-window-system, fluxbox, xterm.

---

### Post by 5-HT on 2006-03-09
Not sure why the space got in there for interactive non-login shells, but there are different config files for login vs non-login shells. This can explain why the problem is only affecting xterm and not the virtual terminal.

Maybe some setting in fluxbox's config is trying to overide?

What about appending this to the user's ~/.bashrc file:

```
 export PATH=$PATH:/sbin 
```

That should be sourced for interactive non-login shells (you'll have to restart xterm for it to take effect).

I thought that if you don't specify any $PATH changes in either a user's .bashrc or /etc/bash.bashrc,  whatever is specified in /etc/profile (for login shells) would be used for non-login ones...but from what you're describing, unless you did change one of the rc files, it looks like that may not be the case. 

Maybe someone else who knows of any other file that could be getting sourced to cause this will let you know of what that may be (to find out where that space is lurking), but adding /sbin as I described above should get it working. 

Hope that helps

---

### Post by Akhran on 2006-03-09
For testing purpose, I installed rxvt and eterm. rxvt has the same error but eterm displays the correct $PATH value ( no extra space ).

In short, $PATH shows the correct value in eterm, but incorrect in rxvt and xterm on both machines.

Thanks !

---

### Post by 5-HT on 2006-03-09
That's weird how different paths are showing up for the various teminal emulators...good news if you like eterm though.

Did adding that line to .bashrc help out for the others at all?

---

