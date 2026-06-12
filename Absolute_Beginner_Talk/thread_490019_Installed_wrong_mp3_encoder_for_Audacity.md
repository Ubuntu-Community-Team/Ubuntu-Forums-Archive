---
title: "Installed wrong mp3 encoder for Audacity"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by ynottony on 2007-07-02
After installing lame in Audacity to export as mp3, it seems I selected the wrong encoder for installation.  

i mistakenly selected the libmp3lame.so.0.0.0  rather than libmp3lame.so.0  and installed it.  

Now when I record and attempt to play-back I receive this error message: "Error while opening sound device.  Please check the output device settings and the project sample rate."

I'm a newbie with Linux.  ;)

I attempted a search for the libmp3lame.so.0.0.0 file in the Home Folder (File System) hoping I could find the file and delete it, but was unsuccessful in locating it.  Would really appreciate any help on getting Audacity to play-back again.  Thanks.  - Tony Brigmon

---

### Post by nanotube on 2007-07-02
well, i don't think that that's the reason, because the .0 is simply a link to .0.0.0. but, they are both located in /usr/lib, in case you want to fiddle with it.

this is what i have on my feisty install:
```
nanotube@groovy4:~$ locate libmp3lame
/usr/lib/libmp3lame.so.0.0.0
/usr/lib/libmp3lame.so.0
nanotube@groovy4:~$ ll /usr/lib/libmp3lame.so.0
lrwxrwxrwx 1 root root 19 2007-05-21 11:22 /usr/lib/libmp3lame.so.0 -> libmp3lame.so.0.0.0


```

---

### Post by jonlemur on 2007-07-16
I think you would probably have to go to Edit -> Preferences and select "Find Library" under the mp3 section.

Here is something I wrote in another post that might help you through the rest:

I just downloaded and installed Audacity today, and got exporting to mp3 via LAME to work. First, you don't have to show hidden files, but (except for the extra files you'll have to look through) it couldn't hurt. Second, I had to change the box that says "Only libmp3lame.so" to "Extended Libraries (*.so*)." Note that the "lib" files don't exactly go in alphabetical order as it makes a distinction between upper and lower case, so you will have to navigate past quite a few lib files. Now that I think about it though, you could probably just put in the name "libmp3lame.so.0" into the text box and click "OK." (I actually just tried that, and it seems to work.) And BTW, I am in /usr/lib, but that should be default. And just to try to be thorough, I am running Gnome in Dapper Drake and have LAME, liblame0, and LAME-EXTRAS installed through Synaptic.

Hope this helps

---

