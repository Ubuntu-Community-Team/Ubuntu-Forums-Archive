---
title: "How to uninstall savage(game)?"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by pbatoon on 2007-07-03
I need to know how to uninstall the game savage. For some reason it wont start up anymore. So what I wanna do it reinstall it again to give it another shot.

Can someone guide me on the uninstallation process?

---

### Post by overdrank on 2007-07-03
> **pbatoon said:**
> I need to know how to uninstall the game savage. For some reason it wont start up anymore. So what I wanna do it reinstall it again to give it another shot.

Can someone guide me on the uninstallation process?

HI, how did you install the package?

---

### Post by KIAaze on 2007-07-03
Have you tried starting it by comand-line?
It sometimes gives useful error messages which might prevent you from reinstalling the game.

When you start programs through shortcuts, any error messages going to the standard error output or the standard output are hidden.

edit: He probably installed it with the loki installer (.run) as specified here for example: [http://gaming.gwos.org/e107_plugins/content/content.php?content.61]("http://gaming.gwos.org/e107_plugins/content/content.php?content.61")
But I have no idea how to uninstall such a game.
Maybe doing > rm -r ~/.Games/Savage/ would be enough.
Or simply reinstalling the same way without uninstalling it.

---

### Post by pbatoon on 2007-07-06
i installed the game by the package file. i first downloaded the package to my computer then did the "run as application" thing

---

### Post by pbatoon on 2007-07-07
```
batoon@batoon-desktop:~$ rm -r ~/.Games/Savage/ 
rm: cannot remove `/home/batoon/.Games/Savage/': No such file or directory

```

idk why it doesnt work?

---

### Post by KIAaze on 2007-07-07
As it says: Because there is no such file or directory.

The command I gave was assuming that you had followed this howto:
[http://gaming.gwos.org/e107_plugins/content/content.php?content.61]("http://gaming.gwos.org/e107_plugins/content/content.php?content.61")

It says at one point:
> In the installation menu, change;
Install path: /home/***USERNAME***/.Games/Savage
Uncomment: Install a symbolic link into path


So, if you left everything by default, the game was probably installed elsewhere.
Try running the installation process again to see what the default installation path is.

However, I find it strange that the game worked before and doesn't work anymore now.
Did it stop working after you did a system update or installed a program?
It might just be a library problem.

Are there any error messages if you launch the game from the terminal?
The command to run it from the terminale is probably "savage" or "Savage".

---

### Post by KIAaze on 2007-07-07
I think I found out how to correctly uninstall the game:
You have to use the [Loki uninstaller]("https://help.ubuntu.com/community/LokiInstaller").

1)Download it from here:
[http://liflg-tracker.death-row.org/torrents/loki_uninstall-full-1.0.3-x86.run.torrent]("http://liflg-tracker.death-row.org/torrents/loki_uninstall-full-1.0.3-x86.run.torrent")
It's a torrent link, so you'll have to use Ktorrent or Azureus for example.

2)Run > sudo sh loki_uninstall-full-1.0.3-x86.run

How it works:
> When you install a game the installer creates an own file (name_of_game.xml) in ~/.loki/installed/ with all installation settings like the files which are copied to the game directory.
uninstall use this file so you can't uninstall the game if you have not backuped this file before wiping /home.
I don't think that there is a way to recreate it without a new installation. But you should be able to install it over the old installation. Better backup important game files before doing it.
[http://liflg.org/forum/viewtopic.php?=&p=4104]("http://liflg.org/forum/viewtopic.php?=&p=4104")

---

