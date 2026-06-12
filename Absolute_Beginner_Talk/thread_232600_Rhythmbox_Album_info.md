---
title: "Rhythmbox Album info"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by jms392 on 2006-08-08
I have just installed Ubuntu Dapper, and am in the process of ripping my CD's to harddisk using SoundJuicer.  However, when the tracks are added to the library in Rhythmbox, the track title is listed correctly, but the artist name, album title, etc, are all listed as "unknown".  This is really annoying  because it stops me from searching by artist or album name.  Any help would be greatly appreciated.

---

### Post by hopstah on 2006-08-09
is soundjuicer correctly downloading the album data from freedb?  are you sure that that info is even in the file?  Rhythmbox may actually only be listing the file name, and not even the track tag info.

---

### Post by jms392 on 2006-08-09
Soundjuicer seems to be getting the tags ok because all of the info shows if I use Banshee, which is fine, but at this stage I prefer Rhythmbox.  I also noticed that when I had the CD inserted, and opened up Rhythmbox, it didn't get any info at all, no track titles or anything.  I didn't get the track info until I started Soundjuicer

---

### Post by jms392 on 2006-08-10
I've looked at this a little further now, it seems neither Soundjuicer or Rhythmbox are reading the tags, however Banshee does.  Rhythmbox did read the tags on one CD-R that I had, but none of my CD's that I have actually purchased.  Could this be due to tag version incompatibility with Rhythmbox?  If so, how can I fix this?  I would be interested to know whether other people have had this problem.

---

### Post by doclivingston on 2006-08-11
> **jms392 said:**
> I've looked at this a little further now, it seems neither Soundjuicer or Rhythmbox are reading the tags, however Banshee does.  Rhythmbox did read the tags on one CD-R that I had, but none of my CD's that I have actually purchased.  Could this be due to tag version incompatibility with Rhythmbox?  If so, how can I fix this?  I would be interested to know whether other people have had this problem.

If S-J isn't "reading the tags" on an audio cd, that means the lookup on musicbrainz must be failing (Rhythmbox uses identical code for this). It's possible Banshee is doing something different which makes it work; I've heard of that happening, and the reverse (S-J working and banshee not) before.

---

### Post by jms392 on 2006-08-11
Thanks, that makes sense.  Any ideas about how to fix it?  Are there any packages that should be installed in order to communicate with Musicbrainz? Maybe I am missing something that SoundJuicer and Rhythmbox need?

---

