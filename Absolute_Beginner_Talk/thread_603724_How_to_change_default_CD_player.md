---
title: "How to change default CD player"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by john262 on 2007-11-05
I use Gutsy. Right now my default audio CD player is Sound Juicer. That's the player that pops up on screen when I insert an audio CD.

But I want to change my default CD player to the Gnome CD Player. How can I do that?

I already went to the Removable Drives and Media applet and I saw that under the Multimedia tab Sound Juicer was listed using the following string:" sound-juicer -d %d." (Without the quotes)

So I tried changing that to both "cd-player -d %d"  and "cdplayer -d %d" and neither worked. I tried browsing the file system for the CD player but I couldn't find it.

So can someone please tell me how to make this work? Thank you.

---

### Post by logos34 on 2007-11-05
try 
> 
gnome-cd

---

### Post by Happy_Man on 2007-11-05
I believe it is in "default applications". I can't be sure, as I'm not on an Ubuntu computer right now.

---

### Post by john262 on 2007-11-05
Thanks. I tried both suggestions and neither worked. Maybe I'll just have to turn off "Play Audio Disks When Inserted" and just open the CD player manually.

---

### Post by logos34 on 2007-11-05
It should be installed by default as part of the gnome desktop media utilities pkg.

try 

**sudo apt-get install gnome-media**

it shows up as 'cd player' in apps>sound & vid

---

### Post by john262 on 2007-11-05
Yes, the CD player is already installed. But what I cannot do so far is get it to start automatically when I insert an audio CD.

---

### Post by mdebusk on 2007-11-05
> **john262 said:**
> But I want to change my default CD player to the Gnome CD Player. How can I do that?

You might scan [thread=333714]this thread[/thread] for ideas.

---

### Post by john262 on 2007-11-05
Thanks for yuor help everybody. I finally figured it out. The command that I needed was "/usr/bin/gnome-cd." Now it works.

---

### Post by logos34 on 2007-11-05
> **john262 said:**
> Thanks for yuor help everybody. I finally figured it out. The command that I needed was "/usr/bin/gnome-cd." Now it works.

I thought to suggest that but it's supposed to check /usr/bin automatically (which is where almost all program executables are stored and why the command alone is usually sufficient)...Mine works with either gnome-cd or /usr/bin/gnome-cd.  hmm.

---

