---
title: "How do you actually open ATI Graphics Control Panel? - Acer Aspire 5024WLMi"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by ovimunt on 2006-06-29
Hi,

I've used Synaptics to install ATI's proprietary drivers *fglrx* on my Acer Aspire 5024WLMi. Now, how do I actually open the control panel? I don't see any new shortcuts or anything like that.

Can anyone help? Thanks

---

### Post by matthew on 2006-06-29
You will need to install another package...I seem to recall it's called fglrx-control, but a quick search for "fglrx" in synaptic will help you find it.

After it's installed you will have a menu item in Applications->System Tools called ATI Command Center.

---

### Post by ovimunt on 2006-06-29
I've checked in Synaptics and the package IS installed, yet no shortcut. I also checked in Alacarte Menu Editor but couldn't find the ATI Control Center in there either.

I'm thinking to remove the ATI stuff but I'm afraid I might f**k up my graphics... :-|

Any suggestions?

---

### Post by hollaburoo on 2006-06-29
type fireglcontrol in the Terminal

---

### Post by matthew on 2006-06-30
[quote=ovimunt]I've checked in Synaptics and the package IS installed, yet no shortcut. I also checked in Alacarte Menu Editor but couldn't find the ATI Control Center in there either.

I'm thinking to remove the ATI stuff but I'm afraid I might f**k up my graphics... :-|

Any suggestions?[/quote]I did a little snooping and discovered that I made the menu item (funny how I forgot that...sorry!). Here are the details. You can use Alacarte Menu Editor to create the entry wherever you would like in your menus. You can change everything but the command.

Name: ATI Command Center
Comment: graphic card control panel
Command: fireglcontrolpanel
Icon location: /usr/share/pixmaps/ati.xpm

I hope that helps!

---

### Post by Rich3077 on 2006-06-30
Nice info, I too installed the ATI control thingy and it didnt get added to the software menu.
Hmmmmmm when I type fireglcontrol I get errors.. I dont like errors. 
Other than that my 3D seems to be working fine and Quake 3 doesnt complain.

Peace
Rcih

---

