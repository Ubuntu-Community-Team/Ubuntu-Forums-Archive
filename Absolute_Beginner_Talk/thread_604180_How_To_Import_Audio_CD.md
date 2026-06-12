---
title: "How To Import Audio CD?"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by dswhite85 on 2007-11-05
How exactly do I rip an audio CD in Ubuntu 7.10? It was burned using the latest version of iTunes, but when I put the CD in, nothing shows up on the desktop, and Banshee/Rhythmbox doesn't see it. How do I get songs off a CD I burned?

---

### Post by Dr Small on 2007-11-05
In Feisty, Sound Juicer loaded when I put in an Audio cd, by default, and I could rip that way.
You could try opening sound juicer from Applications > Sound & Video and see if that works.

Dr Small

---

### Post by newlinux on 2007-11-05
I like grip. It is in the repos.

---

### Post by dswhite85 on 2007-11-06
Sound Juicer CD gives me this error when I try to open it:

"No CD-ROM drives found

Sound Juicer could not find any CD-ROM drives to read."

Any ideas? There is a CD in my drive with songs on it, it shows up on my Windows computer. And I know my CD Drive works, because I put in the Ubuntu 7.10 CD and that shows up, so I'm not sure what to do.

Ok, scratch that, when I put my Ubuntu 7.10 CD in, nothing happens at all! Did I somehow disable my CDROM drive???

---

### Post by bgast1 on 2007-11-06
I'd like to know the same thing. Also how do you get album covers to show up in Amarok. Can you use Amarok to rip CD's and I haven't learned much about file systems yet, is it pretty self explanatory as to what folder you would put the CD you ripped into. In Windows I always just made a folder called 'My Music' on which ever hard drive I was going to use. I think I will store the Cd's on the same drive that I have Ubuntu installed to.

---

### Post by dfreer on 2007-11-06
> **bgast1 said:**
> I'd like to know the same thing. Also how do you get album covers to show up in Amarok. Can you use Amarok to rip CD's and I haven't learned much about file systems yet, is it pretty self explanatory as to what folder you would put the CD you ripped into. In Windows I always just made a folder called 'My Music' on which ever hard drive I was going to use. I think I will store the Cd's on the same drive that I have Ubuntu installed to.

Amarok has a great feature called "Cover Manager". Basically, it shows you all of your cover art for songs in your collection, and you can tell it to fetch cover art (from amazon.com I believe) for any albums that may be missing it's cover art. The only bad thing about it is that it doesn't let you copy the image directly like iTunes does, if you are like me and like to back it up to your music folder.

Now for me, I find it's a lot easier in the long run if you use easytag to properly set your ID3 tags, and include the album art within the mp3's themselves. That way, iTunes and Amarok can simply pull it off the mp3 itself.

Amarok does not have a CD ripping utility by default, although I think there is a plugin/script for it online somewhere (haven't used it myself). With Gutsy, I just use Sound Juicer to rip my audio CD's, works great for me. You can create a music folder anywhere really, although it's probably better if you place it on your desktop or home directory. Once you tell sound juicer where you want it to save your files, and change your collection in amarok to include that folder and watch it for changes recursively, it becomes as simple as this:
Insert Audio CD and Sound Juicer will open
Tell it to rip the CD
Open Amarok and start playing (amarok should have the new music in your library already!)

---

### Post by bgast1 on 2007-11-06
Probably should have checked first but does sound juicer rip files in flac? I prefer lossless with my CD collection.

---

### Post by dfreer on 2007-11-06
> **bgast1 said:**
> Probably should have checked first but does sound juicer rip files in flac? I prefer lossless with my CD collection.

Yep. Not sure if you have to install any extra codecs, but it has a profile for it in it's ripping preferences.

---

### Post by tubasoldier on 2007-11-06
> **newlinux said:**
> I like grip. It is in the repos.

Grip is awesome! extremely configurable so you can tell it to go right into your Music directory.

---

