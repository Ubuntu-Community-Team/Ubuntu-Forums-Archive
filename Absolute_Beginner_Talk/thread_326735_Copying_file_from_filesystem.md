---
title: "Copying file from filesystem"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by Daergeth on 2006-12-28
Ok, I need to copy a file from usr/games to my Desktop, I know you use cp (file name) (dir), but when I try sudo cp (filename) (mike/Desktop) it says that that directory doesnt exist, any help here?

---

### Post by cotcot on 2006-12-28
And do you see the file with nautilus ? Or can you find your file with find file ?

---

### Post by pseudonym on 2006-12-28
Depending on where you are, you may need to type the full path to your destination directory ie. /home/mike/Desktop . This can also be simplified to ~/Desktop

Also, if you're copying to your /home, you shouldn't use 'sudo'. This will result in the file being 'owned' by root user, and not you. As user, you can read (most) things in directories like /usr etc. (just not write), so you don't need 'sudo' to access them.

---

### Post by Daergeth on 2006-12-28
Ah, that worked wonderfully. It also brings up another question.
Let me try to explain as best as I understand it. Im trying get the file as an icon on my desktop bar. Whenever I cp it to desktop then move it over to the bar, then click on it to start it, it says it cannot open the file. The file is something I made to tell the original program to look at the file when starting up (Im sorry if that is hard to understand). So, how can I make it so I dont have to go into /usr/games and type sudo ./run (name of file) everytime I want to run tintin++ ?

---

### Post by po0f on 2006-12-28
Daergeth,

You can create a launcher with `sudo /usr/games/tintin++` as the command.

---

### Post by Daergeth on 2006-12-28
Create a launcher, gotcha. Hold on a sec though, how do I go about doing that? Im a total Linux newbie :D Thanks for the reply!

---

### Post by pseudonym on 2006-12-28
> **Daergeth said:**
> Create a launcher, gotcha. Hold on a sec though, how do I go about doing that? Im a total Linux newbie :D Thanks for the reply!
If this is a game you shouldn't need to run it as sudo. I don't use gnome desktop but I think you can create a launcher by right-clicking your desktop and choosing 'create launcher...' :) Where it asks you for a command to start your game, just enter 'tintin++' (without quotes). The same principle works for setting up launches on the panel.

HTH

---

