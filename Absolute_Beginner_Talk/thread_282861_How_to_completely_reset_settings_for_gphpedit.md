---
title: "How to completely reset settings for gphpedit?"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by UnknownVariable on 2006-10-23
I installed gPHPedit from synaptic and I'm pleased with it as a PHP editing tool, however, I goofed up in the preferences and now all of the fonts are extremely small and unreadable. Tedious as it was, I went through each type of code and reset the size back to a normal size, yet the fonts still showed too small, after I applied, ok'd, and reopened the program. I figured I could get away with a clean install of it and be cool. sudo apt-get remove gphpedit; sudo apt-get install gphpedit did nothing for me, no settings were reversed. So I figured there's got to be some kind of file containing settings for the program. I did a locate gphpedit in the terminal and sudo rm -r'd all that was there as they weren't anything too important. That was followed by another uninstall and reinstall of the program. However, it's still goofed up with the fonts! Something has to be keeping settings for it somewhere. Anybody have any guesses where, or any insight on how I can reset the defaults in this program? :) Thanks.

---

### Post by Arby on 2006-10-23
Individual user settings for any program are stored in the 'dot' files in your home directory. If you run 'ls -la' in a terminal you will see lots of files with names like .mozilla for example. Look for a one called .gPHPedit. If it's a gnome application it might be buried in the depths of .gnome somewhere.

There's probably something stored in that folder that's causing your problem. When you find the right .folder remove it. Then do your reinstall. That should create a new .gPHPedit with default settings in it

---

### Post by UnknownVariable on 2006-10-23
Yep, I did that already. :)

When I used locate gphpedit, that's one of the folders that came up. I used sudo rm -r to recursively get rid of everything in it. The settings were still saved though...

One thing, after I deleted everything I found with locate gphpedit, and went to reinstall it, the terminal said "selecting previously unpacked gphpedit" or something similar to that. That was AFTER I'd deleted everything from locate gphpedit, as well as the .deb file in the archive folder on my system. Nothing that I know of that was involved with gphpedit still remained on my system, yet it still goofs up. :S  Strange.

---

### Post by Arby on 2006-10-23
that is odd behaviour. As far as I know settings files reside in one of two places. Individual user settings in /home/user and global config/settings in /etc. If you've removed the relevent entries from those places I'd have bet on that fixing your problem.

You said you got rid of the .deb file already. I suppose you could try clearing your apt archive just to be sure.```
sudo apt-get clean
```In case you don't know, this clears all the lefotver .deb files from /var/cache/apt/archives. You can set Synaptic to do this automatically if you haven't already. ```
Settings -> preferences->files
``` Probably won't make any difference but it's not a bad idea anyway.

The only other thing I can think of is; does gPHPedit have dependencies? Could there be something in their settings files that is causing your problem?

Best I can offer sorry

---

### Post by PartickThistle on 2007-03-07
```
rm  ~/.gnome2/gPHPEdit
```

:)

---

