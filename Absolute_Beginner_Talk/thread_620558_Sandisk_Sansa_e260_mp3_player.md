---
title: "Sandisk Sansa e260 mp3 player"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2007-11-22
I have this thing, and I really like it actually, but it's very microsoft friendly from what I can gather - on the box there's a stamp that has the windows vista logo and says "plays for sure" :lolflag: (really shows what people have come to expect from microsoft...) :p

Anyways, it actually works fine, but [COLOR=DarkSlateGray]**custom playlists **[COLOR=Black]is what I'm interested in doing here.  By default, it comes with 1 playlist, the "go list", and you can add and remove songs from the player.  From what I can gather, there is no way to create more playlists and if you can, no way to modify them from within the player.  In addition to this, it only seems to support the "plp" format, and if you open the existing one in gedit or kate, and make some changes and save it, it won't work because it doesn't re-save all the random crap they put in it.

Conclusion: there's_** no way**_ (as far as I know) to create more playlists, or even modify the existing one from outside the player!!!
[/COLOR][/COLOR][INDENT][COLOR=DarkSlateGray][COLOR=Black]**[COLOR=DarkOliveGreen]Any ideas?[/COLOR]**[/COLOR][/COLOR]
[/INDENT]

---

### Post by NewDisciple on 2007-11-22
(Beginner's Guide to a Sansa e200 MP3 Player) [ubuntuforums.org/showthread.php?t=312196&highlight=sansa]("ubuntuforums.org/showthread.php?t=312196&highlight=sansa")

SSS007 Having Rhythmbox/Banshee recognize Sansa player

Here is the post from the ABi forum, I give complete credit to this guy:
Quote:
Originally Posted by Cgil  
Just added support to banshee... It's quite easy:

1.Set your sansa in MSC mode.
2.Connect it to the computer.
3. In the root folder of your sansa create a text file( If you are using GNOME use the following in nautilus: right click-> Create a document-> empty file. This might work for KDE but I'm not sure...)
4.Now, name your file as .is_audio_player

Start Banshee and it should recognize it 

BTW I'm using the CVS version of Banshee
It's really that simple - make a hidden text file called ".is_audio_player" and BAM. Rhythmbox recognized it. Make SURE that you put the hidden file in Sansa's root file (the file you immediately start from, which directs you to the "MUSIC" "PHOTO" etc files)

He did mention he is running the CVS version - fear not, for I am running the version that came with Ubuntu (and Banshee was installed through the Ubuntu repo's): so I've tested it and it indeed works. Makes Rhythembox very handy all of a sudden.

This is what I have used for my playlists.  Also use easytag (in Synaptic) for tagging all MP3's.

---

### Post by ryanVickers on 2007-11-22
Hm, I'll try it!  I've had no problems connecting it and moving stuff around with just the file browser (in fact, in my opinion, thats the only way to go! ;)) :p

---

### Post by ryanVickers on 2007-11-22
I tried that m3u converting "gawk" script, and that doesn't even work! :evil:

I'll just have to accept that it's impossible. :( That's so pathetic! Aren't playlists kind of important!? and the make it so they won't work! :evil:!!!

---

### Post by motang on 2008-01-19
> **NewDisciple said:**
> (Beginner's Guide to a Sansa e200 MP3 Player) [ubuntuforums.org/showthread.php?t=312196&highlight=sansa]("ubuntuforums.org/showthread.php?t=312196&highlight=sansa")

SSS007 Having Rhythmbox/Banshee recognize Sansa player

Here is the post from the ABi forum, I give complete credit to this guy:
Quote:
Originally Posted by Cgil  
Just added support to banshee... It's quite easy:

1.Set your sansa in MSC mode.
2.Connect it to the computer.
3. In the root folder of your sansa create a text file( If you are using GNOME use the following in nautilus: right click-> Create a document-> empty file. This might work for KDE but I'm not sure...)
4.Now, name your file as .is_audio_player

Start Banshee and it should recognize it 

BTW I'm using the CVS version of Banshee
It's really that simple - make a hidden text file called ".is_audio_player" and BAM. Rhythmbox recognized it. Make SURE that you put the hidden file in Sansa's root file (the file you immediately start from, which directs you to the "MUSIC" "PHOTO" etc files)

He did mention he is running the CVS version - fear not, for I am running the version that came with Ubuntu (and Banshee was installed through the Ubuntu repo's): so I've tested it and it indeed works. Makes Rhythembox very handy all of a sudden.

This is what I have used for my playlists.  Also use easytag (in Synaptic) for tagging all MP3's.

Oh my that worked like a charm thank you very much.  Now I can finally use it via Banshee.  :)

---

### Post by stevek123 on 2008-04-24
I just tried this ... install of Banshee and add .is_audio_player thru nautilus to root of my player ... now the unit and the added microSD are not recognized at all. Before this they were but it wouldnt open/recognize the mp3s in the base unit. I'm a noob and I'm screwed....:(

---

### Post by SZF2001 on 2008-04-26
I hate to say but that howto is old and I can't bother to update it with the latest and greatest of everything the world of Ubuntu can offer of today.

I can, however, show you this link: [http://www.mazleg.com/sansa/](http://www.mazleg.com/sansa/)

Give that a try and tell me how it works.

---

