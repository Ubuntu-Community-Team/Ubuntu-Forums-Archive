---
title: "Help please! Gutsy in video driver select loop"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by bwallum on 2007-09-30
Having done the Gutsy upgrade route from within Fiesty terminal etc and gone for restart the following occurred.

I was presented with a small app window that has two tabs, Screen and Graphics Card. No matter what you choose, either the defaults or my own specific monitor (IBM 6627) and card (nVidia GeForce 7300 GS DDR2 256 PCI-E)  when you press ok the sytem reverts to a full screen terminal display. It then displays for one second, goes blank for half a second. It repeats this for a total of 3 times. It then returns to the small app window with the Screen and Graphics Card tabs.

The only way to break the loop is to press the power button on the computer.

If I press esc as Grub boots then I can choose the recovery mode and get a stable full screen terminal. I can see that my work files are ok by using the ls command in the terminal.

How do I fix Gutsy or get back to my stable Fiesty please? 

(I know I'm an idiot for trying the beta but I read a post that said it was ok and easy - slapped my own  wrists already)

Rgds
Bob

---

### Post by bwallum on 2007-09-30
Yo! Fixed thanks to Game_boy.

Choose the generic settings for nvidia cards. Choose generic monitor. Do NOT press OK. Instead turn off your computer by the power switch.

Leave for a few seconds then turn on. Press esc before grub boots and select the third entry on the kernel menu (2.6.20-16 an earlier version).

Then you should get the desktop up.

Be careful when trying to change monitor from generic. I ended up with a split and displaced  desktop although the mouse pointer behaved as though the desktop was displayed normally. With trial and error you can get the menus to work and reset the monitor to generic when all is well again.

It is a buggy beta, beware!

On the upside BBC News works without any resorting to the terminal. Nice and easy to set up, well done developers!

---

