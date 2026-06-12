---
title: "Mass Convert WMA files to mp3?"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by medya on 2007-07-02
hey
is there any command to convert many WMA files to mp3?

let say you have a music folder and you want to convert every WMA there to MP3.
how to do it ?


and can that thing work Recursivly ? like you call it to do all the folders in music -->pop
music--classic.... (all sub-folders)

thanks

---

### Post by kingof1981 on 2007-07-02
hey... maybe this will help...
just go to the menu "Applications"
select "Add/Remove Programms"
search for "Sound Converter"
select "apply" and vaula you can convert almost every soundfile in this you want to have...

---

### Post by John.Michael.Kane on 2007-07-02
One these guides may help.

[**HOWTO: convert wma to mp3**]("http://ubuntuforums.org/showthread.php?t=37793")

[**Convert WMA to MP3**]("http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Convert_WMA_to_MP3")

---

### Post by Sockerdrickan on 2007-07-02
remember ogg is better (if you are going to use it for your mp3-player then you can't play them probably though)

---

### Post by medya on 2007-07-02
why ogg is better?

---

### Post by greg_g on 2007-07-02
Because they say so!?  ;)

No really, there have been comparisons done, this page is a good reference:

[http://www.xiph.org/vorbis/listen.html](http://www.xiph.org/vorbis/listen.html)

Also, here is what they say about converting already compressed (like mp3s) to ogg:

> 
Can I convert my MP3 collection to the Ogg Vorbis format?

    You can convert any audio format to Ogg Vorbis. However, converting from one lossy format, like MP3, to another lossy format, like Vorbis, is generally a bad idea. Both MP3 and Vorbis encoders achieve high compression ratios by throwing away parts of the audio waveform that you probably won't hear. However, the MP3 and Vorbis codecs are very different, so they each will throw away different parts of the audio, although there certainly is some overlap. Converting a MP3 to Vorbis involves decoding the MP3 file back to an uncompressed format, like WAV, and recompressing it using the Ogg Vorbis encoder. The decoded MP3 will be missing the parts of the original audio that the MP3 encoder chose to discard. The Ogg Vorbis encoder will then discard other audio components when it compresses the data. At best, the result will be an Ogg file that sounds the same as your original MP3, but it is most likely that the resulting file will sound worse than your original MP3. In no case will you get a file that sounds better than the original MP3.

    Since many music players can play both MP3 and Ogg files, there is no reason that you should have to switch all of your files to one format or the other. If you like Ogg Vorbis, then we would encourage you to use it when you encode from original, lossless audio sources (like CDs). When encoding from originals, you will find that you can make Ogg files that are smaller or of better quality (or both) than your MP3s.

    (If you must absolutely must convert from MP3 to Ogg, there are several conversion scripts available on Freshmeat .)


---

### Post by petit_prince on 2007-11-05
As far as I can tell, none of the above answers do what you actually want. This is what did the job for me:
```
find . -type f -exec gst-launch-0.10 filesrc location='{}' ! decodebin ! lame bitrate=192 ! filesink location='{}'.mp3 \;
```

**[SIZE="3"]Explanation of the above command:[/SIZE]**
```
find . -type f
``` means "show all files contained in this directory"
```
-exec
``` means "for each of the files do the following"
```
gst-launch-0.10
``` is an application to build filter-sets which can be used to do all sorts of things -- such as converting music!
```
filesrc location='{}'
``` means "read from this file", where {} is replaced with whatever ```
find
``` finds in your directory.
the exclamation marks are basically pipe symbols -- because we can't use the normal pipe symbol, as it would be interpreted by the shell.
```
decodebin
``` means "do whatever is necessary to attach the former filter to the next one"
```
lame bitrate=192
``` means "convert to mp3 using lame at a bitrate of 192kbit/s"
```
filesink location='{}'.mp3
``` means "save the output into this file", where {} is again replaced by the respective file name.
```
\;
``` marks the end of the command.


Hope this helps you.
dan

---

