---
title: "alarm clock"
date: 2005-10-06
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2005-10-06
Does anyone know of any alarm clock that might be in ubuntu?  I'd like to use it to wake up in the morning.

Do I need to install some program?  Which one?

---

### Post by Ampersand on 2005-10-06
One possibility is installing xmms and the xmms-alarm plugin. This will allow you to set a time for music or any other sound file to start playing at a set time.

---

### Post by racermike1967 on 2005-10-06
I'm trying to limit my self from installing unnecessary programs.  Does anyone know of any script that i can run?  If so can you tell me how to?

---

### Post by Ampersand on 2005-10-06
You can use sleep together with rhythmbox (which is installed by default), assuming you've got some .wavs or .oggs (or mp3s, and installed support for them). 

Open rhythmbox from the sound & video menu, and import whatever sound file you want to wake up to. Then open a terminal, and run the command 'sleep nh && rhythmbox --play-pause' (replace n with the number of hours you want it to wait before playing, it doesn't have to be an integer.)

---

### Post by utterlyjaded on 2005-12-22
[QUOTE=Ampersand]You can use sleep together with rhythmbox (which is installed by default), assuming you've got some .wavs or .oggs (or mp3s, and installed support for them). 

Open rhythmbox from the sound & video menu, and import whatever sound file you want to wake up to. Then open a terminal, and run the command 'sleep nh && rhythmbox --play-pause' (replace n with the number of hours you want it to wait before playing, it doesn't have to be an integer.)[/QUOTE]



wow thanks

---

### Post by Kethinov on 2005-12-22
Why not just use cron?

```

crontab -e

```

Then add this:

```

30 7 * * *   xmms "/some/sound/file/somewhere"

```

That'll wake you up bright and early every morning at 7:30. Make sure to leave XMMS open, or cron won't play the soundfile. And don't forget to leave your speakers on and your sound up!

If you need more complex times set, you could install kcron, which can help you create complex crontabs visually without coding it yourself in the terminal. I love kcron! :)

---

### Post by Juippisi on 2005-12-22
As a KDE-supporter, I must suggest amaroK.

[http://amarok.kde.org/amarokwiki/index.php/FAQ#How_do_I_use_amaroK_as_an_alarm_clock.3F](http://amarok.kde.org/amarokwiki/index.php/FAQ#How_do_I_use_amaroK_as_an_alarm_clock.3F)

works fine ;-). Bad thing: You need to have ~KDE installed. Kontact, amaroK, dcop_server and kdeinit should be enough processes to have that working.

---

### Post by batigolix on 2008-05-04
sudo apt-get install sanduhr

---

