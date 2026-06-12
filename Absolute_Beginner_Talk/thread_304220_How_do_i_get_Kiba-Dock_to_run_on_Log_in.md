---
title: "How do i get Kiba-Dock to run on Log in"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by Jamesbowden on 2006-11-21
I have just installed Kiba-Dock on ubuntu. 

using this .deb package: [http://forum.beryl-project.org/topic-4930-edgy-kiba-dock-package](http://forum.beryl-project.org/topic-4930-edgy-kiba-dock-package)

i relay like it, but the only problem is that the only way i can run it is from terminal using: 

```
kiba-dock
```

or by creating a launcher that runs that command.

i would like it to run when i log in, but i have no idea how to do this.

can any one help?

thanks

---

### Post by PriceChild on 2006-11-21
System>Preferences>Sessions

Choose the "Startup" tab.

Add "kiba-dock" there :)

---

### Post by steevk on 2006-11-21
I'm running Kubuntu, so this won't work for you, but if someone else is and is wondering how...

I find the easiest way is to use the terimal, but that's because I'm comfortable with it. You can do this graphically, too...

> sudo kate ~/.kde/Autostart/customstart.sh

Copy and paste this into the file...

> #!/bin/bash

kiba-dock & 

Make sure it's executable...

> sudo chmod +x ~/.kde/Autostart/customstart.sh

Save, quit, and it should start up the next time you log in.

---

### Post by Jamesbowden on 2006-11-21
thanks, i usually use "kiba-systray.py" to run kiba-dock so i get the nice systems tray icon however when i add this command to the start up tab is does no start when i log in, it will only work if i add "kiba-dock" like you said.

---

### Post by Don_DiZzLe on 2006-11-24
I have .desktop file of kiba-dock that i want to add in my src folder during compilation and building the dep, how do I do that?

Do i need to edit some makefiles or something?

---

### Post by That_Geek on 2006-11-24
steevk, as you are running kde, all us gnomers should have to do is change the kate to gedit right?

---

### Post by argie on 2006-11-24
> **That_Geek said:**
> steevk, as you are running kde, all us gnomers should have to do is change the kate to gedit right?
Well, I don't think gnome keeps its startup things in ~/.kde/Autostart/ :)

Also, another way, (which I find simpler), is to just make a symbolic link in ~/.kde/Autostart/ to the program.

---

### Post by turbojugend_gr on 2006-11-24
@ That Geek #6: Why bother even if it was a possibility (which it isn't). You just follow what Price Child says. So simple.

---

### Post by PriceChild on 2006-11-24
> **turbojugend_gr said:**
> @ That Geek #6: Why bother even if it was a possibility (which it isn't). You just follow what Price Child says. So simple.+1

---

### Post by miceagol on 2007-02-18
...and I'm trying to *remove* kiba-dock from starting up at login. ;) I've removed it from Session, but it still loads at startup. Anybody know why? I thought it might be that there's still som subprocesses running when I shut down the computer, but I don't see anything kiba like when using the top command.

---

