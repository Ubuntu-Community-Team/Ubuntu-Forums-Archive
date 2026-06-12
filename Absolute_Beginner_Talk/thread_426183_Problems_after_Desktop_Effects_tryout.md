---
title: "Problems after Desktop Effects tryout"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by gazzadtfan on 2007-04-28
Hi, I upgraded from 6.10 to 7.04 recently and all was well until I tried the Desktop Effects button. I decided to go back to normal but then I noticed several problems had appeared afterwards.

1 I no longer get the min, max and close buttons at the top right of any screen.
2 I had changed the names of the desk buttons (bottom r/h corner) but they always go back to Desk 1, Desk2 etc after rebooting.
3 When I open the terminal, all I get is a white box. I can get rid of it by using the exit command, even although I can't see the command being typed.

I thought this was all graphics related but don't know what I can do about it.

As a second query, not related, how do I reduce the number of Kernel versions that show up on the menu upon booting up. I thought of just keeping the most recent and perhaps one older one in case I might need it for any reason.

I currently dual boot with XP and have a nvidia geforce 6200 card

thanks in anticipation
Gaz

---

### Post by josephus on 2007-04-28
second question is easier than the first.  edit the grub menu list and remove the entries that you don't need (you might want to make a backup copy of the file before you edit it)

```
sudo pico /boot/grub/menu.lst
```

i'm not sure what is wrong with regards to your first question, but if i were to hazard a guess i would say that compiz is still being loaded up at login instead of metacity.  look inside of ~/.gnomerc and see if the last entry is

WINDOW_MANAGER=~/.gnome-compiz-manager/openbox

or something to that effect.  you can remove that entry and see if metacity loads up instead.

---

### Post by mikewhatever on 2007-04-28
Do you keep using the restricted graphics driver? 
Since you have upgraded to Feisty, it would be a good idea to uninstall the old kernel version/s from synaptic. Search for 2.6.17, find you kernel version and uninstall.

---

