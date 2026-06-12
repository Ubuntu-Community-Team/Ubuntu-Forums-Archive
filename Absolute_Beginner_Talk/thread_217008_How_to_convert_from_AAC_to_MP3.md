---
title: "How to convert from AAC to MP3?"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by Pichu0102 on 2006-07-16
I recently switched to Ubuntu, and some of my music library is in AAC format. I want to move the ACC files out of my music folder and transcode them to MP3. Problem is, iTunes used to organize it so that the music is scattered in subdirectories in subdirectories.
Is there any way to move any m4a files out of all the subdirectories only, without moving the mp3 files?

---

### Post by bluecherry on 2006-07-16
I think this is what you are looking for:

* for a single file:
> 
ffmpeg -i input.m4a -acodec mp3 -ac 2 -ab 128 output.mp3


* and a little batch script:
> 
for i in *.m4a; do \
    ffmpeg -i "$i" -acodec mp3 -ac 2 -ab 128 "${i%m4a}mp3"; \
done


[http://linux.seindal.dk/item75.html](http://linux.seindal.dk/item75.html)

---

### Post by crispy_420 on 2006-07-16
Check this out:

[Nautilus Script for Audio Conversion]("http://doc.gwos.org/index.php/Audio-convert")

Then all you do is right click and go through some options. Simple enough right?

---

### Post by hanzomon4 on 2006-07-16
You could use the find command to move the files. Just give the path to your itunes music folder and it will search all sub-folders for the search parameters you set so it would look like this
```
find /path/ -iname "*m4p" -exec cp '{}' ~/music/ \;
```
"/path/" is the the path to your music folder. example: /home/hanzomon4/music_dir. Just so you know the "find" command will search all sub_folders that are in the folder you specify as your /path/

The "-iname" part means it will not be case-senstive.

The "*mp4" makes use of a wildcard (*) to take the place of the name of the song. This means it will find all flies that end with "mp4"

"-exec" allows you to preform a command on all files found in this case "cp" or "mv"

" '{}' " This is a place holder that represents the files found by the "find" command that the "cp" or "mv" command will process

" ~/music/ \;" This is the folder you will send the *mp4 files to. In my case it was the "music" folder. The last two characters stops the shell from expanding any special characters (brings an end to the command)

---

### Post by qyot27 on 2006-07-16
> **Pichu0102 said:**
> I recently switched to Ubuntu, and some of my music library is in AAC format. I want to move the ACC files out of my music folder and transcode them to MP3. Problem is, iTunes used to organize it so that the music is scattered in subdirectories in subdirectories.
Is there any way to move any m4a files out of all the subdirectories only, without moving the mp3 files?
Why transcode them?  There are plugins for most audio players (like XMMS - I dunno which repository it's in, but look for xmms-mp4-plugin or some such) to support AAC/MP4 if it's not already built-in (like it is in mplayer).  That'll save the quality from being degraded any further.  Of course, this is assuming that when you say 'm4a' you actually mean either content that was decrypted or that you ripped directly as AAC using iTunes (ignoring the fact that .m4a isn't a proper extension, of course, which is partly why I mentioned this, since I know it's common).

---

### Post by em3raldxiii on 2006-09-04
Now, what about m4b files?  xmms doesn't seem to see them as the same as m4a files.  Now, I can RENAME them all to *.m4a, but that seems a little bit counterintuitive doesn't it?  Would it be nicer to be able to tell xmms to use the same codec for m4b that it does for m4a?

---

### Post by qyot27 on 2006-09-04
> **em3raldxiii said:**
> Now, what about m4b files?  xmms doesn't seem to see them as the same as m4a files.  Now, I can RENAME them all to *.m4a, but that seems a little bit counterintuitive doesn't it?  Would it be nicer to be able to tell xmms to use the same codec for m4b that it does for m4a?
It's not really XMMS' fault, it's the plugin.  Keeping in mind I know nothing about writing programming code, I would think that all that would be needed is to add the .m4b extension into the plugin's recognition code.  The difficulty with .m4b files, from what I've heard, is that only that extension will let the players know that the thing has chapter support enabled; renaming it to .m4a or .mp4 may get it to play, but the chapters won't be recognized.  Again, that's something that would need to be added to the plugin, and I have no clue how much that particular plugin gets updated.

---

