---
title: "Two problems: automatic wi-fi in .xinitrc and freezing apps"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by Cyvros on 2007-09-11
I've got a couple of problems here - firstly, I'm running Feisty on a Dell Inspiron 1501, dual-booting with Vista.

My first problem is that I have no idea how to activate the wireless networking via my .xinitrc file and I can only get the networking going in GNOME (I think it's an applet requiring the GNOME panel, but I'm not sure) when what I really want to do is use Openbox and/or dwm. I used the [Ubuntu on Dell Inspiron 1501 guide for getting the wi-fi working](http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html) and it works fine.

My second problem is that I have apps freezing on me a lot. It's mainly media players - Amarok, BMP, BMPx, MPlayer, VLC, Totem and XMMS. For BMP, BMPx and XMMS, I can add a file to the playlist, but, as soon as I press Play, it freezes. If I switch to another window and switch back, all I see is the background (the grey and white bits, basically).

If I try Totem, it freezes. But, if I try MPlayer or VLC, it will play, but the only thing moving in the window is the video file I'm playing. Another app I'm using for video, aviplay, is working fine.

But there are other apps that are doing this - there's the GNOME Network Manager, where I can't configure anything because it just freezes, and sometimes I can't log into GNOME or anything else. In fact, I'm currently writing this from my Failsafe GNOME session. :(

I've tried a few things - first was getting rid of a lot of the Gtk themes I installed, next was getting rid of all the Compiz/Beryl/Fusion stuff (which I'd tried, but couldn't get working) and then losing a lot of codecs. None of them seemed to work.

I'm also having trouble installing a music notation app called [MuseScore](http://mscore.sourceforge.net/en/idx.php) - I can't do the usual make, make install thing suggested and using the included mkdebian shell script for either 0.6.0 or 0.6.1 gives me a package that seemingly has everything **except** the binary. I'm not sure if it's a problem with how I'm doing it or not.

Can anyone help me with anything here? :D I'd be really, really grateful.

---

### Post by Cyvros on 2007-09-13
Now I have a couple of new problems. I can't log out from GNOME the normal way (session options pop-up) because, rather than being presented with the login screen, I'm faced with a black screen. I can still switch to other CLI workspaces, but the normal one's stuffed and I can only exit it by 'manually' rebooting.

However, I can still log out with Ctrl+Alt+Bksp.

I'm also having troubles with the Users & Groups sort of blanking as well (see my previous post, about the fifth paragraph).

But, I do believe I know how to compile MuseScore now.

Does anyone know of anything that can help me, particularly with getting the wi-fi to autostart through my .xinitrc file?

---

