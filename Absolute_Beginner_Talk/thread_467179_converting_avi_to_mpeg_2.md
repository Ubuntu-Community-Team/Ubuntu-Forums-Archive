---
title: "converting avi to mpeg 2"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by Tedis on 2007-06-07
I have seen alot of threads on this, but there hasn't been any clear answers that worked.

I simply need to convert an avi file to an mpeg-2 file so I can author a dvd with it.  I just want to convert the file itself so I can set the quality to be as high as possible.  I have seen stuff with Mencoder, but it didn't work.  

Please, someone help! Also, I am kind of a linux n00b, so please be as specific and detailed as possible.

Thanks

---

### Post by Cypher on 2007-06-07
[ffmpeg]("http://ffmpeg.mplayerhq.hu/") will handle the job.

---

### Post by Tedis on 2007-06-07
I just tried:

ffmpeg -i input.avi output.mpg

It 'worked' but the output.mpg file was terrible quality.  Is there any way to set the quality to full, or something?

---

### Post by Immolatus on 2007-06-07
do it again and watch the file size. Is it increasing or decreasing?

---

### Post by Cypher on 2007-06-07
ffmpeg has numerous options that can control all aspects of the encoding/decoding stages. I'm not the most familiar person with ffmpeg yet, so check out the documentation on that site and play around with some of the options.

Also, you might want to do run through two passes to get things in ship-shape order..

---

### Post by underdog512 on 2007-07-31
> **Cypher said:**
> 

Also, you might want to do run through two passes to get things in ship-shape order..



How do you do this

---

### Post by little_penguin on 2007-08-03
> **Tedis said:**
> I have seen alot of threads on this, but there hasn't been any clear answers that worked.

I simply need to convert an avi file to an mpeg-2 file so I can author a dvd with it.  I just want to convert the file itself so I can set the quality to be as high as possible.  I have seen stuff with Mencoder, but it didn't work.  

Please, someone help! Also, I am kind of a linux n00b, so please be as specific and detailed as possible.

Thanks

Hi Tedis,

An easy way to convert avi to mpeg2 (SVCD) which can be played in a standalone DVD player is to use Avidemux. You can get this from the Ubuntu repositories via Synaptic.

- Open your avi file in Avidemux.
- Then from the Auto menu, just select SVCD - this preloads some defaults automatically. 
- Now just click Save, give it a name, and off it goes. If you need better quality, just experiment a bit.

Regards,
little_penguin

---

### Post by kelvin spratt on 2007-08-03
I use DeVeDe it is very similer to convertXtodvd in windows download the latest version 3.0
from [http://www.getdeb.net/](http://www.getdeb.net/)   and it also has menus, do a 10sec preview if you have sound problems go to their site and down load the patch at the bottom of the page, render to ISO, right click on ISO select write to disc and click providing you've put a disc in the jobs done

---

### Post by Mize on 2007-10-04
> **Tedis said:**
> I just tried:

ffmpeg -i input.avi output.mpg

It 'worked' but the output.mpg file was terrible quality.  Is there any way to set the quality to full, or something?

add -sameq before the output filename to match the input file quality.

---

### Post by sophtpaw on 2007-10-13
> **kelvin spratt said:**
> I use DeVeDe it is very similer to convertXtodvd in windows download the latest version 3.0
from [http://www.getdeb.net/](http://www.getdeb.net/)   and it also has menus, do a 10sec preview if you have sound problems go to their site and down load the patch at the bottom of the page, render to ISO, right click on ISO select write to disc and click providing you've put a disc in the jobs done

Hi Guys..

i was looking for a solution to burning avi to dvd. and fell on this thread in my search. Can i say i've used DeVeDe and sometimes it works. Essential is to use the preview to make sure there are no streaks. Unfortunately half the time an avi will show up with lots of horizontal streaks. Why i don't know... Could it be the quality of the avi?

Anyhow, is there another way? i was told mpeg2... So, i downloaded ffmpeg but i see no gui frontend in Applications for it and besides i am reading here that it has compromised the quality.

Is there another way still(besides running back to windows) and how, please?

--
sophtpaw

---

### Post by vanadium on 2007-10-13
It has been mentionned already: avidemux is a graphical linear video editing utility that allows to transcode to mpg2. Command-line ffmpeg will be fastest for this job, but the difficulty is to find the right command line options. Under the "Auto" menu, Avidemux has options to automatically set the required filters and transformations for video DVD.

---

### Post by sophtpaw on 2007-10-13
it s not clear at all to me how avidemux creates mpeg from avi 

any pointers there... coz it looks super unintuitve to me

thank you

---

### Post by vanadium on 2007-10-14
It seems you better invest in the command line conversion. I am doing some attempts here, but upon saving, Avidemux crashes or freezes, etc. I have used it successfully before to combine and split dvd video, though. Anyway, the principle is:

* Load Avidemux
* File - Open; locate and open your AVI video
* In the main screen, select "Video: DVD (lavc)", "Audio: fmm ac3", "Format: mpeg PS A+V" (mpeg Program stream for dvd authoring)
It is my impression that the functions for automatic resizing are not working, unfortunately. You therefore need to resize manually to the required DVD resolution. I guess pal might be  720 x 540, but I could be wrong. Then press "Filters" under Video, under "Transform" press "Resize", specify 720 x 540 (look up the correct resolution!)
* Press Save. At that moment, video and audio should be converted according to the settings in Video and Audio, repectively, and combined in to an output file as specified in "Format". I am testing here with a small camera video of 15 fps, and it fails.

---

### Post by lamadredelsapo on 2007-10-14
have you tried* man ffmpe*g?

---

### Post by juantovarm on 2007-10-14
Since ffmpeg comes with preconfigured output values, i suggest you read your **man ffmpeg **. It is a very powerful and fast tool, the best i've used, and the simplest (once you get used to if, of course :) )

---

### Post by kane77 on 2007-12-23
the basic ffmpeg command for converting file to mpeg2 (video dvd) is something like this:
```
ffmpeg -i input_file.avi -target pal-dvd output.,mpg
``` (or ntsc dvd, depeds what dvds you want pal is used in europe, ntsc is used in US, but almost all dvd players are able to play both)
if you want you can use -b 5000k to specify the bitrate... video dvd can have up to 9Mbps (= **-b 9000k** in ffmpeg's option)

the -ab (audio bitrate) option works just like -b, but you don't need to set audio bitrate, by default it's set to ac3 at 448kbits, which is very good and you wouldn't save much data by choosing lower quality

you can then use QDVDauthor to create the video DVD

---

