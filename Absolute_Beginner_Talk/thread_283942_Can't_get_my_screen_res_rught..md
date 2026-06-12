---
title: "Can't get my screen res rught."
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by mtjnkee on 2006-10-24
Just started using Ubuntu and this machine was running XP before. Now my screen resolution qill get no higher that 640/480. The menu will not let me choose a higher setting. Does anyone know how to do this? By the way all my windows extend outside of my desktop, I have to alt+click and drag to line the menu bars up.

---

### Post by CatKiller on 2006-10-24
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

You'll probably want to find out your monitor's specifications and enter them at the appropriate time.

EDIT: Crikey, that sounded terse. Didn't mean it to. Welcome to the community. And to get to the terminal to type in the above command, it's Applications -> Accessories -> Terminal. Type in the password you used to log in with. It won't show that you're typing anything for the password, but that's supposed to happen.

---

