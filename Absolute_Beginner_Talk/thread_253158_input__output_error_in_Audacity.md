---
title: "input / output error in Audacity"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by tobmeister on 2006-09-07
Hey All,

I finally got Audacity loaded but now its telling me that I can't record or listen to audio files (basically all the things I need).  I know that for my WIN system, I had to add Mplayer to it to get it to work, does anyone have any suggestions??

Thanks

Tobmeister

:confused:

---

### Post by CatKiller on 2006-09-08
> **tobmeister said:**
> Hey All,

I finally got Audacity loaded but now its telling me that I can't record or listen to audio files (basically all the things I need).  I know that for my WIN system, I had to add Mplayer to it to get it to work, does anyone have any suggestions??

Thanks

Tobmeister

:confused:

Go to System -> Preferences -> Sound and uncheck "Enable software sound mixing (ESD)" before you use Audacity. For some reason, Audacity and ESD don't get on.

You won't get system sounds while ESD is off, but you probably don't want them when you're using Audacity. You can turn ESD back on if you want after you've finished in Audacity.

---

### Post by liquilife on 2006-10-06
Hmm, I was having the same issue and your solution didnt work for me. Any further ideas?

---

### Post by Zimmer on 2006-10-06
> **liquilife said:**
> Hmm, I was having the same issue and your solution didnt work for me. Any further ideas?

Make sure you do not have another sound app running at the same time.
Also in Preferences disable the system sounds...
These are the simple things and having gotten Audacity to work some time ago I have forgtten if there was anything else I did to make it work...I wwill go away and search my old brain cells a bit firther...

---

### Post by doobit on 2006-10-06
Open the mixer and make sure the wav and PCM and master levels are up and not muted. It the preferences uncheck or check the Playthrough and Play other tracks boxes under Audio I/O depending on what they are. I had to mess a little with that until I got the effect I wanted.
Also make sure you have the correct devices chosen.
Are your other sounds working OK?

---

### Post by liquilife on 2006-10-06
Thank you kindly for the responces. Sound works great throughout the rest of ubuntu. In Audacity I have two options for sound and that is my usb speakers and usb headset - neither of which work. For my sound engine I only have ALSA to select from. When I open audacity i get an error saying there is no supported i/o device (or some such). I'm away from the Ubuntu machine right now so I can't try anything :(

The only other app I had running was Gaim. Unchecking ESD before launching Audacity did not help as well.

---

### Post by CatKiller on 2006-10-06
You could try a **sudo killall esd**. Don't know how much it would help. There is a thread that you might find interesting called something like "the comprehensive sound problems thread". Should be worth a look. There's also the Ubuntu Studio project - they ought to have plenty of information on how to get the sound in Linux to do what they want.

---

### Post by liquilife on 2006-10-06
Awesome, I'll give the "sudo killall esd" trick a go tonight. The ubuntu studio project, never heard of it. I'll be sure to check it out. Thanks again for the swift responces! I'll check in later when I have access to ubuntu again and let you know what I found out :)

---

### Post by Zimmer on 2006-10-06
> **liquilife said:**
> Awesome, I'll give the "sudo killall esd" trick a go tonight. The ubuntu studio project, never heard of it. I'll be sure to check it out. Thanks again for the swift responces! I'll check in later when I have access to ubuntu again and let you know what I found out :)

You could also try changing your esd.conf file to

[esd] 
auto_spawn=0
spawn_wait_ms=100
default_options= -terminate -nobeeps -as 2

(Back up the original, of course)

---

### Post by kaplanmyrth on 2006-10-06
I was getting the i/o error message that others have reported running audacity, and it wasn't fixed by killing esd. In the end, I did ps -A and scanned through the processes to see what was running, and mplayer was in there -- twice! There was no evidence that it was running on the desktop, but it was listed in the ps output. I did sudo killall mplayer (had to do it twice to kill them both), and then audacity just ran.

---

### Post by liquilife on 2006-10-07
I uninstalled Audacity. I then performed the "sudo killall esd" in the terminal and reinstalled Audacity and it's working :D

Ooops.. well it still is having issues. I get no sound when I import an MP3 for editing.

---

### Post by Zimmer on 2006-10-08
> **liquilife said:**
> I uninstalled Audacity. I then performed the "sudo killall esd" in the terminal and reinstalled Audacity and it's working :D

Ooops.. well it still is having issues. I get no sound when I import an MP3 for editing.

For your MP3 Have you got liblame0 installed? Have you shown Audacity where it is (usr/lib) via the preferences  ?  That is necessary for you to be able to export mp3, so I guess it may be necessary in order to play one, too...

---

### Post by Coburn on 2006-12-06
> **CatKiller said:**
> Go to System -> Preferences -> Sound and uncheck "Enable software sound mixing (ESD)" before you use Audacity. For some reason, Audacity and ESD don't get on.

You won't get system sounds while ESD is off, but you probably don't want them when you're using Audacity. You can turn ESD back on if you want after you've finished in Audacity.

"for some reason" sounds pretty interesting to me.

I would like to know the reason.

I have a computer that I upgraded to Dapper from a Breezy CD.  It took forever on dialup--don't ask!  It runs Audacity just fine with ESD and System Sounds checked _on_.

I have another one with Dapper installed from its own CD--one of the first released, if that helps.  It requires you to uncheck one of the two for Audacity to play sounds.  I just noticed it lately.  I've had Audacity on there for months, but I don't think I've actually used it on this one.

Update:

I noticed posts in this thread that were not viewable when I posted.

I will try reinstalling audacity with esd off.

I will leave my post as interesting information for future users.

---

### Post by kwiter on 2007-11-11
I'm unable to set an input device in Audacity. I turned ESD off too but still no joy.

Nia:wen Thank you.

---
[http://www.urbanskinz.com](http://www.urbanskinz.com)

---

