---
title: "Trying to burn a DVD"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by tarchy on 2007-10-22
Okay so I'm burning files to DVDs and none of them work. It worked with Nero on Vista..

I have used every program imaginable, I try to burn .BIN files, .CUE files... I can't find a program like Daemon tools to convert to .ISO, so I haven't tried that yet.

I have tried burning .AVI files to disk, they do not work.

Please help me, I have hundreds of movies and nowhere to watch them (I hate watching it on my computer)

---

### Post by tarchy on 2007-10-22
And it comes up ALWAYS as "Disk Error" on my DVD player.

---

### Post by ramjet_1953 on 2007-10-22
I've had good success with k9copy for copying and compressing DVD9's down to DVD5's. It provides a very good copy, which is virtually indistinguishable from the original.

[COLOR="Red"]sudo apt-get install k9copy[/COLOR]

I then use k3b to burn the image to a DVD.

[COLOR="Red"]sudo apt-get install k3b
[/COLOR]
Even though k9copy does offer the option to burn directly to DVD, I've found it a bit flakey and prefer to just let it create the iso file.

Both of these packages are KDE, but they work fine under GNOME.

ps Don't forget that you will need [COLOR="Blue"]libdvdcss2[/COLOR] installed, as well.

Regards,
Roger :cool:

---

### Post by MrKlean on 2007-10-22
I switched to brasero....it's a gnome proggie...but..I found I have to burn my dvd's at 4x to get a good copy ...might wanna try that !

---

