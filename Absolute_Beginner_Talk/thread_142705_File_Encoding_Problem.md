---
title: "File Encoding Problem"
date: 2006-03-11
forum: Absolute Beginner Talk
---

### Post by heyjoe on 2006-03-11
Hi, I was wondering if somebody out there could help me. I'm wanting to conver wav files into mp3 for my mp3 player but am having a few problems. I have downloaded audacity. When it opens i get an error message saying-THere was an error initializing the audio i/o layer. You will not be able to play or record audio. Then when it opens and i attempt to 'export as mp3' it asks me for libmp3lame.so. Now I have installed lame 3.96.1-1 using synaptic and have extracted a lame-3.96.1.zip file into a folder i named LAME. where do i go from here?

thanks in advance,
frank

p.s.- i am an absolute beginne with an absolute limited knowledge of the command line.

---

### Post by Pragmatist on 2006-03-12
I wrote a simple script that works like a charm:
 ```

 #!/bin/sh
 
 # mylame: A script to batch convert WAV files to MP3 using the lame encoder
 
 for arg
 do
    y=`basename "$arg" .wav`;
    y=$y.mp3;
    lame -h "$arg" "$y";
 done
 
```  
cut and paste this code into a text editor and save the file in your home directory (I called my file: mylame) Then type this to make it executable:
 
 ```
chmod a+x mylame
```  Check to make sure it is executable:
 ```
ls -l mylame
```  the permissions at the far left should be: [B]-rwxr-xr-x

[/B]Now to use this is extremely easy.  You just type this:
```
mylame filenames
```  You can put a single filename, filenames seperated by spaces, or whole directories:
```
mylame filename.wav
``` ```
mylame filename1.wav filename2.wav filename3.wav
``` ```
mylame directory/*
``` Note in this last case I put a /* after the directory name. This just means, "take every file in this directory and feed them to this command (mylame)". It is equivalent to your manually appending each filename in that directory after the command name mylame (the directory/* is much easier :)

After the one-time setup, this is so easy and **fast** that after you've tried it once you'll never use a GUI tool again.

---

### Post by uselessinfo on 2006-03-29
Pragmatist, I just tried out your script, and I must say that it's just great. Thanks very much for posting it!

---

