---
title: "Scaling in xorg.conf"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by op157 on 2007-03-24
Hello,
  I can't find an answer to this anywhere.  I have 2 displays, 1 monster monitor and 1 projector using a nVida Quadro FX4500, and I want to have the same screen on both.  I tried messing around with the xorg.conf file trying to get it to work, but the monitor only wants to display 2048x2048 and the projector only wants to display 1600x1200.  Right now I have the projector showing a subsection of the projector screen.  I want to scale the display on the projector to show the full screen.  Unfortunately, I don't have access to the xorg.conf file at the moment b/c of some power repairs they're doing down the street.  I do know what I've tried though.

1) Option "FlatPanelProperties" "Scaling = Scaled/Native/Centered" - I tried all of these on both screen and it didn't have an effect.  I believe I put it in the device section

2) Virtual 1600 1200 - I tried that in a Display subsection I believe.  Before doing this projector would show the top left 1600x1200 pixels of the 2048x2048 display.  Adding this only centered it.

3) I tried TwinView with cloning.  I added the <DFP-0> Scaling = scaled or something along those lines with different combinations.  It just showed the top left 1600x1200 pixels of the 2048x2048 screen.

4) More of an FYI.  The video card has 2 inputs.  When I have the monitor in #1 and the projector in#2, maximizing a window will make it fit in the 2048x2048 screen, and the taskbar (or whatever the bar on the desktop is) shows across the 2048 screen.  When it's switched, there's still a 2048x2048 screen, but the taskbar shows across only 1600 pixels (filling up the projetor screen).  Maximizing a window will fill up the top left 1600x1200 pixels (I forgot to try maximizing with the virtual 1600 1200)

5) Another FYI.  If the screens aren't clones, I get 2 seperate desktops.  One has no icons on the background, and I can't figure out how to get windows on it.  I tried opening a window on one, and then sending to all workspaces, but that didn't work.  I'm not opposed to (temorarily) setting up something where the 1600x1200 screen VNC's or something to the the other screen while scaling it.

Any ideas?

---

### Post by op157 on 2007-03-24
Bump

---

### Post by op157 on 2007-03-25
bump again

---

