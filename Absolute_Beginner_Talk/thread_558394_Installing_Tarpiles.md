---
title: "Installing Tarpiles"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by Cheese Roller on 2007-09-23
Okay, it's about time I learn how to do this.

Can you guys please guide me through the process of installing Tarpiles?

I don't wanna hear you just tell me to find a .deb file of it, because sometimes that really doensn't exist.

---

### Post by Maestro23 on 2007-09-23
**tar** command

[http://www.psychocats.net/ubuntu/installingsoftware#source](http://www.psychocats.net/ubuntu/installingsoftware#source)

*Keep in mind that depending on what you are installing, you may run into dependency issues which must be resolved before installation.
Also, there is usually a README/INSTALL doc in the extracted folder after you run the tar command on the tarball.

Good luck.

---

### Post by Cheese Roller on 2007-09-23
On another note, what type of file is this?

[http://graalonline.com/zone/downloads/file?name=graal4setup](http://graalonline.com/zone/downloads/file?name=graal4setup)

---

### Post by overdrank on 2007-09-23
> **Cheese Roller said:**
> On another note, what type of file is this?

[http://graalonline.com/zone/downloads/file?name=graal4setup](http://graalonline.com/zone/downloads/file?name=graal4setup)

HI maybe this link will help and it was a bin file as I saw
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
Good luck! :)

Although the first link was a good one !

---

### Post by Cheese Roller on 2007-09-23
Well, How would I install a binary file like that?

I miss this game.

---

### Post by yuku-aki on 2007-09-23
Yes, but as a warning, I spent HOURS compiling software to satisfy dependencies on some simple thing that I wanted to install, sometimes to no avail.  Maybe there's not support for your particular hardware on this release, or it's a beta that sucks, or you didn't install several libraries upon original OS installation.... it could be anything.  I think after all that experimentation I'm back to apt-get and synaptic.

---

### Post by Hospadar on 2007-09-23
usually .bin files are binary shell script files.  generally these are run with a command like ```
sudo sh <name of file>
```

---

### Post by Maestro23 on 2007-09-23
Executing .bin files: [http://www.cyberciti.biz/faq/howto-unix-command-run-execute-bin-files-in-linux/](http://www.cyberciti.biz/faq/howto-unix-command-run-execute-bin-files-in-linux/)

---

### Post by yuku-aki on 2007-09-23
Ok, so... you should take note of where downloaded files are saved on Firefox, or just click Tools->Downloads then right click "Open", choose "Open containing folder", right click on the file, then go to "Open with other application" - at the bottom you'll see "Use a custom command" click on it and enter "sh" (with no quotation marks, of course... sorry for not using a different font for code, I'm lazy today.) then hit Enter, and you should soon see directions and specifics on the software itself.

---

### Post by yuku-aki on 2007-09-23
Sorry for the multi-post, but I'd better add that this experiment/solution was using GNOME... I can't say the same is applicable in KDE or any other window manager.

---

### Post by Cheese Roller on 2007-09-23
Delete this post and the one below it please.

---

### Post by Cheese Roller on 2007-09-23
-

---

