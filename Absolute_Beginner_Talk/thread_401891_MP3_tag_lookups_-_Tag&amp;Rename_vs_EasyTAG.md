---
title: "MP3 tag lookups - Tag&amp;Rename vs EasyTAG"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by qprfact on 2007-04-05
I've been using EasyTAG, and it's a really nice app, but the problem I have is getting tags from freedb when the files aren't in the right order (and of course, I don't know the right order necessarily!)

On Windows, I used an app called Tag&Rename. I tried installing the trial version in Ubuntu under WINE, but the lookups it uses (to Amazon) didn't seem to work. Any idea why that could be, or is there a way of getting EasyTAG to do what I want?

Thanks!

---

### Post by userundefine on 2007-04-07
Alternatively you could try [MusicBrainz Picard]("http://ubuntuforums.org/showthread.php?t=174560") (disclaimer: I have not tried it).  In Windows I know I used to use it because it was the quickest way to get mp3s tagged and identified.  Instead of assuming all the files are in proper cd-order like a freedb service requires, it analyzes length filesize and other metadata based on the thousands of others submitted to the service and then tags it.  Now, that's how it worked in Windows, two years ago when I used it, but I assume it's the same under Linux.

You can't get easytag to work with amazon, it's not part of the program (at this point).

And another option is using Amarok, which has Musicbrainz db access built-in.  I actually hadn't realized this until just searching around for Musicbrainz, but it sure is convenient !

---

### Post by qprfact on 2007-04-10
I installed MusicBrainz Picard and it looks pretty good.

One minor thing - is there a way of making it embedding the cover art into the file tag?

---

### Post by qprfact on 2007-04-10
To do the searches, do I need to forward ports or anything like that? I'm wondering if that's why Tag&Rename isn't working under WINE.

---

### Post by aparigraha on 2008-04-13
Well it used to work until just now. I've been using it for over a year... but it recently just stopped working. I figure it has to do with Wine. Even old versions worked PERFECTLY in the beginning of this year. I'm gonna try the new version of wine now....

---

### Post by aparigraha on 2008-04-13
No didn't get it to work with the new version of wine either. Tried many versions of Tag&Rename.

Found KID3 for Linux instead which is fairly useful and imports data from TrackType.org, gnudb.org, MusicBrainz and Discogs

---

