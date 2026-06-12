---
title: "Converting files to Xvid"
date: 2014-08-26
forum: Any Other OS
---

### Post by firas2 on 2014-08-26
Good day 

usually in windows I use divx converter   , so I also found a divx converter for Linux   but it is not doing the job 

can any one recommend  a good tool 

many thanks

---

### Post by TheFu on 2014-08-26
simple-mpeg4.sh
```
#!/bin/sh
#
# This is for really simple mpeg4.avi conversion, use
#
for filename in "$@"; do

   IN=$filename
 nice ffmpeg -i "$IN" -sameq -f avi -vcodec mpeg4 -acodec copy "$IN-ffmpeg.avi" 
done

```

or

simple-xvid-2pass.sh 
```
#!/bin/sh
#
# This is for really simple XVID conversion, use
#
XVIDENCOPTS="bitrate=1400:max_key_interval=250:trellis:max_bframes=1:vhq=3"
# XVIDENCOPTS="fixed_quant=4:max_key_interval=250:trellis:max_bframes=1:vhq=3"

for filename in "$@"; do

   IN=$filename
      
   NICE_LEVEL="+15"

   nice /usr/bin/mencoder "$IN" -oac mp3lame -lameopts preset=128 -ovc xvid \
        -vf lavcdeint -noodml -forceidx -ffourcc XVID \
        -xvidencopts ${XVIDENCOPTS}:pass=1 -of avi -o "${IN}-xvid.avi"
   nice /usr/bin/mencoder "$IN" -oac mp3lame -lameopts preset=128 -ovc xvid \
        -vf lavcdeint -noodml -forceidx -ffourcc XVID \
        -xvidencopts ${XVIDENCOPTS}:pass=2 -of avi -o "${IN}-xvid.avi"
done

```
I haven't used these scripts in a few years - switched to using handbrake for h.264. Anyway - shows what is possible using 2 different tools.  Oh - and don't pass in any files with spaces in the names.

---

### Post by firas2 on 2014-08-26
thank u sir 

please forgive me    But   I put the movie name in / for filename in   correct ?? 

or what should i fill out

---

### Post by TheFu on 2014-08-26
You need to read the scripts, decide which you want to use, install any dependencies (ffmpeg or mencoder) save it locally inside a file, make the file "executable", then run it with a list of files to be converted passed as arguments on the command line.

Sounds complex when I write it all out, but it isn't. It is standard Linux CLI stuff.

---

### Post by firas2 on 2014-08-26
ok will fallow 

thanks

---

### Post by TheFu on 2014-08-26
There may be GUI tools - but all those that I've seen are based on ffmepg.  Any search on the internet for video converters for iphone, ipad, android phones, tablets are almost universally based on ffmepg.  I say - skip the middleman - use ffmepg directly. ;)  I suspect the software center might have a video converter - don't know.

---

### Post by firas2 on 2014-08-26
Im with u on this   skip the middleman :p

---

### Post by FakeOutdoorsman on 2014-08-26
```
ffmpeg -i input -vcodec mpeg4 -acodec libmp3lame -q:v 2 -q:a 4 output.avi
```

For more info see [FFmpeg MPEG-4 Part 2 Video Encoding Guide](https://trac.ffmpeg.org/wiki/Encode/MPEG-4). Get a build from the [FFmpeg Download](http://ffmpeg.org/download.html) page or [compile it](http://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu).

---

### Post by firas2 on 2014-08-27
> **TheFu said:**
> You need to read the scripts, decide which you want to use, install any dependencies (ffmpeg or mencoder) save it locally inside a file, make the file "executable", then run it with a list of files to be converted passed as arguments on the command line.

Sounds complex when I write it all out, but it isn't. It is standard Linux CLI stuff.

well My frien I keep getting 

No such file or directory   :mad:

I tried running it in every way I know  and made sure i am in the right place   witch is home

---

### Post by firas2 on 2014-08-27
> **FakeOutdoorsman said:**
> ```
ffmpeg -i input -vcodec mpeg4 -acodec libmp3lame -q:v 2 -q:a 4 output.avi
```

For more info see [FFmpeg MPEG-4 Part 2 Video Encoding Guide]("https://trac.ffmpeg.org/wiki/Encode/MPEG-4"). Get a build from the [FFmpeg Download]("http://ffmpeg.org/download.html") page or [compile it]("http://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu").

thank u sir for ur help   I would Love to have ffmpeg , I did download it from there website  ,  But I couldnt figure out how to run it :p

So i gave up on it  ,, sorry newbi here

---

### Post by SeijiSensei on 2014-08-27
Telling a new Ubuntu user that he or she needs to compile something is definitely not the best approach.

OP, try installing **winff** with "sudo apt-get install winff" then choose AVI from the "Convert to" box and the appropriate XviD "Preset" for your content.

---

### Post by firas2 on 2014-08-27
> **SeijiSensei said:**
> Telling a new Ubuntu user that he or she needs to compile something is definitely not the best approach.

OP, try installing **winff** with "sudo apt-get install winff" then choose AVI from the "Convert to" box and the appropriate XviD "Preset" for your content.



It worked   many many thanks   wow   that is what im looking for 

thank u sir

---

### Post by FakeOutdoorsman on 2014-08-27
> **firas2 said:**
> thank u sir for ur help   I would Love to have ffmpeg , I did download it from there website  ,  But I couldnt figure out how to run it :p

So i gave up on it  ,, sorry newbi here

You just have to download it (from one of the links under the "Linux Static Builds" section), then extract it (the file browser GUI should be able to do that for you or use the tar command), then navigate to the directory containing the ffmpeg file you downloaded. Then just run it in terminal, but don't forget the **./**:
```
./ffmpeg -i input -vcodec mpeg4 -acodec libmp3lame -q:v 2 -q:a 4 output.avi
```

> **SeijiSensei said:**
> Telling a new Ubuntu user that he or she needs to compile something is definitely not the best approach.

Notice that I also provided a link to simply download a binary, and even new users who can follow instructions and cut and paste have compiled successfully.

---

### Post by firas2 on 2014-08-27
> **FakeOutdoorsman said:**
> You just have to download it (from one of the links under the "Linux Static Builds" section), then extract it (the file browser GUI should be able to do that for you or use the tar command), then navigate to the directory containing the ffmpeg file you downloaded. Then just run it in terminal, but don't forget the **./**:
```
./ffmpeg -i input -vcodec mpeg4 -acodec libmp3lame -q:v 2 -q:a 4 output.avi
```



Notice that I also provided a link to simply download a binary, and even new users who can follow instructions and cut and paste have compiled successfully.

Hi  ur right  I did not open the Link  u provided , sorry   there was a reson i did not do so ,  I was thinking it will take me back to the home page where i was @ the first place :p
and did not get any luck

if this makes it clear  ,  and English is my third Language ,   ( but im hanging in there :p )

many thanks

---

### Post by dave131 on 2014-08-29
Does OpenShot video converter allow you to do this?  I use it for other things - like converting old home movies or extracting/pasting parts of videos, but I never tried using dvix as the output type so I don't know if it supports it or not.

---

### Post by firas2 on 2014-08-29
> **dave131 said:**
> Does OpenShot video converter allow you to do this?  I use it for other things - like converting old home movies or extracting/pasting parts of videos, but I never tried using dvix as the output type so I don't know if it supports it or not.

Good day  Im not sure about openshot   But here take a look at winff   it worked great for me 

[http://u.cubeupload.com/elfc/20140829214216384x21.png](http://u.cubeupload.com/elfc/20140829214216384x21.png)

[http://u.cubeupload.com/elfc/201408292143181920x1.png](http://u.cubeupload.com/elfc/201408292143181920x1.png)

---

### Post by andrew.46 on 2014-08-30
> **FakeOutdoorsman said:**
> For more info see [FFmpeg MPEG-4 Part 2 Video Encoding Guide]("https://trac.ffmpeg.org/wiki/Encode/MPEG-4").

My eyes are not good enough to see if it really makes a huge difference but I usually use this as well:

[3.9 Which are good parameters for encoding high quality MPEG-4?]("http://www.ffmpeg.org/faq.html#Which-are-good-parameters-for-encoding-high-quality-MPEG_002d4_003f")

Certainly looks pretty reasonable on my wife's tv which is one of those unfortunate devices that does not understand h.264, aac and mp4 container :(.

---

### Post by firas2 on 2014-08-30
> **andrew.46 said:**
> My eyes are not good enough to see if it really makes a huge difference but I usually use this as well:

[3.9 Which are good parameters for encoding high quality MPEG-4?]("http://www.ffmpeg.org/faq.html#Which-are-good-parameters-for-encoding-high-quality-MPEG_002d4_003f")

Certainly looks pretty reasonable on my wife's tv which is one of those unfortunate devices that does not understand h.264, aac and mp4 container :(.

very good info   thanks

---

