---
title: "Emerald Themes Problem"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by bodhisaxva on 2007-12-21
Hi,

I'm quite new to linux. I've been trying to change the look of my desktop. For the most part it has gone well and I've found the following link very helpful:

[http://tuxenclave.wordpress.com/2007...tion-guide-v2/](http://tuxenclave.wordpress.com/2007...tion-guide-v2/)

The one problem I have is getting "Emerald themes" to work. It is mentioned that you need to have "3d composite manager" running. I do not know what that is, so I tried installing some advanced desktop effects through a compiz package, but I cannot get them to work ... I cannot even get basic desktop effects to work through System-Preferences-Appearance, with the same message "Desktop Effects Could Not Be Enabled". Ubuntu help tells me this is probably due to my graphics card.

What am I doing wrong? Is there any work around for this? Am I barking up the wrong tree anyways? Can my computer just not handle anything but a very basic Linux setup?  Do I have the wrong graphics driver?

I believe the following to be my graphics card (It is a Radeon of some type), although I cannot find anything labelled "graphics" in my hardward profile:

Radeon XPRESS 200M 5955 (PCIE)

Thank you for your help!!!

---

### Post by kajillin on 2007-12-21
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) Follow that link, and all instructions, that should get your driver working. Then in add/remove search for compiz, select and install. And that should work, although sometimes compiz need exta configuration to work and sometimes it doesnt. so if it works good, if it doesnt let us know. OR use the search function, i can guarantee your problem has been asked a million times.

Edit: Also once everything is working check this site out, [http://gnome-look.org/](http://gnome-look.org/) and their partner sites. All you need to have the most badass desktop on the block.

---

### Post by bodhisaxva on 2007-12-21
Ok, it seems to have worked ... now I have another problem:  "The Composite Extension is Not Available" ... 

I tried downloading a composite extension package, restarting, to no avail.  What do I do now?

---

### Post by kajillin on 2007-12-21
open a terminal type
```

sudo gedit /etc/X11/xorg.conf
```

then look for this line

```
Section "Extensions"
	Option "Composite" "0"
EndSection
```

then change the "0" to "0n" that should work. ive heard "enable" works as well

The do a Ctrl+Alt+Backspace login, and it should work

---

