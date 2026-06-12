---
title: "Shortcut target"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by harleyrider on 2006-05-25
Hi,
I recently installed RealPlayer10GOLD.bin and it worked fine. I also did some updates, but after an accidental install of Realplayer from Synaptic, my shortcut in Applications|Sound & Video|RealPlayer 10 no longer works. When I click on it, I get "Error Cannot launch entry, Details: Failed to execute child process "realplay" (No such file or directory). I can go to the folder where it resides and click on realplay.bin, and the application starts and functions properly. I also tried to uninstall with a "sudo apt-get remove RealPlayer10GOLD", but to no avail. According to Synaptic, the realplayer is not installed. I would like to have this work again with Firefox and with the shortcut in my menu described above. Any suggestions?

---

### Post by Nano Geek on 2006-05-25
You can change the path that the menu shoutcut takes by using the menu editor, Go: Applications>Accessories>Applications Menu Editor>Sound & Video>Right-click on Real Player>Properties, and change the file path to where your Realplayer application is kept. To unistall it in Synaptic type: **sudo apt-get remove realplayer** in the terminal insteed of REALPLAYER10. Hope it works.

---

