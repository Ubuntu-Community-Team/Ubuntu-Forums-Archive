---
title: "Music Management software?  Plus, can rhythym box edit id3 tags?"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by AlexLinuxUser101 on 2008-02-15
the main problem for me with ubuntu is lack of good music management software... :(

Amarok and banshee's organizing menus (by artist/song/album/etc.) take 5-10 seconds everytime to reupdate everytime I click one of them.  That is one of my most used feature on any music management software so those are out.

I got itunes to work on wine, but it is rather sluggish.  itunes is my ideal program and what I used to use, but the sluggishness is a pain in the ***.

Anyways, despite the lack of features in rhythymbox, it's the best thing I got going right now.  The speed is probably the most important... but is there a way to edit id3 tags?  I can view them, but I recently found out when trying to change it that it won't let me.  Any tips or suggestions for other music management software?  I wish they made itunes for linux... I would probably actually pay for that.

Oh and also, rhythymbox doesn't show my album artwork already embedded in the song file.  Wtf is with that?  instead it downloads it off the net quickly... this is fine... but for the majority of my albums it can't find anything.  Is there anyway it can just show what I already have?

---

### Post by emarkd on 2008-02-15
I use EasyTag for tag editing.  It's in Synaptic.  Don't know about your rhythmbox questions, though...

---

### Post by AlexLinuxUser101 on 2008-02-16
that can't tag aac files, unfortunately :( Anyone else have any suggestions?  I think the lack of really great music management software is a major downfall of ubuntu, other than that I love it.

---

### Post by newagelink on 2008-03-02
[COLOR="Indigo"]I found this thread through searching something like "rhythmbox editing tags"; I'm hoping to have the same questions answered.[/COLOR] :/

---

### Post by ubuntu-freak on 2008-03-02
EasyTag-AAC will be in Hardy. You could try adding the Hardy repos and install it from there. DO NOT perform a system update whilst you have the Hardy repos. Quickest way to get it done is to;
 
**sudo gedit /etc/apt/sources.list**
 
and replace "gutsy" with "hardy" on each line. Save and then; 
 
**sudo apt-get update && sudo apt-get install easytag-aac**  
 
Change it back when you're done installing EasyTag-AAC, or you will end up with an alpha OS.
 
Nathan

---

### Post by newagelink on 2008-03-04
[COLOR="Indigo"]Isn't that installing something before it was meant to be released? Like, beta testing it? Can't that screw up your computer?[/COLOR]

Edit: easytag is available in the Synaptic Package Manager for me (in Ubuntu 7.10.) I'll try installing that, then! From the description: > viewing, editing and writing ID3 tags
EasyTAG is an utility for viewing, editing and writing
the ID3 tags of different audio files, using a GTK+ interface.

Currently EasyTAG supports the following:
 - View, edit, write tags of MP3, MP2 files (ID3 tag), FLAC files (FLAC Vorbis ...
Edit: [COLOR="Navy"]I didn't realize EasyTag was a separate program. Isn't there a way to edit flac files directly using Rhythmbox?[/COLOR]

---

### Post by click4851 on 2008-03-04
No, You currently can't edit FLAC file ID3 tags in Rhythmbox....I was wishing for the same thing....

---

### Post by Ardrias on 2008-03-04
I'd use (and do) foobar2k through Wine. There simply isnt anything native that does the job.

---

### Post by billgoldberg on 2008-03-04
For music managment (and movie managment) I use GCstar (in the repo's).

Try it out.

---

