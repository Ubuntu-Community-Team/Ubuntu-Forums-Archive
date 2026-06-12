---
title: "nautilus in command line"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by montag451 on 2006-07-18
I'm not sure if nautilus should do this, but nautilus doesn't seem to respond correctly to relative paths.

Just running the 'nautilus' command seems to open your home director by default. However, if you're in a directory and specify a directory name, it looks for that directory in your current director. This seems counter-intuitive since if I'm in /home/username/folder and I type 'nautilus', I should get a browser window open to 'folder' and not /home/username.

Am I doing something wrong, or is this just the way the nautilus command is meant to act? If the latter is true, is there a way to suggest otherwise to the developers?

**Edit:** A slightly more verbose example: I'm in /home/matt/torrent in my terminal window. I type 'nautilus'. Nautilus opens, but it opens to my home directory (/home/matt). I type 'nautilus torrent'. I get an error saying "Couldn't find /home/matt/torrent/torrent." I type 'cd' to return to my home directory and type 'nautilus torrent'. Nautilus now opens to the correct directory but leaves the user feeling strangely cheated out of convenience.

---

### Post by aysiu on 2006-07-18
Once you invoke the *nautilus* command, you're no longer referencing the terminal directory.

---

### Post by brentoboy on 2006-07-18
this post sort of made me laugh when I read it.  I always want the exact opposite thing... I want to surf around in nautilus, and then open a terminal starting in the current folder where it is in nautilus.

truth be told, I dont think anyone on the GNOME dev team ever considered the idea that someone would surf around the file system and then launch nautilus and hope to be in the folder they launched from.  Most people who start nautilus expect to be at /home/username reguardless of where they were before they started it.

sorry

---

### Post by digby on 2006-07-18
What happens is that when you provide an arguement a location after the command) it references from where you are.  If you run the program w/ no arguements, it defaults to your home directory.

So to open from where you are, run```
nautilus ./
```or to open somewhere else, you either have to provide an absolute path (starting all the way back at /) or one relative to where you are.

---

### Post by Arisna on 2006-07-18
> **brentoboy said:**
> this post sort of made me laugh when I read it.  I always want the exact opposite thing... I want to surf around in nautilus, and then open a terminal starting in the current folder where it is in nautilus.


The package "nautilus-open-terminal" provides this functionality via right-click in any Nautilus window.

> **digby said:**
> What happens is that when you provide an arguement a location after the command) it references from where you are.  If you run the program w/ no arguements, it defaults to your home directory.

So to open from where you are, run```
nautilus ./
```or to open somewhere else, you either have to provide an absolute path (starting all the way back at /) or one relative to where you are.

You can even leave off the "/" in "./" in this case because "." alone represents the current directory.  If you want to work on a file called "foo" in a subdirectory called "bar", however, you would need to use <Command> ./bar/foo

---

### Post by montag451 on 2006-07-18
No problem. 'nautilus .' makes sense, I just didn't know the notation for it. Thanks for the insight, and thanks for the nautilus-open-terminal suggestion.

---

