---
title: "[SOLVED] Rename File on M4A/WMA Tags"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by imaginal on 2008-01-25
I have a solid 12000 tracks that I would like to rename based on tag information, but they are mixed format mp3/m4a/wma... 

mp3 tag is ok for mp3, but enabling m4a support has me caught in compile/dependency hell. I have no idea what do do with the wmas...

Are there any programs out there that take care of *all* of these? I've resisted running to wine until now, but I miss my xp tagging software. :( Suggestions?

---

### Post by rhc on 2008-01-25
1)MusicBrainz Picard.
Try it.

You can just click "look up" inside the program and it finds the album from a large database.

Also you can enter this site
[http://musicbrainz.org/search.html](http://musicbrainz.org/search.html)
and write the album yourself and then click "tagger" from browser,it sends the album to the program.

2)Second one Cowbell.

3)And i use MusicBrainz and the audio player "Listen" together.
Listen also has a very good tagging player inside.

---

### Post by emarkd on 2008-01-25
Don't think it'll support the wma stuff, but [EasyTag]("http://easytag.sourceforge.net/") is a nice tagger for linux.

---

### Post by rhc on 2008-01-25
I think these are sufficient.
Try these and if you don't like,i'll say more.

---

### Post by imaginal on 2008-01-25
Thank you for your quick replies!!!

Easytag doesn't have WMA support, and m4a support is, well, not supported. This is the program I'm looking for though.

Picard does all of the file types, but all of my files already have the tags I want them to have. (There are no missing tags) I fight with picard. Sometimes it splits my complete albums into 2 incomplete albums. Besides, it takes far to long.

I just want to rename the files in batch, using simple /home/$user$/$artist$/$album$/ etc... the tags are correct, but picard won't just blindly rename. Any ideas? I need a combination of EasyTag with the filetype support of Picard.

---

### Post by rhc on 2008-01-25
imaginal,
2nd program i said,Cowbell.
Install it,and go to preferences,
there is an option there,rename files according to song information.
Is it what you want?
If it s not,i ll suggest another one.

[http://more-cowbell.org/index.php/Main_Page](http://more-cowbell.org/index.php/Main_Page)

---

### Post by imaginal on 2008-01-25
Thank you again, and sorry for not mentioning cowbell in my trial/error process.

It does not show any of my m4as or wmas. It also doesn't allow for recursive directory importing. I would have to add each file manually. Also, I want to be able to rename/move the files, using wildcards, to directories. There are only 4 options in cowbell. I want to enter in my own naming method, like in EasyTag or Picard.

---

### Post by rhc on 2008-01-25
Which audio player you re using?

---

### Post by imaginal on 2008-01-25
I'm using exaile 0.2.11, and I'm rather content with it. It plays all of the files, and only keeps me from editing wma tags. That asside, my tags are already correct... but the transfer from operating system a to b left my file management in rambles.

---

### Post by rhc on 2008-01-25
If you are not using Amarok like me,
the one you are looking for is "Listen" audio player.
IT2s really great for both tagging and library options.

And if you don't want to change your player,
the program you are looking for Ex-Falso.
Try it from add-remove programs.
I exactly know that it has a "m4a" support.

---

### Post by rhc on 2008-01-25
> **imaginal said:**
> I'm using exaile 0.2.11, and I'm rather content with it. It plays all of the files, and only keeps me from editing wma tags. That asside, my tags are already correct... but the transfer from operating system a to b left my file management in rambles.

You can play all of your files with Listen too,and Exaile hmm..
It s good but the thing in Exaile that "queue manager" and "library" is not in the same screen or you have to click somewhere is bad  i think.
If you are staying with Exaile,then try Ex-Falso,if you don't like,
i ll suggest another one :)

---

### Post by rhc on 2008-01-25
It's like there s 4 option in "rename files" section but not.
Click there write your file name,then preview.
Then save. (For Ex-Falso)

---

### Post by imaginal on 2008-01-25
Thank you again rhc for all of your advice.

However, I am content with Exaile and it's tagging. I am not a fan of listen in the least, and don't care for some issues I've stumbled on in Amarok. It is a matter of preference.

Ex Falso and Quod Libet don't do everything I wish they could either. They are too restrictive, and I'm rather anal when it comes to my music collection.

Understanding that there probably isn't a piece of software that will work for all 3 audio types, I bit the bullet and installed Mp3tag under wine. I would rather stay loyal to open source, but I just don't think the software exists. (likely because of proprietary hurdles linked to my specific codecs) 

Thank you again for your patiences. I'll continue to badger the coders of [mp3tag]("http://www.mp3tag.de/") to release a linux version.

---

### Post by hugmenot on 2008-01-26
But QL/ExFalso will definitely cleanly rename all your audio files. Even if you prefer another player.
Try it out.

---

### Post by dawesc on 2008-02-16
Another idea i've just used is the following bash script (so use gedit or similar to create a file as follows):

#!/bin/bash
for file in *.mp4; do
  val=$(AtomicParsley "$file" -t | grep "Atom \"©nam\" contains:")
  mv "$file" "${val:22}.mp4"
done

Save it to /usr/bin/renameMP4 

Now download AtomicParsely from 

[http://sourceforge.net/projects/atomicparsley/](http://sourceforge.net/projects/atomicparsley/)

if you're using Ubuntu then download the "Debian" version and save to disk. You just need the file "AtomicParsley" from the zip file, save it to /usr/bin/AtomicParsley

Now ensure permissions are correctly set:

sudo chmod 755 /usr/bin/AtomicParsley
sudo chmod 755 /usr/bin/renameMP4

Now go to the directory containing the files you wish to rename and run the command:

renameMP4

---

