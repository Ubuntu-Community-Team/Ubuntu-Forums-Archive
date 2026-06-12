---
title: "Transferring mp3s from windows to ubuntu"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by swimm3r137@gmail.com on 2008-04-13
I have about 40gigs of mp3s in itunes which I want to save when converting over from windows to ubuntu.  I'm going to put all them on an external hard drive, then while running the *alternate* version of installation, I'm going to delete everything on the windows partion (mainly because I don't want or need any of it).  After it's completely deleted I was wondering what the best way to transfer these 7000 mp3s back onto my original laptop hard drive that was just cleaned?  Also, does ubuntu come with a music player compatible to play these?

---

### Post by Lolicon on 2008-04-13
I would paste them in the new partition. Ubuntu comes with an MP3 player, but I don't like it very much, and you need to install MP3 codecs to play them.

---

### Post by swimm3r137@gmail.com on 2008-04-14
What do u mean "paste"?  Like copy and paste?????  I'm confused lol

---

### Post by Rubby on 2008-04-14
If the mp3's are on an external hard drive; Yeah, it really is that simple(copy and paste)

---

### Post by Tatty on 2008-04-14
To play proprietry formats like .mp3 you will need to install the ubuntu-restricted-extras, have a read of this wiki page:

[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by cm.squared on 2008-04-14
Before you go wiping your harddrive, you might want to double check what file format your music files are in, especially if they've come from a range of sources.  If you have bought music from the itunes store it will be in a copy protected .m4p format that you won't be able to play once you get into ubuntu (or on any other computer).  So you might wait before destroying the windows partition and itunes that has the key to unlock copy protected music.  It would really be a shame if you had 40 gigs of music that you couldn't listen to.

To get around the copy protection is a somewhat arduous process, with the easiest way probably being to burn audio cds of each album that you have and then reimporting with a music player in ubuntu.  A pain, yes, but better than nothing.  (if you do have all mp3 files this doesn't apply and you're fine, but it would be well worth checking)

You also might consider resizing the windows partition and dual booting ubuntu, especially if you've never used linux before.  That way you'll be able to ease into using a new operating system since the learning curve can be steep.  It will also let you burn your library piecewise instead of all at once (bleh).

Regarding music players, the default is called Rhythmbox.  Other ones that people use are Amarok and Banshee.  These can be installed with the "Add/Remove..." programs utility under the application menu.  None is an exact clone of itunes, but they're all serviceable.  Try them out and see what you like.

---

### Post by cm.squared on 2008-04-14
I had another thought.  If you choose to dual boot with windows and ubuntu it shouldn't be too hard to access your windows partition from within ubuntu, and copy the files into your ubuntu partition.  Then again, copying the files to the external harddrive and back into ubuntu will work just as well.

Also, if you're new to ubuntu you may want to use the default installation disk instead of the alternate, since it has a graphical interface and is probably easier to negotiate.  Unless you have some unusual circumstances with your computer you don't really need the alternate installer.

---

### Post by swimm3r137@gmail.com on 2008-04-26
I have another question.  Before I installed ubuntu over windows, I put all 40gb of my mp3 file music on an external hard drive.  Then I overwrote windows with ubuntu.  How would I transfer all these mp3's to ubuntu?  I know in windows I would just make a folder or just put them all in the "my music" folder.  How would I put all these files, and whats the right place to put them so music players will play them without any files?

---

### Post by natrixgli on 2008-04-26
If you don't plan on removing the external drive you can leave them there, and in Rhythmbox Music Player go to File > Import Folder and select the folder that contains your mp3's. 

You will see 'Import Errors' for any files that can't be played, which will include ALL .mp3's if you haven't installed the ubuntu-restricted-extras package.

-n8

---

### Post by swimm3r137@gmail.com on 2008-04-26
> **natrixgli said:**
> If you don't plan on removing the external drive you can leave them there, and in Rhythmbox Music Player go to File > Import Folder and select the folder that contains your mp3's. 

You will see 'Import Errors' for any files that can't be played, which will include ALL .mp3's if you haven't installed the ubuntu-restricted-extras package.

-n8

I dont understand.  I just downloaded the ubuntu restricted extras package, but when I do something so simple just like inserting a cd (intending to play songs off of it), and open the folder, their all in Wav format.... Why?  Also, when I click on any of those songs in the folder, such as "track 1.wmv", it opens up ruthmbox, and says "an error occured.  Stream contains no data"  ?????????  I guess, if wav format is a problem, is there a way to fix this so wav files are compatible in rythombox?

---

### Post by Liakath on 2008-04-26
> **swimm3r137@gmail.com said:**
> I have about 40gigs of mp3s in itunes which I want to save when converting over from windows to ubuntu.  I'm going to put all them on an external hard drive, then while running the *alternate* version of installation, I'm going to delete everything on the windows partion (mainly because I don't want or need any of it).  After it's completely deleted I was wondering what the best way to transfer these 7000 mp3s back onto my original laptop hard drive that was just cleaned?  Also, does ubuntu come with a music player compatible to play these?

You are going to invite a lot of SPAM in your inbox!!

You can easily access & play the music in your external drive with AMAROK.

---

