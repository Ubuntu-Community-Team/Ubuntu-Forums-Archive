---
title: "How to apply the editted xorg.conf file"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by nousername on 2006-04-19
1. After editing the xorg.conf file how to I try it to see if it works without restarting the computer?

2. How can I view errors which occurred while trying to load the new xorg.conf file (i.e. a log file or something)?

Thanks

---

### Post by aysiu on 2006-04-19
[QUOTE=nousername]1. After editing the xorg.conf file how to I try it to see if it works without restarting the computer?[/QUOTE] Press Control-Alt-Backspace

---

### Post by brentoboy on 2006-04-19
once you are in the text terminal (from ctrl+alt+backspace) run:

 sudo /etc/init.d/gdm restart

---

### Post by Mustard on 2006-04-19
To view errors, you would look in the /var/log/ folder for the Xorg.0.log and display it in terminal...

```
sudo cat /var/log/Xorg.0.log
#use the shift + page up keys to go up the screen
#after the output completes in terminal
```

---

