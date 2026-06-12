---
title: "Automatically add file extensions"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by GStubbs43 on 2007-07-21
Hi, I have my music setup as ~/music/genre/artist/album/song and some of the songs don't have a file extension (mp3) in their filename, and they aren't detected by Amarok, Listen, Exaile, etc. Anything except for Rhythmbox.

Is there a way I can automatically add .mp3 to any files that don't already have it by starting in the music directory and automatically searching through all the subfolders?


Thanks!

---

### Post by sad_iq on 2007-07-21
Ok...found something...it's for Kde but should work in Gnome...also...no terminal needed(except to install and start the app)
 ```
sudo apt-get install krename
``` then start krename from a terminal...it will start as a wizard...so should be easy, has recursive subdirectory search...and a lot more stuff. Also you should make a directory somewere, copy some random mp3(with and without extension) and do some experimenting before you go for the real deal(I nearly trashed a music folder of mine...**experiment first**!!!!) Also...a script would make it possible to do all this...but I lack the skills :(
 Hope it works for you!!!

---

### Post by BlackMeTaL on 2007-07-21
Or you can do it with some simple commands. Go to the music folder in a terminal and execute this.

```
find . -not -name '*.mp3' -exec mv '{}' '{}.mp3' \;
```

---

### Post by sad_iq on 2007-07-21
> **BlackMeTaL said:**
> Or you can do it with some simple commands. Go to the music folder in a terminal and execute this.

```
find . -not -name '*.mp3' -exec mv '{}' '{}.mp3' \;
```

Hmm...I think it fails for me :( 
```
sadiq@omerta:~/Desktop/New Folder$ find . -not -name '*.mp3' -exec mv '{}' '{}.mp3' \;
mv: cannot move `.' to `..mp3': Device or resource busy
sadiq@omerta:~/Desktop/New Folder$

``` 
 It's a test dir...but still fails
 Also...woun't ***.mp3** find only files with mp3 extension??? And to make it recursive search???

---

### Post by GStubbs43 on 2007-07-21
> **BlackMeTaL said:**
> Or you can do it with some simple commands. Go to the music folder in a terminal and execute this.

```
find . -not -name '*.mp3' -exec mv '{}' '{}.mp3' \;
```

Okay, that just renamed all the genre folders to (genre).mp3

I guess I'd have to find the folders with the files that don't have extensions and do it within each separate folder, is there a way to find folders with files with no extensions in them?

EDIT: Yeah, you're right, if I do that then I get "mv: cannot move `.' to `..mp3': Device or resource busy"
I'm gonna try krename..

any other ideas?

---

### Post by sad_iq on 2007-07-21
Ok...found it :popcorn:
darn...thowse man pages are long :( Here goes:
 ```
find . -type f -not -name '*.mp3' -exec mv '{}' '{}.mp3' \;
```
 [COLOR="Red"]**Experiment First!!!**[/COLOR]

---

### Post by Mornedhel on 2007-07-21
'rename' is cool too (takes any Perl expression as an argument, so you can really do whatever you want - regexps, etc.)

---

### Post by GStubbs43 on 2007-07-21
> **sad_iq said:**
> Ok...found it :popcorn:
darn...thowse man pages are long :( Here goes:
 ```
find . -type f -not -name '*.mp3' -exec mv '{}' '{}.mp3' \;
```
 [COLOR="Red"]**Experiment First!!!**[/COLOR]

Thanks! I think that'd work, but I did get it with krename.
Much nicer to know I can do it with the command line.

I tried it with test folders/files and it worked perfectly. :)

---

