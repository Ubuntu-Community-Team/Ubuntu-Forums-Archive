---
title: "Xserver-xgl and Compiz resoliution problem"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by joanaomgod on 2007-10-27
Hello people! First I'll say that i am from bulgaria and my English is poor :D
I have installed xserver-xgl and compiz on my gutsy. the problem is that without compiz and resolution above 1024x768 the screen go to hell(turns to a box, there is no problem under 1024x768) My compiz is working verry well, but sometimes i need to stop it... Here is an screenshot of the bug(when i take this shot, the situation is ok, but you see that the screen is in box, the same happens when i turn off compiz).
[[img]http://img3.freeimagehosting.net/uploads/th.6282d63622.png[/img]](http://img3.freeimagehosting.net/image.php?6282d63622.png)
 My video card(intel) is integrate with mother board

---

### Post by benhall on 2007-10-27
Does the problem only appear when compiz is off?

What I would recommend to start would be to log in and log out, in case something in the display manager needed restarting. If this doens't help, check the available resolutions in System->Administration->Screens and Graphics, to see if you are using an inappropriate monitor driver. If this doesn't work you could try to use the semi-graphical screen configuration wizard provided by the command "sudo dpkg-reconfigure xserver-xorg". This should be a last resort though as it can be a bit hairy to deal with.

---

