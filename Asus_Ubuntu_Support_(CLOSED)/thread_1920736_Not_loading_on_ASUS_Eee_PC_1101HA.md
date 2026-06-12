---
title: "Not loading on ASUS Eee PC 1101HA"
date: 2012-02-05
forum: Asus Ubuntu Support (CLOSED)
---

### Post by schmack on 2012-02-05
[COLOR=black][FONT=Verdana]I'm installing Ubuntu 11.10 on my Asus eee pc 1101HA.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I did:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]> To make the livecd startup we have to unload a couple of drivers adding some parameters to kernel, otherwise it ends up in a white screen (or stuck at battery checking) [/FONT][/COLOR]> [FONT=Verdana][COLOR=black]add 'poulsbo.dummy=1 psb_gfx.dummy=1' to kernel params at grub time (hit F6 when livecd starts and append params at the end of string)[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]this way the 2 kernel modules are not loaded, because of wrong options enabled, and livecd could use vesa as X driver. [/COLOR][/FONT][FONT=Verdana][COLOR=black] by [[COLOR=#0000ff]lucazade[/COLOR]]("http://ubuntuforums.org/member.php?u=242850")[/COLOR][/FONT]
 
[COLOR=black][FONT=Verdana]...and it seems to start installing but after picking the language, internet connection and installing some this the screen just isn't moving, only have the cursor and the background picture...[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]What can I do?[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Thank you[/FONT][/COLOR]

---

