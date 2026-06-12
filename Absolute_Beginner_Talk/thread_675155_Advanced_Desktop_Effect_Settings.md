---
title: "Advanced Desktop Effect Settings"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2008-01-22
Ok, I've seen it a million times or more and i just restored my computer and i can't remember the code that i put in the terminal to install the advanced desktop effect settings =\

---

### Post by wolfen69 on 2008-01-22
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by emarkd on 2008-01-22
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by RadiationHazard on 2008-01-22
what i mean is for compiz fusion. like so i can get the cube effect and stuff.

---

### Post by emarkd on 2008-01-22
That's the code you need.  Click on Preferences > Appearance and select the Visual Effects tab.  Set it to "Custom" and use the Compizconfig-settings-manager to set all of your options, like the cube.

---

### Post by RadiationHazard on 2008-01-22
ok, well what do i do if when i click it nothing happens?

---

### Post by emarkd on 2008-01-22
You mean the config dialog doesn't come up?  Or you select the cube and it doesn't work? Or...

---

### Post by sailor2001 on 2008-01-22
in terminal:  compiz --replace    then most likely ctrl/alt and left click   You should bring up your manager though and configure it like you want...  to get back to your regular window:  metacity --replace

---

### Post by RadiationHazard on 2008-01-22
the config dialog doesn't come up

---

### Post by emarkd on 2008-01-22
So you installed it by running:
```

sudo apt-get install compizconfig-settings-manager
```

Now you should have a new menu item under Preferences > Advanced Desktop Effects that will allow you to run the program and configure your Compiz.  Did it install properly?  Did you get an error message?  Is the menu item there?  Let me know where you're having problems.

---

### Post by RadiationHazard on 2008-01-22
Ok. as you can see in the terminal it seems like everything installed correctly... but when i go to click on the settings. well nothing happens...like at all :confused::(:(

---

