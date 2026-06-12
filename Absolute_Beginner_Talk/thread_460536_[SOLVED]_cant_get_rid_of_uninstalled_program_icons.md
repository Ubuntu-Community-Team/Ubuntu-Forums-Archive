---
title: "[SOLVED] cant get rid of uninstalled program icons in my applications menu"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by daimaru on 2007-05-31
my problem as the title says is that i have a few program icons still lingering even though they have long been uninstalled. clicking them obviously starts nothing because nothing is there. now i would love to get rid of them. 

as an example under in uninstalled eclipse but it still exists under Programming-->eclipse. 
so i tried alacarte to remove it but it does not show up in alacarte :confused:. and as an added bonus if i just uncheck the whole Programming menu since there is nothing in there right now, nothing happens it still stays =D>

so im guessing i broke my alacarte or something. is there a way to remove and reinstall the main menu?
and if so would the still working and added program icons from other software installs still be there?

thx in advance hope someone has a fix for this cause otherwise i probably would have to create a new user and move everything over there and hope that stuff still works.

---

### Post by zvacet on 2007-05-31
In main menu find section in wich you put program(accessories,internet...) and unchek it.

---

### Post by daimaru on 2007-05-31
> **zvacet said:**
> In main menu find section in wich you put program(accessories,internet...) and unchek it.

did that as i wrote in my orig post. nothing happens

---

### Post by daimaru on 2007-06-01
no ideas anyone ??? [-o<

---

### Post by silkstone on 2007-06-01
Have you tried right-clicking on Applications, then select Edit Menus and uncheck the entries you don't want?

---

### Post by shearn89 on 2007-06-01
you could try editing 

$HOME/.config/menus/applications.menu

using gedit
(i'm a little new to linux, so I'm not sure if that would work. I'd recommend backing it up beforehand....)

---

### Post by TwistesdTexan on 2007-06-01
Under System> Preferences>Sessions Check to see if the "Automatically save changes to session" block is ticked. You might try changing this.

---

### Post by daimaru on 2007-06-01
thanks for trying guys but in reinstalled my ubuntu and by doing that screwed it up bigtime gonna reinstall again :(  
as to your questions id did try right clicking on menu etc (same as entering sudo alacarte or choosing system-perf-mainmenu) but it did not work. 
i now think that maybe and im just saying maybe automatix screwed it up for me .. dont really know but in installed eclipse throught automatix and thats one of the programs that wont go away in the menu. 

so now ill reinstall again , install everything manually and hope that i dont get this problem agein, 

thx for trying to help guys.

---

### Post by arnieboy on 2007-06-02
> **daimaru said:**
> thanks for trying guys but in reinstalled my ubuntu and by doing that screwed it up bigtime gonna reinstall again :(  
as to your questions id did try right clicking on menu etc (same as entering sudo alacarte or choosing system-perf-mainmenu) but it did not work. 
i now think that maybe and im just saying maybe automatix screwed it up for me .. dont really know but in installed eclipse throught automatix and thats one of the programs that wont go away in the menu. 

so now ill reinstall again , install everything manually and hope that i dont get this problem agein, 

thx for trying to help guys.
did you uninstall eclipse from automatix? if you dont uninstall something it wont go away automagically you know.. if you did uninstall and the menu item still doesnt go, just do this:
```
sudo rm -f /usr/share/applications/eclipse.desktop
```
and stop reinstalling for Pete's sake.

---

### Post by daimaru on 2007-06-04
> **arnieboy said:**
> did you uninstall eclipse from automatix? if you dont uninstall something it wont go away automagically you know.. if you did uninstall and the menu item still doesnt go, just do this:
```
sudo rm -f /usr/share/applications/eclipse.desktop
```
and stop reinstalling for Pete's sake.

LOL thx damn but you where too late ... i reinstalled. well actually i switched to 64bit ubuntu so i could have more trouble :p , just wasn't satisfied that everything worked so well;)

---

