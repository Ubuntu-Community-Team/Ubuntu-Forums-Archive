---
title: "Install Gfx Card, get 1280 Resolution, enable Wireless"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by nintennuendo on 2007-03-13
okay, windows crashed again, could not boot up unless was safe mode, so i figured i'd jump into Ubuntu at last.  Few problems though

1.  not a big one.  when i boot up, i get a screen that has two ubuntu logos side-by-side at the top, with messed up colors.  nothing happens, just a pester.  

2.  How can I install my graphics card?  I went to this page [   [http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html)   ], I downloaded the file, but it says to run that in a terminal, and I do, but it says cannot find.  help?  and, once i do, will the screen stop.. flickering when i go up and down web pages and stuff?

3.  I really need 1280 resolution x800 or x960, either, i would prefer the more space I can get.  I am going to be using my laptop for work so it is vital I can maximize time-saving.  I edited xorg.conf so all the resolutions said 1280x800 but i can't access or anything.  

4.  I have the drivers for my wireless card.  how can I install them?  there were no instructions for them on the website, and the wireless card list in a wiki for Ubuntu had no instructions.

Any help is welcome.  if anyone is in the triad area of north carolina or visiting soon, I could get you visitor passes for Old Salem if interested as payment :(

---

### Post by Ptero-4 on 2007-03-13
For the third question you need to put sudo before the nano /etc/X11/xorg.conf command to get admin privileges (and type your password when asked).

For the fourth you need to install ndiswrapper before you can use your windoze wifi card drivers.

---

### Post by Songwind on 2007-03-13
for #2, did you just type the name of the command, or did you put ./ in front of it?

"Current directory" is not part of the default path, so to run a command called "go" from the directory you are currently in you have to type "./go"

---

