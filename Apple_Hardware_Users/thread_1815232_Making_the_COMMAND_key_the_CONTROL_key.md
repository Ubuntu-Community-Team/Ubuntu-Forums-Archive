---
title: "Making the COMMAND key the CONTROL key?"
date: 2011-07-30
forum: Apple Hardware Users
---

### Post by iDoiStuff on 2011-07-30
If you're familiar with macs, you know that they use command keys instead of control..

If I want to select all I press COMMAND + A not CONTROL + A
copy is COMMAND + C, paste is COMMAND + V, quitting an application is COMMAND + Q.

I am used to this, and I would like to change the command key to be the control key, and the macs control key to be the "windows" key.

---

### Post by pindar on 2011-07-31
I don't think you can do this with the keyboard configuration utility because this uses the command setxkbmap, and AFAICS, this doesn't have an option to swap left win (that's what the key is called in linux) with left ctrl. So I guess you'll have to use xmodmap. In a nutshell:

[LIST=1]
[*]Make a copy of your current layout by running 'xmodmap -pke > ~/.Xmodmap'
[*] Run the command 'xev' and find out what the keycodes of your apple and control keys are (press them, and the keycode will be printed on your terminal window).
[*] Open the .Xmodmap file in an editor and simply try to swap the definitions for these two keys.
[*] Run 'xmodmap ~/.Xmodmap'
[/LIST]

I haven't tried this particular layout, so I don't know if it works, but there's lots of information about xmodmap, so you should find your way around.

---

