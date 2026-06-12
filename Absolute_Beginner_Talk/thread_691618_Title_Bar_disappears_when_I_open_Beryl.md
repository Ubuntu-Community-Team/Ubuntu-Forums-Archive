---
title: "Title Bar disappears when I open Beryl"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by alstroph on 2008-02-08
I've tried a few fixes with no help. What should I do?

---

### Post by gsiliceo on 2008-02-08
Do you have an nvidia card?

---

### Post by macogw on 2008-02-08
Do you have Emerald installed?

---

### Post by alstroph on 2008-02-08
Yes and yes.

---

### Post by macogw on 2008-02-08
Is Emerald running?
```
ps -e | grep -i emerald
```
If that doesn't show anything, try running
```
emerald --replace
```
and it should bring the window borders back.  I suggest doing that one from a runbox (alt+f2) because if you do it in the terminal and close the terminal, emerald will probably stop running.

---

### Post by alstroph on 2008-02-08
Actually now I restarted my computer. Beryl was set to start with the comp. Now I have no title bar AND not task bar on the top or bottom. This sucks... what can I do now? I managed to get firefox up luckily

I've figured out how to open the terminal. Now what can I type to get my task bars back?

---

### Post by macogw on 2008-02-08
```
gnome-panel
``` should restart the panels.  They could be running and semi-crashed too (maybe?), so if that doesn't work, ```
killall gnome-panel
``` should kill/restart it.

---

### Post by alstroph on 2008-02-08
Thanks. I restarted my system and the top task bar appeared but the bottom one did not. I entered that command and the bottom task bar came. Now I'll try and fix these damned title bars.

---

### Post by alstroph on 2008-02-08
> **macogw said:**
> Is Emerald running?
```
ps -e | grep -i emerald
```
If that doesn't show anything, try running
```
emerald --replace
```
and it should bring the window borders back.  I suggest doing that one from a runbox (alt+f2) because if you do it in the terminal and close the terminal, emerald will probably stop running.

This is what I get:
alstroph@alstroph-laptop:~$ ps -e | grep -i emerald
 6067 ?        00:00:00 emerald
alstroph@alstroph-laptop:~$ emerald --replace



Then it sits blank.


I'm uninstalling Beryl, reinstalling my Nvidia drivers, then reinstalling Beryl. I'll see where that gets me.

---

### Post by alstroph on 2008-02-08
I fixed the problem. I right clicked on beryl manager and selected compiz as my theme manager.I was then able to apply emerald themes and had a title bar. Thanks for the help everyone. I'll be back when the next problem arises..

Edit: Wait... that disables Beryl though. I like the cube effect of Beryl better than Compiz and I would like to use it. Is there anyway I can have my title bars AND use Beryl? :( This is so hard.

---

### Post by RussellGee on 2008-02-08
Enable the cube rotation plugin in compiz and you will have the 3d cube in compiz.:)

---

### Post by alstroph on 2008-02-08
Problems again. Title bar disappeared. I closed beryl, took it off of startup, then did CTRL ALT BACKSPACE to restart. Still no title bars.

Why am I having so many problems?

---

### Post by gsiliceo on 2008-02-08
Do this in the terminal
sudo nvidia-xconfig --add-argb-glx-visuals
and then
ctrl+alt+delete
Tell me how it went

---

### Post by alstroph on 2008-02-09
I got the title bars back temporarily using the command metacity --release (something like that... I forgot). I did what you said and I'll restart my computer in a minute to see if it helped. Thanks :)

---

### Post by PurposeOfReason on 2008-02-09
Honeslty, why are you using bery? Compiz fusion is beryl and compiz fused together. Anything that can be done is bery is done in compiz. If you haven't, install compizconfig-settings-manager or something along those lines and you can configure compiz so that it works just like you have beryl working and as it is fully supported under Ubuntu 7.10 you'll have less problems.

---

### Post by alstroph on 2008-02-09
> **PurposeOfReason said:**
> Honeslty, why are you using bery? Compiz fusion is beryl and compiz fused together. Anything that can be done is bery is done in compiz. If you haven't, install compizconfig-settings-manager or something along those lines and you can configure compiz so that it works just like you have beryl working and as it is fully supported under Ubuntu 7.10 you'll have less problems.

Thanks for the suggestion. I'll definitely use compizfusion now... but as soon as I installed it my title bar disappeared again. :( This is unbelievably frustrating. Why won't this just work?



Edit:   I went to System>Preferences>Advanced Desktop Effects Settings and changed the Window Decoration plugin to on. Pop went the title bar. I think I might be okay. :) Thanks for the help everyone :) How do I "thanks" people?


Edit 2: New problem... it disappeared again. I went and typed emerald --restart and it came back up... but as soon as I close the terminal the title bar goes away again. Never ending problems.

---

### Post by alstroph on 2008-02-09
Absolutely great. Now I'm completely screwed as far as GUI go. When I restart the computer it makes me log in and gives me some graphics error and sends me straight to a command line. How should I proceed? Right now I'm in using the Ubuntu CD to load the basic operating system. 

Can I reset everything back to default somehow? I've got some things downloaded already that I don't want to lose... so I'd like not to reformat.

Help please :(

---

### Post by PurposeOfReason on 2008-02-09
Does the error have anything to do with an xorg.conf file?

---

### Post by gsiliceo on 2008-02-09
dpkg-reconfigure xserver-xorg
in the command line, and follow the assitance, just answer yes to all those questions to get gui back.

---

### Post by Harabec on 2008-02-12
Install Aquamarine instead of Emerald, seemed to fix my problems.
```
sudo apt-get install aquamarine
```
Then, when you launch beryl-manager click "Select Window Decorator" and select "Aquamarine (KDE Decorator)". Reload both the decorator and the window manager and hopefully that should do something.

---

