---
title: "realplayer install"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by guderian on 2006-09-14
i have read the install notes and other threads for realplayer installation and i get to the following point:

**'To add the RealPlayer plugin to firefox, copy the files nphelix.so and nphelix.xpi from the */RealPlayer/plugins folder to the firefox plugins folder at /usr/lib/firefox/plugins. If the files are not located in the RealPlayer folder, look for it in the "*/mozilla/plugins" folder.'**

i have located the above files but it won't let me copy the files into the firefox folder. says i don't have authority.
i have only one user setup and it's the original install user.
i have not altered any access settings since the install. 

i'm sure this will be any easy one for you lot...

regards,
a linux virgin

---

### Post by deadgobby on 2006-09-14
You you tried installing Automatix? It saves a lot of time.
Gobby
[http://ubuntuforums.org/showthread.php?t=177646&highlight=Automatix](http://ubuntuforums.org/showthread.php?t=177646&highlight=Automatix)
[http://ubuntuforums.org/showthread.php?t=138405&highlight=Flash+Player](http://ubuntuforums.org/showthread.php?t=138405&highlight=Flash+Player)

---

### Post by Najand on 2006-09-14
You need to use "sudo", use this command in terminal:
```

sudo cp */RealPlayer/plugins/nphelix.so /usr/lib/firefox/plugins
sudo cp */RealPlayer/plugins/nphelix.xpi /usr/lib/firefox/plugins

```

---

