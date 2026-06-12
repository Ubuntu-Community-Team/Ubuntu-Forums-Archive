---
title: "Grub Background Colors"
date: 2005-02-11
forum: Art &amp; Design
---

### Post by Sapper2ID on 2005-02-11
I would like to change colors to a Red background and Black letters. Simply putting in that way doesn't seem to work. Currently it is Cyan/Blue White/Blue. How would I phrase it to change these?

---

### Post by Sapper2ID on 2005-02-11
It figures! Ask for help then solve the problem myself.

cyan/blue    white/blue
border/background     selected kernel line/unselected

Now it's red/black    red/blue

I can't get two word colors to work (cherryred). I'll try a color chart for the proper names of other shades

For noobs, (like me) I used  "sudo gedit /boot/grub/menu.lst"
uncomment the line under #pretty colors
Change as you like and hit "Save"
To show menu comment "Hidden Menu"

---

### Post by maart on 2005-02-12
Im using:
red/black white/black

Can someone list here all possible colors which can use there?

---

### Post by bvc on 2005-02-12
[http://www.gnu.org/software/grub/manual/html_node/color.html](http://www.gnu.org/software/grub/manual/html_node/color.html)

---

### Post by Mikebgr on 2006-05-01
thanks for this! I actually didnt uncomment pretty colours line, and I was scratching my head as for why no color would show!

---

### Post by tsrjzq on 2006-05-03
oh, the grub's menu can be color...
it's so interesting...

---

### Post by commodore on 2006-05-04
I thought it had backgrounds too.

---

### Post by Dr_Faustivius on 2006-11-06
From what I can glean from forums, documentation, and the Irc room (Thanks guys!) the default install of grub does not support a background image. There are third party programs that can be installed that will enable this, but I haven't finished researching this enough to be confident when giving instruction. 

If I find anything more, I'll post it up here.

---

### Post by Tomosaur on 2006-11-06
There are set colours to use for Grub, and a background image can be enabled, although the line you need to use is not included in the menu.lst file. You need to add the line:

splashimage=/path/to/image

There are also certain restrictions on the color depth and resolution of your image, so it's well worth reading up on it if you're interested.

The script in my sig will allow you to set both a background image and alter the color scheme, but Grub will start acting a bit weird if you try to do both together (it will still work fine, it just may not look as you intended). The color editing options will allow you to select from all available default colors. You should know that there are **different available colours** for the foreground and background, which may be why your colour scheme won't work. Try switching the colours around and see what happens.

---

