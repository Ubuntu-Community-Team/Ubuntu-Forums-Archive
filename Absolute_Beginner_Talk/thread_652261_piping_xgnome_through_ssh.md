---
title: "piping x/gnome through ssh"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by KCormier on 2007-12-28
Howdy all.  I'm piping X through ssh from one ubuntu 7.10 install to another.  Both laptops.  One wired 10/100, the other wireless g.  I ssh from my laptop into the server with X piping enabled.  I run gnome-session and I can see the gnome session from the server.  I do whatever I want to do and when i'm done I go to log out.  Once logged out my gnome session on my personal laptop is allll sorts of screwed up.  My windows no longer have status bars across the top so I can't move them, I can't close them if they don't have a menu.  My menu bar is really weird as well.  Normally windows open up below the menu bar, now when they open up they're covering it.  How do I get it to reenable my local gnome-session after closing the remote one?  Thanks!

Kevin

---

### Post by p_quarles on 2007-12-28
This isn't a solution so much as a workaround, but I would just restart Gnome. Ctrl-alt-backspace to log out, and then should initialize as it normally does. 

Like I said, it's a quick fix, and I'm sure there's a better way to prevent this problem from occurring in the first place, but I don't know it.

---

### Post by Dr Small on 2007-12-28
Run it all through Xephyr:
[http://ubuntuforums.org/showthread.php?t=620003](http://ubuntuforums.org/showthread.php?t=620003)

---

### Post by KCormier on 2007-12-28
thanks for the advice :)  After posting i found this [http://ubuntuforums.org/showthread.php?t=505541](http://ubuntuforums.org/showthread.php?t=505541) which worked for me.  That zephyr solution looks much more robust though...I'll have to check it out when I have some time.  Another question though, any ideas on how i can do this from a an x86 macbook running osx?  eek.  Trying to avoid the virtual machine here and do this right through osx!  Thanks for any advice!

Kevin

---

### Post by p_quarles on 2007-12-28
I believe that you need an Xserver on the machine to which you are tunneling the remote X session. So, you would just need to install X11 on the Macbook.

---

### Post by KCormier on 2007-12-28
ok. so i set up x11, get into full screen mode, start gnome session, get out of full screen mode just fine, but as soon as I try to go back all hell breaks loose :-\  Any helps or am i gonna have to find an apple forum to sign up to?

-Kevin

---

