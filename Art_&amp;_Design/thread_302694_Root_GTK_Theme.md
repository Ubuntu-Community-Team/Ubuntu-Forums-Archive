---
title: "Root GTK Theme"
date: 2006-11-19
forum: Art &amp; Design
---

### Post by viciouslime on 2006-11-19
If you install a new GTK theme then when you run any applications with sudo they look REALLY ugly. I know you can copy the theme to /usr/share/themes and then it will work, but this is a bit too much like hard work :p 

Would it not be possible to have the theme read from the home directory of however ran the sudo command so the application doesn't look all ugly and grey? Or, if this would pose some sort of security risk, how about making it default to human if the theme can't be found in /usr/share/themes ?

---

### Post by aidanr on 2006-11-19
```
sudo ln -s /home/<insert your username here>/.themes /root/.themes
sudo ln -s /home/<insert your username here>/.icons /root/.icons
sudo ln -s /home/<insert your username here>/.fonts /root/.fonts
```

---

### Post by viciouslime on 2006-11-19
Yeh, but that has to be done every time I reinstall, it would be better if ubuntu would just look there for the theme in the first place.

Thanks anyway though.

---

### Post by aidanr on 2006-11-19
doesn't work so well if theres multiple users with different themes

---

### Post by viciouslime on 2006-11-19
But can it not identify which user ran the sudo command and check their home directory? Or is there no way of doing that?

---

### Post by Fyda on 2006-12-23
For that, it might be better to use this:

```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
sudo ln -s ~/.fonts /root/.fonts
```

Someone correct me if I'm wrong, but wouldn't that rewrite the path for the current user each time, thus making it work? It would probably be a problem if you were actually logged in as root (since, then, ~ would be pointing recursively at itself), but since Ubuntu has disabled that, I don't see it being a problem.

---

### Post by mcduck on 2006-12-24
> **Fyda said:**
> For that, it might be better to use this:

```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
sudo ln -s ~/.fonts /root/.fonts
```

Someone correct me if I'm wrong, but wouldn't that rewrite the path for the current user each time, thus making it work? It would probably be a problem if you were actually logged in as root (since, then, ~ would be pointing recursively at itself), but since Ubuntu has disabled that, I don't see it being a problem.

no, it will change the path to real one when you execute the command, so it will still only link the directories from the user who runs the command.

The question is why there should be more than 1 user with access to admin tools?

And why it isn't done by default? At least I like to easily see if some app is running as root..

---

