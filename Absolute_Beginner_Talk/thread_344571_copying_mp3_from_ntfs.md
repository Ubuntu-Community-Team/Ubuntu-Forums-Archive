---
title: "copying mp3 from ntfs"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by birdseye on 2007-01-23
I can happily rip and play / transfer mp3 files in ubuntu and also in windows. but I cant get the linux mp3 players to play the mp3 files I still have in my windows partition and I cant get them to play any files which I copy into linux from my windows partition. Odd really since the files I've copied over are clearly there.

When I copy the mp3 files from XP to Ubuntu they arrive but the player (either Rhythmbox or another whose name escapes me) will not play them. But both players will play MP3's that I have ripped directly into linux.

When I try to get the players to recognise the MP3 files in the NTFS partition, they see the file names but the files appear to be empty ie zero kb.

what could be causing this - I dont want to have to rip my cd's all over again if I can avoid it.?

---

### Post by deadgobby on 2007-01-23
Did the Mp3's have a new file name after taking from the XP part to Ubie? Like band.mp3.1 or band.mp3OK. If so you need to rename the file. From band.mp3OK to band.mp3
Gobby

---

### Post by Canis familiaris on 2007-01-23
For accessing files in an NTFS partition. Use ntfs-3g. Please follow the kink below for more information:
[http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g]("http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3gtp://")

I may be possible that the MP3 codecs for Ubuntu are not installed. Install them using Easy Ubuntu or Automatix.
Automatix will be able to run all MP3, MPEG, and DVDs very well.
For info on installing Automatix, follow the link below:
I strongly recommend you use Amarok as your Music player.
[http://ubuntuforums.org/showpost.php?p=1953858&postcount=2]("http://ubuntuforums.org/showpost.php?p=1953858&postcount=2")

After installing Automatix, open Automatix and install your codecs in a straightforward manner.

You should now be able to play MP3s

---

### Post by renzokuken on 2007-01-23
Also, you dont have some sort of encryption active on your ripping software in windows do you?

Some of the first mp3 i ever ripped on windows using Windows Media Player i forgot to turn off the license thing that only lets you play them on that computer, and so i can not play those files on my ubuntu install.

---

### Post by daemonoid on 2007-01-23
The problem here doesn't sound as though it's with the file system, but the files themselves.

What are you using to rip the windows files? if you're using windows media player then with the wrong settings you can end up DRMing your own tunes! Try ripping with iTunes or audiograbber and see if you have the same problem.

---

### Post by DerHesse on 2007-01-23
What are the rights for the copied files. Who is owner, what are the permissions?

---

### Post by birdseye on 2007-01-23
Answering as many questions as I can:

the owner is me, permissions are read only for me (I've yet to ge the hang of changing permissions on a file)

the XP ripping software is either dBmonkey or media monkey and neither are encrypting. the files (some mp3 others wma) play ok on my mp3 player

the files I copied over from XP have the normal .mp3 or .wma extension but here's a funny I had not noticed. In file tree, the directory says "empty" but the files are all there in the right hand window and shoing 4mb or whatever.

trying to play with rhythmbox brings up an error message - this file is not an audio stream. the other application I've tried juK shows the files as having 0 size.

neither application will play direct from the windows partition.

---

### Post by birdseye on 2007-01-23
moved up a bit ):P

---

