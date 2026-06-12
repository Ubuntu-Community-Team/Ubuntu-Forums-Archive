---
title: "Proper method for uninstalling software installed from binary?"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by pbaehr on 2006-02-16
I installed the UT2k4 demo from a binary. I've got the full version and I'm going to install that now but it feels wrong not to uninstall the demo first. Is there a proper, easy way to uninstall software loaded from a binary? I'm assuming that apt-get is useless as it wasn't involved in the installation process.

Is it as simple as finding where the program was installed and removing the directory and it's corresponding menu in Gnome?

I'm interested in learning the right way since I'm relatively new to Linux.

---

### Post by Estariel on 2006-02-16
Most proprietary games you can buy use an installer that was developed by Loki (which was a company that ported games to linux).
UT also uses this installer.

When installing, you usually chose a place where you want the game to be installed.
This is normally in your home directory (unless you used the root account to install the game).

In this directory, which you specified is a program called "uninstall". (Which gets added there automatically by the loki installer on installation)

Move to the place where you installed the game to:

```
cd /home/myname/path/to/my/game
```

then run the script:

```
./uninstall
```
"./" means execute the following program which is sitting in the directory I am currently in. If you'd just type "uninstall" it would say "command not found" since ubuntu wouldn't know where the program is.


All this of course can only be done if you remember where your program got installed.
You can try finding it by typing
```
whereis commandthatstartsthegame
```
if i remember correctly, in case of the ut demo, this command is something like ut2004demo

---

### Post by pbaehr on 2006-02-16
Beautiful, thanks for taking the time to break it down for me. I'll try it when I get home.

---

