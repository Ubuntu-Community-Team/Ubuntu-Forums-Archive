---
title: "Real Player Install"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by Gary Nored on 2006-03-19
I can't figure out how to install RealPlayer. If I go to Applications-->Add Applications and mark Real Player for install, I get a message saying it's not available. 

So I went to Real Player website and downloaded the .bin file. Put it in my home folder. Figured out how to give it execute permissions, and did the same for the folder. Double-click, and the message says Couldn't display /home/gnored/downloads/realplayer/RealPlayer10GOLD.bin".

Following Real Player instructions, figured out how to open the terminal and moved to the folder containing the .bin file. Typed the name of the file and pressed enter. Response was "permission denied."

Prepended "sudo" and tried again. "Command not found."

I'm running out of ideas. This looks like a path problem from the old DOS days, but I don't know how to fix it. Can anyone help?

Gary Nored

---

### Post by KansasJoe on 2006-03-19
./RealPlayer10GOLD.bin

make sure the ./ is in front this is what tells it to execute

---

### Post by John_the_linux_newbie on 2006-04-08
OK - I am a goof.  I'm running Breezy on a laptop and just installed onto a desktop.
I managed to install Real Player on the laptop and a week later I seem to have forgotten what I did.

I've been to the help files in the wiki 

[https://wiki.ubuntu.com/RealplayerInstallationMethods?highlight=%28player%29%7C%28real%29](https://wiki.ubuntu.com/RealplayerInstallationMethods?highlight=%28player%29%7C%28real%29)

with no luck.  I can get as far as the setup Real screen after downloading from the multiverse.  But am stuck at the point at which I need to type the path to the installer.  All roads lead back to the type the path screen.

If I try any of the other setup methods in the terminal I get an error that there is a problem finding and installing the support files.

Any ideas?

---

