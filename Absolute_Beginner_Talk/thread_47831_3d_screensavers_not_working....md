---
title: "3d screensavers not working..."
date: 2005-07-10
forum: Absolute Beginner Talk
---

### Post by gammyhand on 2005-07-10
I can't get 3d screensavers to work. They preview fine in the screensaver chooser but when I actually try to preview one nothing happens. Any ideas why?

---

### Post by mtron on 2005-07-10
did you try to install the apropriate 3d drivers for your hardware ?

nvidia: [http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver)
ati:[http://www.ubuntuforums.org/showthread.php?t=24557](http://www.ubuntuforums.org/showthread.php?t=24557)

cheers

---

### Post by gammyhand on 2005-07-14
[QUOTE=mtron]did you try to install the apropriate 3d drivers for your hardware ?

nvidia: [http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver)
ati:[http://www.ubuntuforums.org/showthread.php?t=24557](http://www.ubuntuforums.org/showthread.php?t=24557)

cheers[/QUOTE]
 Yes. I get 4000+ in fglrxgears.

---

### Post by gammyhand on 2005-07-15
[QUOTE=gammyhand]Yes. I get 4000+ in fglrxgears.[/QUOTE]
 Anyone?

---

### Post by gammyhand on 2005-07-21
I guess no answer then :(

---

### Post by Teroedni on 2005-07-21
can you post hardware specs?

Can you see the screensaver or do it just a blank screen.
Many monitors can turn itself off (Powermode)
There is also option in bios and i guess you find some options in ubuntu to

---

### Post by gammyhand on 2005-07-21
[QUOTE=Teroedni]can you post hardware specs?

Can you see the screensaver or do it just a blank screen.
Many monitors can turn itself off (Powermode)
There is also option in bios and i guess you find some options in ubuntu to[/QUOTE]
 I think it is a driver problem. Before installing the ATI drivers (for dual screen) I could view the 3d screensavers (very slowly though). Once I installed the ATI drivers I click on "preview" for a screensaver and nothing happens. It just sits there with a cursor on the screen. Which is weird as I can see the 3d screensaver in the dialog box preview.

---

### Post by poofyhairguy on 2005-07-21
[QUOTE=gammyhand]I think it is a driver problem. Before installing the ATI drivers (for dual screen) I could view the 3d screensavers (very slowly though). Once I installed the ATI drivers I click on "preview" for a screensaver and nothing happens. It just sits there with a cursor on the screen. Which is weird as I can see the 3d screensaver in the dialog box preview.[/QUOTE]

Hmm...do you have composite enable in your xorg file? they hate each other....

---

### Post by gammyhand on 2005-07-22
[QUOTE=poofyhairguy]Hmm...do you have composite enable in your xorg file? they hate each other....[/QUOTE]
 What line would I be looking for in xorg.conf?

---

### Post by onlyoucansaveus on 2007-10-05
I have the same problem...
Anyways
I think the line you&#341;e looking for is:
> Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

