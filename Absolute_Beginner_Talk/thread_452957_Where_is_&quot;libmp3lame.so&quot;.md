---
title: "Where is &quot;libmp3lame.so&quot;?"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by paker on 2007-05-23
I am saving an mp3 file in Audacity. But it wants me to locate "libmp3lame.so." I searched for this file but it's not on my computer. Where can I get this file?

What I am trying to do is to import 2 mp3 files and append one to the other. Audacity imports mp3's fine and appending is a breeze. But saving the file as mp3 is where I am stuck. Thank you.

Or, if anyone knows another program that will append mp3's (without asking a tough question), I will gladly switch to it.

---

### Post by jiminycricket on 2007-05-23
First install 'lame' from Synaptic (enable multiverse and universe).

Then, look for libmp3lame.so.* (it sometimes is libmp3lame.so.0.0.0) in /usr/lib

---

### Post by mitch.c on 2007-05-23
liblame-dev provides the file (without having to use libmp3lame.so.0.0.0... not that it matters much).

A big help in situations like this is the apt-file package, then when you need to figure out what package provides a particular file you can:
```
$ apt-file search libmp3lame.so
  liblame-dev: usr/lib/libmp3lame.so
  liblame0: usr/lib/libmp3lame.so.0
  liblame0: usr/lib/libmp3lame.so.0.0.0
```

---

### Post by paker on 2007-05-23
LAME has already been installed. I have been using Grip to rip CD to mp3's using LAME. I am not combining 2 mp3's into one. Synaptic says LAME is already installed (filled green square), version 3-96-1-2ubuntu1. "libmp3lame" is nowhere on my computer. Thanks.

I didn't see Mitch C's post. I am following your instruction now. I will write back. Thanks.

---

### Post by paker on 2007-05-23
> **mitch.c said:**
> liblame-dev provides the file (without having to use libmp3lame.so.0.0.0... not that it matters much).

A big help in situations like this is the apt-file package, then when you need to figure out what package provides a particular file you can:
```
$ apt-file search libmp3lame.so
  liblame-dev: usr/lib/libmp3lame.so
  liblame0: usr/lib/libmp3lame.so.0
  liblame0: usr/lib/libmp3lame.so.0.0.0
```
I typed "apt-file search libmp3lame.so" and hit enter. 

Then typed "liblame-dev: ......." 
bash liblame-dev command not found.

Same for liblame0.

Not knowing the significance of what I typed, I am still lost. Thanks.

---

### Post by mitch.c on 2007-05-23
> **paker said:**
> I typed "apt-file search libmp3lame.so" and hit enter. 

Then typed "liblame-dev: ......." 
bash liblame-dev command not found.

Same for liblame0.

Not knowing the significance of what I typed, I am still lost. Thanks.
Sorry, should have been more clear.

First, I have to assume you have the multiverse repository enabled. If you don't, let me know.

Install liblame-dev:
```
$ sudo apt-get install liblame-dev
```
Then you'll be able to find libmp3lame.so for Audacity.

If you want to use apt-file in the future, then use the same apt-get command to install that package:
```
$ sudo apt-get install apt-file
```
Let me know how it goes.

---

### Post by paker on 2007-05-23
Thanks. I found the file by using "extended form" option in the Audacity prompt screen. I clicked on ".....so.0" and confirmed the selection. It worked beautifully. Thanks.

---

### Post by ubromtoo on 2007-05-23
MITCH C :

     Thanks ,have been hoping to run across this info for a while now.  but I do have one

question:

     In the past, I would use Audacity to edit a given sound file, then export it as a WAV

file, then use SoundKonverter to change it from Wav to MP3.

      Now, using Audacity to export it directly as an MP3 file, it's an easier process, but

 the file size is nearly 4 times as large ; for instance 25.7 MB versus 6.8 MB .

       Could I be doing something wrong?   :-k

---

### Post by NJC on 2007-05-26
FWIW, this enabled me to Export to mp3 (after I had installed Lame package):

> Yeah,thanks,Orb,you're right,but I found the answer in another post that I can't find now,but basically all you have to do in Audacity is go to......
Edit>Preferences>File Formats>MP3 Export Setup>Find Library, and then it'll
ask you whether you want to find the libmp3lame.so file now,select yes,then
at the bottom where it says"Only libmp3lame.so", click there and select
"All files" and find libmp3lame.so.0.0.0 and hit OK and you should be good to go ! As shown here. Good Luck !
Attached Thumbnails
Click image for larger version Name: Screenshot-1.png Views: 56 Size: 126.1 KB ID: 15555  


[http://ubuntuforums.org/showpost.php?p=1483146&postcount=4](http://ubuntuforums.org/showpost.php?p=1483146&postcount=4)

---

