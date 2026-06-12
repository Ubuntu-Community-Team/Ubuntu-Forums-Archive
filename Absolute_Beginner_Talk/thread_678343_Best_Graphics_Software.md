---
title: "Best Graphics Software"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by Majorflam on 2008-01-25
What is the best graphics software for Linux?

I'm used to Macromedia Fireworks in Windows, and was wondering if I could find a Linux equivalent?

TIA

---

### Post by bwtranch on 2008-01-25
I would have to say, hands down, GIMP.

---

### Post by fatality_uk on 2008-01-25
For vector graphics, id use xara extreme, in the repositories and also Inkscape is there as well. Gimp is great for bitmap work, but if your used to vector stuff, the two above will be useful.

---

### Post by rosegarden78 on 2008-01-25
Other than GIMP and Inkscape you'll want video conversion like the Sorenson plugin for Flash MX.  Download **FFMPEG** from Synaptic Package Manager.  It's a command-line program so you'll have to use 'man ffmpeg' and the Internet to learn it.  But I use it for animated gifs and mpeg video conversion, frame and audio extraction.  

Otherwise you'll need to make a symlink to your Common Files in your /home/user/.wine/windows/Program\ Files directory so you can run Flash MX with Linux.  I've also tested Photoshop 6, Fireworks 4, Premiere 6 and Director 6 and they work flawlessly with WINE for Ubuntu except clone stamp and Sorenson plugin and QuickTime.

You can also try [this]("http://ubuntuforums.org/showthread.php?t=677959") and [that]("http://ubuntuforums.org/showthread.php?t=385981") if you want a nicer desktop and more program suggestions.  Once you've extracted the frames you can edit each one, change the order and recompile the frames with ffmpeg.

---

