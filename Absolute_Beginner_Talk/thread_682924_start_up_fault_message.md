---
title: "start up fault message"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by crawall on 2008-01-30
during start up i get a message saying that the file .dcrm will be ignored.

what should i do?

---

### Post by taurus on 2008-01-30
Open a terminal and run

Applications -> Accessories -> Terminal
```
sudo chown username:username /home/username/.dmrc
sudo chmod 644 /home/username/.dmrc
```
Replace _username_ with your actual login name

---

### Post by crawall on 2008-01-30
the start up didn't change. The complete message is as follow:
"User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 premissions. User's $HOME directory must be owned by user and not writable by other users."

so what can i do to solve this

---

### Post by taurus on 2008-01-30
Did you run those two commands from my previous post and did you remember to replace **[COLOR="Blue"]username[/COLOR]** with your actual login name?

Otherwise, post the outputs of these commands.

```
id
ls -la ~/.dmrc
```

---

### Post by crawall on 2008-01-30
OK I found the solution in the general forum

[http://ubuntuforums.org/showthread.php?t=405368&highlight=.dmrc](http://ubuntuforums.org/showthread.php?t=405368&highlight=.dmrc)

thanks anyway

---

