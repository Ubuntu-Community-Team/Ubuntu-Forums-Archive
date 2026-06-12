---
title: "[SOLVED] vnc4server or vncserver ?"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by BassKozz on 2007-11-20
I am running xubuntu (7.10) on an old p3 800mhz w/ 256Mb RAM... and I'd like to setup VNC so I can connect to my xubuntu box from my WinXP boxes.

When I search the Synaptic Package Manager for vnc4server I get two results:
[IMG]http://i4.photobucket.com/albums/y105/basskozz/xubuntu/vnc-question.png[/IMG]

Which one should I use? or is there a better alternative besides these two?
TIA,
-BassKozz

---

### Post by kebes on 2007-11-20
The [package description for "vncserver"]("http://packages.ubuntu.com/gutsy/x11/vncserver") says:
> A new version of vnc and is available in the vnc4server package. This package exist because of backward compatibility.
So, basically you should use the newer [vnc4server]("http://packages.ubuntu.com/gutsy/x11/vnc4server") instead. (By the way, there are multiple vncserver packages. I use [tightvnc]("http://packages.ubuntu.com/gutsy/x11/tightvncserver"), but they are all good and should all work with each other.)

---

### Post by BassKozz on 2007-11-20
Thanks for the reply kebes,
I got ansy and started working on this before reading your reply, and I followed [this post](http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html) ([http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html](http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html)) to the 'T'...

Except when I try and connect from my WinXP box using TightVNC I get the following error message:
[IMG]http://i4.photobucket.com/albums/y105/basskozz/xubuntu/ScreenShot28.jpg[/IMG]
Any ideas?
Thanks again,
-BassKozz

---

### Post by BassKozz on 2007-11-20
:bump: anyone?

---

### Post by BassKozz on 2007-11-20
Question Moved: [http://ubuntuforums.org/showthread.php?t=618937](http://ubuntuforums.org/showthread.php?t=618937)

---

