---
title: "ZSNES runs slow.  Also monitor resolution trouble."
date: 2005-10-27
forum: Absolute Beginner Talk
---

### Post by jqp on 2005-10-27
I managed to install ZSNES from a .deb file someone linked to in the forums.

ZSNES lags for me in ubuntu but runs beautifully on Windows.  In detail, it runs fine in a window smaller than 640x480, but runs very poorly in any fullscreen mode and any resolution >= 640x480.  The mouse cursor lags a bit behind my movements, and I believe the joystick has the same problem with lag.  Is there anything I can do about this?  I don't know where to start troubleshooting.

Also, I would like to run ubuntu in 1280x1024 mode.  When I first installed ubuntu, it didn't recognize that my monitor supports that resolution.  Also, 1280x1024 worked fine in my previous installation of FC4.  I had followed some instructions to edit xorg.conf, but after that, everything did look a little stretched.  I'm sure I did something wrong.  I need some simple instructions on how I might need to edit xorg.conf (the right way) to get that resolution working correctly.   I undid all my changes to xorg.conf and I'm back at 1024x768 for the time being.

Also, how to you restart X without rebooting?

This is my 4th distro, and hopefully the distro that will make me actually learn how to use Linux well and use it more than windows.  I'm kind of a power windows user.  I'm on day 2 with ubuntu, and I do like it so far.  I'm using a P4 2Ghz, 512 MB RDRAM (stupid Dell RDRAM...), and a Nvidia 5600 256MB video card.  

While I'm asking questions...
Can you install/run Konqueror in Gnome?  I like Gnome, but I like to test my website stuff in Konqueror.  I also like using Konqueror as a file browser.  Is there a good Gnome-friendly file browser similar to Konqueror?

---

### Post by poofyhairguy on 2005-10-27
[QUOTE=jqp]I managed to install ZSNES from a .deb file someone linked to in the forums.

ZSNES lags for me in ubuntu but runs beautifully on Windows.  In detail, it runs fine in a window smaller than 640x480, but runs very poorly in any fullscreen mode and any resolution >= 640x480.  The mouse cursor lags a bit behind my movements, and I believe the joystick has the same problem with lag.  Is there anything I can do about this?  I don't know where to start troubleshooting.[/QUOTE]

You need to use an Opengl mode. First install your video card drivers  (the Ubuntu Guide will help you there) then use one of the modes with an "O" in it. If it still does not fly, it because you are using the Hoary backported 1.42 deb in Breezy. For some reason its really slow. This bugs me very badly, and so I will have a fix sooner or latter because I love my Zsnes. Maybe just me begging for a new backport. The solution till then is to use the old version in the repos.


> Also, I would like to run ubuntu in 1280x1024 mode.  When I first installed ubuntu, it didn't recognize that my monitor supports that resolution.  Also, 1280x1024 worked fine in my previous installation of FC4.  I had followed some instructions to edit xorg.conf, but after that, everything did look a little stretched.  I'm sure I did something wrong.  I need some simple instructions on how I might need to edit xorg.conf (the right way) to get that resolution working correctly.   I undid all my changes to xorg.conf and I'm back at 1024x768 for the time being.

> sudo dpkg-reconfigure xserver-xorg

Have you tried that command?

> 
Also, how to you restart X without rebooting?

ALT- CTRL -BACKSPACE

> 
This is my 4th distro, and hopefully the distro that will make me actually learn how to use Linux well and use it more than windows.  I'm kind of a power windows user.  I'm on day 2 with ubuntu, and I do like it so far.  I'm using a P4 2Ghz, 512 MB RDRAM (stupid Dell RDRAM...), and a Nvidia 5600 256MB video card.  

You sound exactly like me, right down to the computer specs. Some time you should try my Composite Manager guide if you get the chance, it fun for us Windows power users.

> 
While I'm asking questions...
Can you install/run Konqueror in Gnome?  I like Gnome, but I like to test my website stuff in Konqueror.  I also like using Konqueror as a file browser.  Is there a good Gnome-friendly file browser similar to Konqueror?

It will work, but you have to install some KDE libs. Yeah I don't care about that either, I just have to say that.

---

### Post by jqp on 2005-10-27
[QUOTE=poofyhairguy]You need to use an Opengl mode. First install your video card drivers  (the Ubuntu Guide will help you there) then use one of the modes with an "O" in it. If it still does not fly, it because you are using the Hoary backported 1.42 deb in Breezy. For some reason its really slow. This bugs me very badly, and so I will have a fix sooner or latter because I love my Zsnes. Maybe just me begging for a new backport. The solution till then is to use the old version in the repos.[/quote]
I got the Nvidia legacy driver installed.  That pretty much fixed my zsnes problem. OpenGL goes to crap until that thing is installed.

> Have you tried that command?
Yeah, I used that command to get the original xorg.conf file back to normal.  I had to do that to enable the nvidia driver.  Even after the nvidia driver got installed, though, there's no resolution available higher than 1024x768.  Any suggestions on that?  

> You sound exactly like me, right down to the computer specs. Some time you should try my Composite Manager guide if you get the chance, it fun for us Windows power users.
What/where is that guide?
> It will work, but you have to install some KDE libs. Yeah I don't care about that either, I just have to say that.
If it's not too difficult, I'd like to try getting Konqueror running for web browsing/testing.  I may mess with that later.  Having linux installed is the closest I'm going to get to using Konqueror or Safari.  I like testing on them.

Anyway, if I can just get a higher monitor resolution running, I'd be pretty happy for the time being.

BTW, I feel like a complete linux newbie.  I'm willing to use and learn the command line, but I don't know much about it at all.  Is this the forum here I should stick to for support at this point?  Should I go to the main Ubuntu support forum or would it still be over my head at this point?

---

### Post by raublekick on 2005-10-28
While we're on the subject...

How can I get ZSNES working faster if I have an ATI card (with fglrx driver installed)? Same issues as the first post.

---

### Post by noigeaR on 2005-10-28
[QUOTE=poofyhairguy]Maybe just me begging for a new backport. The solution till then is to use the old version in the repos.
[/QUOTE]

you could download the latest source from [iphers' wip page]("http://www.ipherswipsite.com/") (download link is the blue S in the menu to the left) and compile it yourself. it's not that hard to compile and works just as good as the windows version for me. there are many updates and improvements included in the wip version that aren't in the official version yet.

---

