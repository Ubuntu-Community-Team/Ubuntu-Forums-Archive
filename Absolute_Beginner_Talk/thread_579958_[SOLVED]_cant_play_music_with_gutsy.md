---
title: "[SOLVED] cant play music with gutsy"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by dynamethod on 2007-10-18
hey i use banshee and after upgrading to gutsy, i cant play music anymore, theres no error messages, just nothing happens :s

---

### Post by dynamethod on 2007-10-18
wth...... its not doing anything at all!? i just tried reinstalling banshee and when i select an  mp3 to play it just sits there...

---

### Post by lbelloq on 2007-10-18
MP3 support is not enabled by default in Ubuntu.
Open a terminal and write ```
sudo apt-get install gstreamer-plugins-ugly
``` That should do the trick.

---

### Post by dynamethod on 2007-10-18
E: Couldn't find package gstreamer-plugins-ugly


:S

---

### Post by lbelloq on 2007-10-18
Aaah... eeerm...
Go to System-Administraton-Software sources and make sure all the repositories are enabled.
Then try again the command.

---

### Post by ThrobbingBrain66 on 2007-10-18
That's not the correct name for the package.  Use synaptic to search for gstreamer plugins....you'll find it there.

EDIT: it's gstreamer0.10-plugins-ugly

---

### Post by dynamethod on 2007-10-18
i just checked synaptic and i found gstreamer0.10-plugins-ugly which is already installed

still unable to play mp3's etc :S

---

### Post by ThrobbingBrain66 on 2007-10-18
Open Banshee using a terminal and look to see if it spits any errors when you try to play mp3s.

---

### Post by stijngysemans on 2007-10-18
of try to play an mp3 in "Totem". This program automatically searches for a codec. If it plays your mp3 witouth a problem, it can maybe be related to a banshee problem!

---

### Post by dynamethod on 2007-10-18
ok sorted it but godam this is a pain in the a$$!!!  i have to select each and individual mp3 file and select "open with" banshee, man this is stupid!

---

### Post by stijngysemans on 2007-10-18
Maybe rhythmbox works fine for you?

---

### Post by haldor61 on 2007-10-19
i have exactly same problem with totem.. when i try to run something on totem such as .avi, or .mp3 it says "totem starting" and then nothing it just disaappears.. however, when i try to run same mp3 on xmms there is no problem it's working perfectly.actually it doesn't matter what the file is because when i  try to open totem just totem it doesn't work, either

---

### Post by Mr_bleu on 2007-10-21
This thread's marked solved; I don't see the solution.

---

### Post by papodaca on 2007-10-22
so is the solution just to use a different media player?
i can't tell you how much I like banshee it worked in fiesty but is a no go in gutsy

---

