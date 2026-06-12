---
title: "shortcut question"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by revilot on 2006-07-18
I use the java game server browser for warsow (video game).  I want to make a shortcut to it on my desktop.  The thing is as of now I'm only able to run it through terminal, first cd'ing to the directory it's in, then using this command:

```
java -jar wswBrowser.jar
```

I'd rather just be able to click an icon instead of having to remember that code everytime i want to start it up.

First I had to run this in terminal and select java vm as default.  It says There are 3 alternatives which provide `java':

```
sudo update-alternatives --config java 
```

I have this one set:

```
/usr/lib/jvm/java-gcj/jre/bin/java
```

Any ideas?

---

### Post by reacocard on 2006-07-18
create a shell script to execute the commands for you. something like this:

```
#!/bin/sh
cd /directory/of/game
java -jar wswBrowser.jar
```

replace /directory/of/game with the place you need to cd to. save that as something like launchwarsow.sh and make it executable. double-click on it to launch the game.

---

### Post by revilot on 2006-07-18
> **reacocard said:**
> create a shell script to execute the commands for you. something like this:

```
#!/bin/sh
cd /directory/of/game
java -jar wswBrowser.jar
```

replace /directory/of/game with the place you need to cd to. save that as something like launchwarsow.sh and make it executable. double-click on it to launch the game.

Great, that worked like a charm.  It asks me if I want to run it or display it's contents when i double click it, is there any way to have it just run automatically?  Thanks again.

---

### Post by jayemef on 2006-07-18
Instead of a shell script, just create a shortcut on your desktop as you normally would, using any application you want (sorry, I can't walk you through this at the moment). Once you've done this, right-click on your shortcut, click on Properties, and find the tab that shows what command is getting executed. Replace the command with
```
java -jar /directory/of/game/wswBrowser.jar
```
Then change any of the comments, the name of the shortcut, and the displayed icon as you deem fit.

---

### Post by reacocard on 2006-07-18
or just create a launcher for the script :D right-click on the desktop and choose 'create launcher', then put the path of the script in 'command'. i'd reccommend moving the script to /home/yourusername/bin to get it out of the way.

---

### Post by jayemef on 2006-07-18
The problem with the script is that all it does is execute another executable, making it redundant. Why execute one thing that will just execute something else, when you can execute that something else directly?

The script works... it's just not as clean.

---

### Post by reacocard on 2006-07-18
> The problem with the script is that all it does is execute another executable, making it redundant. Why execute one thing that will just execute something else, when you can execute that something else directly?

The script works... it's just not as clean.


very true. but sometimes an executable must be executed from a certain directory. mupen64, for example, stores some of its config files in the current directory. if it's run from a different directory, it loses the settings set the last time it was run. i created a script that fixes this by always cding to the mupen64 directory. but yes, linking directly is cleaner. on the other hand, with my way, since the script is in my PATH, i can just execute [FONT="Courier New"]mupen64[/FONT] to run it.

---

