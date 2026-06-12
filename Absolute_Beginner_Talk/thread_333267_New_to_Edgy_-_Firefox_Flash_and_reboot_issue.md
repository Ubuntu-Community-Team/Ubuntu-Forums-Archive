---
title: "New to Edgy - Firefox Flash and reboot issue"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by lodravah on 2007-01-07
So, I just installed Edgy, and it seems to be running fine. I have almost everything in place. However, I'm having problems with flash in Firefox. I ran the install non-free flashplugin, and got the answer that it is already the newest version. But firefox doesn't find the flash (in youtube, for instance) and the flash does not show up on about:plugin. Tried "locate libflashplayer.so" but it does not exist. Would also like to be using flash9 since I'm now using Firefox and not Opera9 as I used to, seeing as flash9 didn't work that nicely with opera. 

The second issue is that when I want to restart, it hangs on the "ubuntu" - screen after finishing booting down. 

Any ideas?

---

### Post by ajgreeny on 2007-01-07
Try what I did.
Download the flashplayer plugin zip file from adobe direct, unzip it and then copy the libflashplayer.so file into all the various mozilla firefox plugin directories you find in your file system.  You will need to do most of the copying as root, but it isn't difficult, and the plugin works brilliantly.

Can't help with the other problem, I'm afraid.

---

### Post by lodravah on 2007-01-07
Okay, thanks. Figured out the reboot problem, though. Just had to press and hold the startbutton for a few seconds, then it shut down.

---

### Post by lodravah on 2007-01-07
I have downloaded flash9, but I can't find the "libflashplayer.so" (flash7) currently used by firefox.. It is not where I found it in Dapper. At least I don't think so. This is my first time in Edgy, so I don't know if it is somewhere else. Tried searching after "libflashplayer.so" but file wasn't found.

---

### Post by ajgreeny on 2007-01-07
> **lodravah said:**
> I have downloaded flash9, but I can't find the "libflashplayer.so" (flash7) currently used by firefox.. It is not where I found it in Dapper. At least I don't think so. This is my first time in Edgy, so I don't know if it is somewhere else. Tried searching after "libflashplayer.so" but file wasn't found.

Were you just looking in your home folder instead of the full file system?  If you have flash 7 installed it should be there somewhere.  Have another look at about:plugins in firefox to see if you can find it, and if needed reinstall it.

On my system I have edgy installed as well as dapper.  On edgy the flash plugin is in the following folders:-

/opt/flash32/libflashplayer.so
/usr/lib/firefox/plugins/libflashplayer.so
/usr/lib/mozilla/libflashplayer.so
/home/andrew/Downloads/flash-player-plugin-9.0.21.55/libflashplayer.so (this was from the unpacked zip file I downloaded)

I suggest you try copying the libflashplayer.so to simplar places on your system and trying out what happens.

---

