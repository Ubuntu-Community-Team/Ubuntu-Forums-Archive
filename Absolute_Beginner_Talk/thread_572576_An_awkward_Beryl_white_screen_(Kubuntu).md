---
title: "An awkward Beryl white screen (Kubuntu)"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by Kirinthos on 2007-10-10
Alright so I've examined some of the other white screen topics (not all by any means) and I've found no help, so I'm going to make a post of my own.

My Beryl (which I'm running on Kubuntu 7.04) runs off of a startup script that I wrote that executes 'beryl & emerald' after kdesktop has loaded.
This, of course, causes the oh-so-common white screen problem.  The skydome still works, I can rotate the cube and the skydome image still displays, all of the effects work...I just have the white screen.
So I restarted the server and when it reloaded the login screen, exited to the prompt through <ctrl><alt>F1 and logged into my user through the prompt-- i executed the command 'sudo rm /tmp/0X-lock' I don't remember the exact line but it removes the lock on display 0, obviously.  After that, I started the server with the simple 'startx' command.  The Xserver booted successfully and when the script executes--beryl works flawlessly.
I tried to do some diagnosis but I'm somewhat unfamiliar with the boot sequence of KDE but I did notice that (through the use of ps -aux) the kdesktop process is not running when i start the Xserver through the prompt as opposed to logging in through the Xserver.

Any help would be appreciated and thank you very much
  -Kirinthos

---

