---
title: "[SOLVED] trying to make a sghortcut to a program"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by Shadowmeph on 2008-02-22
ok I play Enemy Territory and there is a automatic map download program that I use to download maps for the server I play on what I want to do is make a shortcut to this program so I don't have to type the command into the terminal all of the time( because I always forget the command) . the command I use to open the program is  ":cd ~/.etwolf/"
then I type in  "java -classpath ETManager.jar etm".Main and it opens up what I have tried to do is create an application launcher then first put this command in "gksudo nautilus/home/dallas/.etwolf/ java -classpath ETManager.jar etm.Main" which does nothing
then I tried java -classpath ETManager.jar etm.Main which does nothing as well. I am not sure if there is a way to make a sshort cut to this program if there is could some one explain how I can do this please :)

---

### Post by stchman on 2008-02-22
> **Shadowmeph said:**
> ok I play Enemy Territory and there is a automatic map download program that I use to download maps for the server I play on what I want to do is make a shortcut to this program so I don't have to type the command into the terminal all of the time( because I always forget the command) . the command I use to open the program is  ":cd ~/.etwolf/"
then I type in  "java -classpath ETManager.jar etm".Main and it opens up what I have tried to do is create an application launcher then first put this command in "gksudo nautilus/home/dallas/.etwolf/ java -classpath ETManager.jar etm.Main" which does nothing
then I tried java -classpath ETManager.jar etm.Main which does nothing as well. I am not sure if there is a way to make a sshort cut to this program if there is could some one explain how I can do this please :)

You can make a script to automate those functions.  Please give me the commands more clearly.  It looks like you type this:

```

cd ~/.etwolf/
java -classpath ETManager.jar etm.Main

```

Are those the correct commands?  If yes then create a script called etwolf.sh in your ~/Desktop with the following:
```

#!/bin/sh

cd ~/.etwolf/
java -classpath ETManager.jar etm.Main

```

Once this done then give the script executable permissions:
```

chmod 755 ~/Desktop/etwolf.sh

```

You will have an icon on your desktop and you can just double click it.

---

### Post by Shadowmeph on 2008-02-22
> **stchman said:**
> You can make a script to automate those functions.  Please give me the commands more clearly.  It looks like you type this:

```

cd ~/.etwolf/
java -classpath ETManager.jar etm.Main

```

Are those the correct commands?  If yes then create a script called etwolf.sh in your ~/Desktop with the following:
```

#!/bin/sh

cd ~/.etwolf/
java -classpath ETManager.jar etm.Main

```

Once this done then give the script executable permissions:
```

chmod 755 ~/Desktop/etwolf.sh

```

You will have an icon on your desktop and you can just double click it.

Excellent thank you so much :)

---

