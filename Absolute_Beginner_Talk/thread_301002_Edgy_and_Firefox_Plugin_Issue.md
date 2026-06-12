---
title: "Edgy and Firefox Plugin Issue"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by drenicky79 on 2006-11-16
At least I think it's a plugin issue. Here's what happened:

Installed Edgy on a separate HD on my system and all went beautifully.

Browsed around using Firefox 2.0 for while and then encountered a web page with Flash content. Firefox prompted me to install the Flash plugin, which I did. Restarted Firefox and now whenever I navigate to this page, or any page with flash content of any sort, Firefox bites the dust. 

Tried to remove the plugin. Not sure if I was successful since I am still learning the whole LINUX universe here. In any case it didn't work. Any flash content shuts down the browser. I downloaded Mozilla and discovered that it did exactly the same thing. Tried Galeon and IT did the same thing too. I'm fine if the page has no flash content (thankfully this site works fine), but the moment flash appears, BOOM, lights out.:-k 

Anyone else encounter this? If so, how might I go about fixing it? Would examining Firefox's error console yield any clues?

---

### Post by localuser on 2006-11-16
Not sure what may have happened, but the best way to install Flash for Firefox is with Automatix.

[http://www.getautomatix.com/](http://www.getautomatix.com/)

You may want to install Flash via automatix to see if it fixes the problem.

This isn't the most techie way, but it may be the simplest.

---

### Post by drenicky79 on 2006-11-16
Giving that a shot. Thanks so much for the suggestion.

---

### Post by nadp on 2006-11-16
I am having that same problem
i tried various ways to install the flash plugin, through adobe's site, from the terminal, from synaptic, from automatix, all with no use =(
and the only way -that i know, cz i tried it- of fixing the problem is reinstall linux >.<

if there is any other way, plz let me know!!

---

### Post by jsteve54302 on 2006-11-16
Have you tried opening a terminal and:

sudo rm /usr/lib/<browserdir>/plugins/libflashplayer.so

where <browserdir> is the folder coresponding to the browser that's crashing?  Repeat for all crashing browsers.

Technically, that should remove the plugin from the browsers' view, allowing it to run even if the plugin is still present elsewhere on your system.

Does this help?

---

### Post by jsteve54302 on 2006-11-16
Oh, sorry - forgot to mention, you'll have to close all instances of your browser to unload the plugins from RAM, the reopen it...

---

### Post by drenicky79 on 2006-11-16
libflashplayer.so does not exist in the firefox folder, so I must have been successful in removing it before. 

Will try the Automatix angle later tonight and report back.

---

### Post by drphilngood on 2006-11-16
[Solution to flash-related Firefox 2 crash in Edgy]("http://ubuntuforums.org/showpost.php?p=1672572&postcount=1")
Hope this helps.

---

### Post by drenicky79 on 2006-11-16
Thank you, dr. That link provided the solution to my problem. Firefox works once again. 

For those of you who might be having the same problem, the fix was:


In the /etc/firefox/firefoxrc file, insert this line:

```
export XLIB_SKIP_ARGB_VISUALS=1
```

---

### Post by Tejasen on 2006-11-18
Hi,

This cause by exception fired in 16 bit display mode.

I solved by change to 24 bit display mode.
Edit your /etc/X11/xorg.conf to change to 24 bit display.

See more information about problem of Edgy on my site [http://www.tejasen.com](http://www.tejasen.com)

Cheers.
Jim

---

