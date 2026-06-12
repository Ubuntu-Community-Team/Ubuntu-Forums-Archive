---
title: "Firefox does not start after clean install and update of 7.10"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by supersk on 2007-11-10
I just installed ubuntu 7.10 on my computer.  I then installed all of the latest updates which updated Firefox as well.

After restarting the computer, when I click on Firefox through the system menu, on the taskbar it indicates "Starting Firefox" but then disappears.  And then nothing else happens.

i've verified that I have an Internet connection and that ubuntu was able to access it to discover and download the latest updates.

not sure why Firefox isn't launching.  I'm new to ubuntu but are there any error logs I can check?  What should my next trouble-shooting steps be?

FYI: Immediately after the updates were downloaded and installed, I tried the "Suspend" feature for ubuntu.  My screen then showed a "checkerboard" type of image of various colors.  It was completely unresponsive - I had to do forced reboot.  Could this have affected Firefox?

Thanks for any suggestions that can help me.

---

### Post by por100pre1 on 2007-11-10
Check if setting up a new profile fixes the issue. Copy, paste and ENTER this command in Terminal (**Applications> Accesories> Terminal**):

```
firefox -ProfileManager
```

BTW, welcome to the forums!

---

### Post by supersk on 2007-11-10
thanks for the welcome.

When I type that in I get:

Bus error (core dump)

From a Windows XP user perspective, core dumps are never good news.

---

### Post by tubasoldier on 2007-11-10
it sounds as if you might have and extension or setting that is not compatible with the new version. it happens sometimes.

i would reccomend removing the /home/~/.mozilla  folder. This will remove any settings and extensions you might possibly have. You can also change its name if you want to keep it as a backup for any reason.

---

### Post by supersk on 2007-11-10
actually there are no extensions in this firefox.  I haven't touched it in terms of adding anything to it.

basically I installed ubuntu -> ran updates -> and then attempted to run Firefox for the first time.

I tried what you suggested by deleted the .mozilla folder on my home directory.  No luck - same error.

---

### Post by alienexplorers on 2007-11-10
Completely remove the .mozilla folder.  Firefox will rebuild this file the next time you run it.  You will have to reload your plugins and extensions.

---

### Post by supersk on 2007-11-10
I just reinstalled the firefox package via Synaptic Package Manager and that seemed to have fixed the issue.

I can actually launch Firefox now.  I still want to understand why Firefox didn't work initially and I'll keep my eye out on the problem in the future.

thanks for everyone who replied on this thread.

---

### Post by jayach on 2008-02-05
I am having this same issue.  I just upgraded from 7.04 to 7.10.  I try to start firefox, get the message it is starting, but never actually comes up. If I try the profile selection option (-ProfileManager), it allows me to create or select another profile, but after that, no more gui.   I can see it running, but the gui doesn't show up:

```

$ ps -ef | grep firefox
6766     1  0 17:53 ?        00:00:00 /bin/sh /usr/bin/firefox
6778  6766  0 17:53 ?        00:00:00 /bin/sh /usr/lib/firefox/run-mozilla.sh /usr/lib/firefox/firefox-bin
6782  6778  0 17:53 ?        00:00:00 /usr/lib/firefox/firefox-bin
6821  6529  0 17:59 pts/0    00:00:00 grep firefox

```

  
I have tried deleting the .mozilla directory and reinstalling firefox as suggested here, but the problem persists.  I am only able to access the web by running firefox within my Win XP vm (this isn't anything to be proud of!).  Thanks for any suggestions-

---

### Post by Bothered on 2008-02-05
Have you tried running firefox from a terminal, to see if there are any error messages?

While you're having firefox issues you can always use and alternative browser in ubuntu rather than in a vm, e.g. any of the packages: epiphany-browser, iceape-browser, opera.

---

### Post by jayach on 2008-02-06
For me, this ended up being something to do with the "wonderful" ati driver support.  I noticed thunderbird had the same problem.  When I switched to the vesa driver, firefox would come up ok.  

I got it kind of working with the ati driver following quite a few quite a few guides, including:
[http://ubuntuforums.org/showthread.php?t=580748](http://ubuntuforums.org/showthread.php?t=580748)
and 
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

The display still isn't working correctly, but this specific firefox issue is no longer a problem.  Thanks

---

