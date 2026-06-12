---
title: "Firefox and the disappearing Filetype Actions"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by OriginalGrumpyOldMan on 2007-03-15
Related to my other [post]("http://ubuntuforums.org/showthread.php?p=2303237#post2303237"), I ran into the following issue: I mistakenly set my file association/ action for playlists (.pls) (in Firefox) to use Rythmbox Player, which turns out not to play them back.

So I wanted to change it. Going to Edit/ Preferences/ Content/ Filetypes/ Manage, I expected to find an entry for .pls files (and plenty of others, like tiff, png, mp3 etc., as in Windows and OSX)

Instead there was only a single entry: SPL, opening with Flash, the most recent plug-in I installed. Where have all the other file actions gone?? They are obviously in effect, since clicking on pls files still opens Rythmbox...

- Is there a way to get them back, listed in the manager again?
- Is there an alternate way to get to them and edit them manually?

---

### Post by OriginalGrumpyOldMan on 2007-03-17
In case someone else runs into the same problem:

This [page]("http://kb.mozillazine.org/Opening_files_using_plugins") offered a starting point, but not the actual solution.

Here's the best I could do to fix my problem:
- Type "about:config" in the location bar
- Scroll down and find "browser.download.hide_plugins_without_extensions"
- Switch it over to "false" i.e. do NOT hide those plugins

Going back to Preferences/Content/File Types/Manage, I could now see the handler for "MP3 ShoutCast playlist", delete it and re-assign it the next time I went to ShoutCast. Of course you could just edit the entry if you are sure about the handler you want to use.

I still think there is something funny with my prefs, since there are no extensions assigned (.avi, .wmv etc.) as they are in FireFox Windows & Mac OSX... Oh well, too many other problems with Ubuntu to dwell on this one.

---

### Post by srt4play on 2007-04-10
Thanks a lot for this information!  I was looking for a way to get firefox to hand off .m3u files from my gnump3d server to xmms instead of the mplayer plugin, and your information was my solution! 

Thank you!

---

### Post by shoq on 2007-05-05
Argghhhh

Would some please explain to me why Ubuntu install cannot reset this? How would a newbie like me EVER know to diagnose such a BASIC issue like allowing plugins to show.  I've wasted hours trying to figure that out,a and finally found this post.  WHy the would they be hidden to begin with.   I just don't undertstand this world. yet. lol

---

### Post by little brad on 2007-05-11
thank you so much!

---

### Post by Sigma on 2007-05-11
Thanks for that info. :)  I was having the same problem with .torrent files (Firefox would automatically save them instead of opening them in Azureus).

I found that you could also reset your file associations by deleting the mimeTypes.rdf file in your Firefox home directory (e.g. .mozilla/firefox/e1mdff20.default/mimeTypes.rdf).  When you restart Firefox, the file is regenerated with the default file associations.

---

