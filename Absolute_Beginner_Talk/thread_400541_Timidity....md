---
title: "Timidity..."
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by Darklighter137 on 2007-04-03
Hi guys!  No matter how I try and use timidity for playing midi's, whether it be through the xmms plugin, running it from the terminal, running it with a GUI, etc., it has a tendency to crash.  If you let it just play the track the whole way through, it's fine.  But if you try quitting before it's done (aside from a Ctrl-C in the terminal), the sound system locks up and the program using timidity won't die.  This can only be fixed by going into the System Monitor and manually removing the timidity processes.

Is this normal behavior for the program, or is it my awful, integrated sound card?

---

### Post by olskar on 2007-04-03
Dont know whats normal...I play it with " timidity file.mid" in the terminal..works fine for me

---

### Post by Darklighter137 on 2007-04-03
I'm currently doing the same thing, but I'm looking to get a graphical thing set up that works well too.  ^_^

---

### Post by DagMan on 2007-04-07
search in synaptic for timidity and find timidity-extras or some other related timidity packages.  I'm not on an ubuntu box to look myself at the moment.  After you have those you can start timidity with a few gui's one of which is a gtk front end.  Read the manual page for the package but it's an additional switch, -ag or something like that.  It works well apart from the slider doing nothing, the playlist not doing much, and the software volume control doing nothing but aside from that it is pretty :P 
Also if you run into needing to pass things to timidity for example streaming sound from the web, then you can pass it to one of the gui's instead of timidity at the shell which makes it more difficult to stop playback right away.

---

