---
title: "Changing SLI modes based on program"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by tito13kfm on 2007-06-08
Hi all,
I figured out last night that my video cards don't really do anything when set to Alternate Frame Render for my SLI mode.  Split Frame Render works great but is overkill on stuff like Doom3 and Quake 4.  

I was wondering if I could leave my xorg.conf file set to SFR mode and maybe have a script that runs for certain games that would temporarily change it to SLI=AA for less graphically intense games like Doom3, but leave it at SFR mode to get the best performance while running games through wine.

I believe the script would have to look something like
nvidia-xconfig SLI=AA
Some command to reboot the desktop
/usr/local/games/doom3

But I have no idea how it should work exactly.  Any help would be greatly appreciated.
Also, it should change the SLI mode back to SFR after quitting the program.

---

