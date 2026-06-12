---
title: "Changing default mouse actions on specific files"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by rvmcconnell on 2008-03-19
Every time I double click on a flac or mp3 file, totem pops up to play it. I want to change that response to enqueue in rhythmbox. Selecting "Open with another application" and selecting rhythmbox or putting in a custom do not have any effect. If there are instructions somewhere on how to do this, they are very well hidden. I have also searched these forums with no success. I could not find any way to search the mailing list archives.

This is a brand new install of 7.10 with all updates. I have removed all traces of mono (yes, it is a disease) and a few other unwanted packages. This will be replacing my wife's MS-Windows machine which is collapsing under its own weight for the third time.

---

### Post by FreewareFan on 2008-03-19
Here's what you need to do.  Right click on the file type, and choose Properties.  When that text box pops up, click on the little square with the wrench on it, on the Type line, over on the right.  

Now, down in the Application Preference order box, look for the application you want to use, and move it to the top.  If it's not there, then click the Add button, and create an entry for it.

Save everything, and from now on, when you double click that filetype, it will use the application of your choice..

---

### Post by FreewareFan on 2008-03-19
UPDATE:  I forgot, not everyone uses Krusader like I do...  If you use the default file system file browser, Nautilus, then do this:

Right click on the file, choose Properties, and when that pops up, choose the Open With tab.  Choose the program you want from the list.  If it's not there, add it.

Hope this helps you out.l

---

### Post by rvmcconnell on 2008-03-19
As I said in the original message, this doesn't have any affect. Even after I chose an alternate program, the file still gets opened in totem.

---

### Post by FreewareFan on 2008-03-19
I understood you to mean you had tried using the pop-up context menu to select the program.

Well, try to go to System - Preferences - Prefered Programs, and changing the program for Multimedia.

---

### Post by rvmcconnell on 2008-03-19
Ok, now it plays in rhythmbox, but it supplants the files already queued in the playlist. How do I make it append to the end of the queue?

Another issue is apparent from this method. How do I now set the default for video files to the movie player? "Multimedia" is too broad a selection for this. I need separate settings for audio and video.

This is what makes GUI so frustrating. Every one is designed to someone else's idea of how it should work. None of them can be configured so they work the way I need them to. Every one I have ever worked with has been as useful as a 55 MPH governor in a Porsche on the Autobahn.

---

### Post by rvmcconnell on 2008-03-19
Well, I spoke too soon. It played two songs with Rhythmbox. Now, even thought it says "Rhythmbox music player" it still calls totem. Right click on a file, and the default still shows "Movie player".

---

### Post by FreewareFan on 2008-03-19
I have no idea what's going on with your setup.  I've tried all I know to do... Perhaps someone with more knowledge will come along.

Hope you get it figured out!

FwF

---

### Post by rvmcconnell on 2008-03-20
It looks like the secret sits in /etc/gnome/defaults.list and /etc/gnome-vfs-mime-magic. There may be a few other pieces to the puzzle scattered around. Now I just need the instructions on how to edit those file so that it won't get replaced on the next update. I also need to know where the per-user variations reside.

I wonder if I can find the same sort of files in XFCE. That would help fix up some of the problems on my two Slackware workstations.

---

### Post by rvmcconnell on 2008-03-21
More pieces. In /usr/share/applications/mimeinfo.cache, most of the lines did not end in a semi-colon. After fixing that, flac files now open in rhythmbox, but won't enqueue. Now I need to find where to change the command line to enable the enqueue option.

I am curious about the defects in the cache file. Since I removed mono, and all associated applications, I wonder if that removal has been sabotaged so that it messes up the desktop. Has anyone else experienced this problem?

---

