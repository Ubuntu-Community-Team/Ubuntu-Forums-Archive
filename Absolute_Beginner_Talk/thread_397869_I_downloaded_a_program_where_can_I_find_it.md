---
title: "I downloaded a program where can I find it"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by viciouspoultry on 2007-03-31
I know this is a very basic question but I downloaded BitTornado using the terminal but now I don't know where it is. Can someone tell me where I can find it/ make it run?

---

### Post by eljalill on 2007-03-31
You can find it with 
```
 locate [Programmname] 
```
"man locate" tells you more about this command. Exit the manual with "q" .

---

### Post by arron on 2007-03-31
did you install it with apt at the prompt?  Or did you just download the .deb package?  or maybe a .exe from a site?


$ apt-cache search tornado
bittornado - bittorrent client with enhanced curses interface
bittornado-gui - bittorrent client with enhanced GUI interface

If you got the gui, look in your Internet programs in your main menu, if not try

```
 bittornado
```

---

### Post by viciouspoultry on 2007-03-31
I don't have the GUI and can't find a way to launch it up though it is installed on my system. I installed with apt from the terminal

---

### Post by seshomaru samma on 2007-03-31
what happens when you open a terminal and write 
```
bittornado 
```
and then click enter?

---

### Post by viciouspoultry on 2007-03-31
It says command isn't found

---

### Post by arron on 2007-03-31
You can use the add-remove programs for bittornado. to get the gui run

```
 sudo apt-get-install bittornado-gui
```

then it should be in your menu.  I assume you want the gui?  Post what you get whn u run this.

---

### Post by Maestro23 on 2007-03-31
In termial:

> whereis bittornado

Should give you the path to the bin file.

---

### Post by viciouspoultry on 2007-03-31
Package bittornado-gui is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package bittornado-gui has no installation candidate

This is what it gave me

---

### Post by Maestro23 on 2007-03-31
> **viciouspoultry said:**
> Package bittornado-gui is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package bittornado-gui has no installation candidate

This is what it gave me

It's there, you might need to enable some extra repositories.

Synaptic(GUI): [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

CommandLine: [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

### Post by viciouspoultry on 2007-03-31
Thank you I got it to download the gui

---

### Post by Maestro23 on 2007-03-31
Good deal vicious.  Can you go back and edit your first post to RESOLVED.  Edit and go to advanced.

Thanks and glad we could help ya.

---

