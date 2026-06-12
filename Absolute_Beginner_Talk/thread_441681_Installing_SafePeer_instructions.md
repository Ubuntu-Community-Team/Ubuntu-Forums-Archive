---
title: "Installing SafePeer instructions"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by FleetAdmiral74 on 2007-05-12
It was easy enough in Windows! I feel so helpless now...

---

### Post by taurus on 2007-05-12
And what is the problem this time?

---

### Post by FleetAdmiral74 on 2007-05-12
Oh, sorry to bother you again!

With Azureus, just wanted to know how to use the SafePeer plugin. I'm not sure if I can just dl the java file and put it in the az. dir like in Windows, because first of all I cant even find the Azureus default dir...

---

### Post by taurus on 2007-05-12
It's a hidden file so if you want to see it, run this command from a terminal.

```
ls -la ~/.azureus
```

---

### Post by FleetAdmiral74 on 2007-05-12
I did that, and it did show me a list of files in the terminal window, but I don't see how this helps me install SafePeer. I still don't see it in the etc window. Or can  I just run the java file from anywhere and it will work w/ Az?

---

### Post by taurus on 2007-05-12
If I understand you right, you want to install that SafePeer plugin for azureus.  Fire up azureus and see if you can install that plugin from azureus menu.

---

### Post by FleetAdmiral74 on 2007-05-12
Under the Plugin menu, there is no install plugin option. BDCC control panel (something about connecting to servers), an irc help chat and log views. Btw, if this matters I am got azureus from the package manager, so Im not sure if that uses a different version then I should be. On Windows there was an Install Plugins option, idk...

---

### Post by taurus on 2007-05-12
What file format is that SafePeer in?  Maybe all you need is to move it to ~/.azureus/plugins.

Make sure you are in the directory where that SafePeer plugin is, then run

```
mkdir ~/.azureus/plugins
mv filename ~/.azureus/plugins
```

---

### Post by FleetAdmiral74 on 2007-05-12
I believe the file is a .jar

---

### Post by taurus on 2007-05-12
Does it work if you move it to ~/.azureus/plugins?  Otherwise, what is the output of this command from a terminal?

```
ls -la /usr/share/azureus/plugins
```

---

### Post by FleetAdmiral74 on 2007-05-13
I moved it to the folder you suggested, and lo and behold it shows up in the azureus menu, so I am pretty sure its working. Thank you for your patience.

I guess the biggest problem for me right now is I do not know where anything goes in linux, like when a program is installed, I don't know the default dirs for anything. I would have never guessed to go in usr/shared for the Azur plugin, when privoxy I found in the etc folder.

---

