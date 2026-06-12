---
title: "Help with Music / iPod Setup"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by mannyotr on 2007-06-15
Hey all.  I recently switched to Linux / Ubuntu Feisty after reading and reading and reading from all you guys how great it is.  And I have to admit, I love it!!  I have a dual boot system with WinXP but so far (4 weeks later) I still haven't needed to load up my WinXP.  Ubuntu has been excellent!

But now I've come to the point where I need to start managing my music files.  I've been reading lots of posts about what programs to install and use, but frankly, I am a bit confused.  So I ask you to help out a newbie.

Here's what I am looking to do.  Please keep in mind that I am used to using iTunes:

I already have on my computer a folder (on a second sata HD mounted to Linux) with all my ripped MP3's.  Thousands of them.  So first thing, I need a program (like iTunes) that I could import them into and create a library / playlist type system.  A program that will allow me to rip/add more music as I get new CD's.  Again, all I can compare is iTunes.  Please know that I don't buy online music or anything like that.  So I don't need access to online music stores.  All I want is something to import/rip music to and organize it.

And also, I need a program that will allow me to upload playlists from that library to my iPod.  Actually, I have several, so I need a program that can handle several iPods (Shuffle, Nano, Mini) in the same machine.

That's it.  Any and all help will be greatly appreciated!  Thank you!!

---

### Post by zeeR on 2007-06-15
Why don't you install Banshee? It organizes music, and can manage any iPod you have.

As for the ripping, Ubuntu already has SoundJuicer: it will rip any audio cd you want to mp3, and then as you place the ripped files on your music folder, they'll be added to Banshee's library too.

You can find it in the "Sound & Video" entry, on the Applications menu.

---

### Post by tgalati4 on 2007-06-15
There are lots of players and music managers:

[http://en.wikipedia.org/wiki/Comparison_of_media_players#Audio_format_support](http://en.wikipedia.org/wiki/Comparison_of_media_players#Audio_format_support)

---

### Post by reclusivemonkey on 2007-06-15
Currently the only program I have found that supports Album Art is GTKPod. Post back though if you need this as there are a couple of things you need to install to make sure it works.

Also, you can use GPixPod to transfer photos, and with plugins Evolution will sync contacts/calendars for you.

---

### Post by timcredible on 2007-06-15
amarok, rhythmbox, and gtkpod all support the ipod.  there's probably more, i just don't know them.  the ipod is a pain because it has a database file that keeps track of everything on it (no copy-paste like other mp3 players).  as for itunes store, nope, not on linux - linux is open source and strives to make everything free and itunes store is all encrypted files.  even if apple gets its way with the recording industry and sells non-encrypted files, they're just as bad as microsoft - they won't allow their stores to be accessible by linux.

---

### Post by liquidfunk on 2007-06-15
I just use Rhythmbox, it works like a dream.

---

### Post by Mike Armstrong on 2007-11-22
iPods on ubuntu are a nightmare, or at least will keep you up for several nights!
If you use Gnome I would go for Banshee and either use Sound Juicer for rippping or Banshee. Either way you will have to get to grips with installing various packages and plugins to enable ripping to MP3. I like the look of exaile but have failed to make it transfer files to my ipod. Banshee is crap for playlists gtkpod may be better. Listen and Songbird may be an option but being fed up and at least ending up with a system using banshee and Gpixpod that works I have at present insufficient desire to enter the fray and try them. Amarok may be fine if you install KDE libs on top of gnome  but that slows down boot and seems to defeat the object. If banshee didn't have to revert your ipod daabase to an older version, was able to create and edit playlists and allowed truncation of the file list by artist or album I would not regret not using itunes!

---

