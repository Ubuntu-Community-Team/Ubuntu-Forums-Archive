---
title: "rhythmbox corrupted"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by norry on 2007-09-26
Hi there,

I am an enthousiastic Linux beginner and have some problems playing my mp3 music.  I wanted to use rhythmbox as audio player. Therefore I tried to install some mp3 codecs by reading some forum threads. This didn't work out; It even got worse. At the moment rythmbox is not able to start anymore. I tried to uninstall and reinstall the app with synaptic, but it didn't help. Rhythmbox still won't start. Could you tell me what might be wrong? What can I do to solve this problem apart from a clean reinstall of Ubuntu?

Besides this I installed the XMML player. I found out this app has got its own mp3 codecs. This works, but I can only read files on the 'File System' drive. My mp3 files are on another ntfs partition. Rhythmbox was able to read non-mp3 files on this ntfs drive. Is XMML able to reach these ntfs drives?

Help is appreciated.

---

### Post by Skerit on 2007-09-26
Oh, story time:

I remember I once thought it was a great idea to install ALL the codecs I could find in the repository. I was wrong, I installed a few wrong ones and then my audio files started *sounding* really bad when they were of decent quality.

Anyway, this doesn't mean they shouldn't be playing. Have you tried to play them in totem? If they work there, it's probably some Rhythmbox error, indeed. If they *don't* work there, you should get a notice asking you if you would like to install the right codecs.

Anyway, if you want you can delete your rhythmbox configuration files (in /home/username/.gnome2/rhythmbox) You might also want to start rhythmbox in the terminal and take a look at the last few lines of output when it fails, to see what it is, exactly, that makes it go kabloeie...

Yes, I know that's not a real word, deal with it ;)

---

### Post by norry on 2007-09-27
Thanks! I think it is indeed a rhythmbox problem. It started after installing some crappy codecs I think. The mp3 files play with xmml, so these mp3 files are allright. I would like to get this rhythmbox error fixed. I am a little ashamed to ask, but how can I start rhythmbox in the terminal? Complete noob on Linux so far...

---

