---
title: "stopping startup programs"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by terry_gardener on 2007-10-19
hello 

i have beryl auto-starting when i logon. 

does anyone know what the terminal command is to stop it autostarting. 

now everytime i start my pc and logon beryl kicks in and presents me with white screen and i can do anything. 

any help or suggestions i would be very grateful 

thanks 

ps i uninstalled my nvidia in preparation for the ubuntu upgrade as advised on the envy website since i used this to install the nvidia driver.

---

### Post by por100pre1 on 2007-10-19
```
cd ~/.config/autostart
```

```
ls -a
```

check if theres an entry like 'beryl.desktop'

```
rm beryl.desktop
```

I'm assuming you added to sessions. :-k

---

