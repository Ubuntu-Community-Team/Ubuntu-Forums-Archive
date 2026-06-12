---
title: "[SOLVED] What's a Good DVD Ripper/Converter?"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by Paul133 on 2007-09-06
I've searched these forums and the web, but I cannot find a DVD ripper that works. I've tried dvd::rip, which seemed to rip the DVD, but took up over 7 gigabytes of hard drive space, when it said the final size would be 1399 MB. Additionally, it froze after ripping and I had no video file. I've also tried acidrip, which wouldn't even rip my DVD. What I want to do is rip a DVD into a .avi file, so I can transfer it to my Cowon D2, which takes, according to Cowon's site 'AVI : MPEG4 ~ 2Mbps, 320x240, 30fps, MP3 audio' files. So what ripper should I try? If I can't find anything that'll work, I guess I'll have to bite the bullet and use Windows.

---

### Post by rsambuca on 2007-09-06
I always have used dvd::rip myself.  I think the reason it is creating the large files is because it isn't finishing the transcoding portion.  Unless you specifically change the settings, it just rips the dvd to your drive first, and then starts transcoding into your requested format.  Obviously sounds like it is ripping, and then getting caught up with the transcoding process.

Have you tried running it from a terminal, so you can see error messages?

---

### Post by nonewmsgs on 2007-09-06
the best freeware rippers are RipIt4Me and dvdfabdecryptor.  both are windows programs but ripit4me does work in wine and there's a howto guide in this forum.  hold on and ill post a link.

---

### Post by Paul133 on 2007-09-06
Oh, so the ripping is larger than the output of the transcoding (which is 1399 MB)? OK. What happened was that it took about 30 minutes to rip a 2 hour DVD (very reasonable). I checked Gparted and was just shocked how much space it took up. It finally finished ripping and then I guess started to transcode. It said it was grabbing a preview image, but it seemed to hang at 25%. So what do you think I should do? Just try it again but start it from the terminal?

---

### Post by rsambuca on 2007-09-06
I would try it from the terminal, that way you will see the error messages.  If you still have the rips on your hard drive, then just open the project and you won't have to go through that again, you can just start at the transcoding phase.

---

### Post by toidi on 2007-09-06
Transcoding is always a slow and laborious issue.  It might just be that the program appears to have locked out but is actually still doing its job.

Never did any in linux yet but an example of a few transcodes I have did in windows:

800mb avi file 90 mins transcoded to dvd format 1hr 25 mins using convertx 5 hours using tmpeg (high quality).

Transcoding dvd to avi files was usually a little quicker, however varied greatly with different quality settings.

This was all done on a amd 4200 DC with 2 gig of ddr2 ram.

Hope this helps.

---

### Post by mc4man on 2007-09-06
You should try k9copy. I see it'll convert to mpeg4, never tried that option but as far as a ripper it works great. This way you can rip then convert with something else if it doesn't do the conversion as you'd like. While k9 outputs to an iso the video_ts is stored in your tmp folder, just cancel when it starts the "burn"(building iso) if you want to work from the video_ts folder
You can set the size to dvd9 size so it will only rip
Additionally k9 can handle most structure protection in full disk and the latest arcross in reauthor mode

---

### Post by chrome307 on 2007-09-06
There's a guide for K9Copy with MPeg4 conversion available here:

[http://linuxappfinder.com/blog/ripping_dvds_to_mpeg4_with_k9copy](http://linuxappfinder.com/blog/ripping_dvds_to_mpeg4_with_k9copy)

---

### Post by Paul133 on 2007-09-06
As far as the encoding, I just didn't think it would take that long because the ripping only took half an hour. What I'm going to do now is try K9copy with MPEG4 conversion (will that give me a .mpg file or a .avi file?) and see if that works. How big will the rip be? Because my /home partition only has 3.95 gigs of free space, while my / partition has 23.58 gigs of free space.

edit: Started the ripping/encoding; the output file should be 700MB x 1. Not sure how big the rip would be (if they're separate) but I just saved it to my /home folder.

---

### Post by sloggerkhan on 2007-09-06
Thoggen anyone? I love it, personally. Works pretty well, especially if you are willing to be slightly loose with file size. Easy to use. Open source format. What's not to love?

---

### Post by Paul133 on 2007-09-06
Well, my player doesn't play Theora, just Vorbis. I guess I could always get a Theora-to-Xvid converter.

---

### Post by nonewmsgs on 2007-09-06
all the guides for ripit4me under wine seem incomplete (they all relied on this one forum's post where i initially set mine up.  that post along with that section of the forum have been removed :|  it amazes me that the mpaa still belives it can put the genie back in the bottle and eliminate knowlege with FUD.  they should stick to fighting the new technologies like bluray and hddvd and let us back up our legally owned old fashion  dvds in peace.

within the next few weeks i intend to make my own how to.

---

### Post by sloggerkhan on 2007-09-06
What player are you using that doesn't play ogg/theora? Are you using windows or something? Just get VLC.

---

### Post by andrew.46 on 2007-09-07
Hi,

 Ripping a dvd to your computer would be quickest with vobcopy, IMHO:

```
vobcopy -v -m /media/cdrom0 
```

Although you can play / encode from this ripped copy on your computer:

```
mplayer dvd://1 -dvd-device /path/to/directory
```

You might be better to use mencoder to encode directly from the DVD to an avi on your Desktop. I am unfamiliar with this technique and have only done a quick test with the following command line syntax, drawn straight from the manual, and I would *strongly* suggest you do a bit more research before following this path:

```
mencoder dvd://1 - -o test.avi -oac copy -ovc lavc -lavcopts vcodec=mpeg4
```

The manual gives a fair few examples, selecting different chapters, different encoding options etc and I am sure there will be detailed discussion elsewhere:

>  **Encode DVD title #2, only selected chapters:**
       mencoder dvd://2 -chapter 10-15 -o title2.avi -oac copy -ovc lavc -lavcopts vcodec=mpeg4

      ** Encode DVD title #2, resizing to 640x480:**
       mencoder dvd://2 -vf scale=640:480 -o title2.avi -oac copy -ovc lavc -lavcopts vcodec=mpeg4

      ** Encode DVD title #2, resizing to 512xHHH (keep aspect ratio):**
       mencoder dvd://2 -vf scale -zoom -xy 512 -o title2.avi -oac copy -ovc lavc -lavcopts vcodec=mpeg4

       **The same, but with bitrate set to 1800kbit and optimized macroblocks:**
       mencoder dvd://2 -o title2.avi -oac copy -ovc lavc -lavcopts vcodec=mpeg4:mbd=1:vbitrate=1800

       **The same, but with MJPEG compression:**
       mencoder dvd://2 -o title2.avi -oac copy -ovc lavc -lavcopts vcodec=mjpeg:mbd=1:vbitrate=1800

       **Encode all *.jpg files in the current directory:**
       mencoder "mf://*.jpg" -mf fps=25 -o output.avi -ovc lavc -lavcopts vcodec=mpeg4

     **  Encode from a tuner (specify a format with -vf format):**
       mencoder -tv driver=v4l:width=640:height=480 tv:// -o tv.avi -ovc raw

     **  Encode from a pipe:**
       rar p test-SVCD.rar | mencoder -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=800 -ofps 24 -



 Anyway I must go and stop encoding Solaris to avi, I seem to be running out of disk space very quickly :-) Have a look at:

[http://www.mplayerhq.hu/DOCS/HTML/en/index.html](http://www.mplayerhq.hu/DOCS/HTML/en/index.html)

                     Andrew

---

### Post by Paul133 on 2007-09-07
Slogger, you don't seem to understand. I'm using a Cowon D2, a portable music/video player. Hardly any portable video players support Theora. At least the Cowon supports Ogg. :) I actually used K9copy and that worked beautifully. It took 2 hours, but it worked. I believe it encoded on the fly, so it wa slow, but it only took up 500 MB of space, as opposed to the 7 gigs I was getting with dvd:rip. 

Unfortunately, I chose the wrong audio track and ended up with the directors' commentary instead of just the movie audio. All well. I'd also like to note that the D2 has some A/V sync issues, and while the transcoded DVD worked fine on my computer, the video was twice as fast as the audio. This was solved by using this script: [http://ubuntuforums.org/showthread.php?t=404589&highlight=cowon](http://ubuntuforums.org/showthread.php?t=404589&highlight=cowon) So, for now, my needs have been solved and I will proceed to mark the thread as such. Thanks for all your help, guys!

---

### Post by wild77 on 2007-09-13
> all the guides for ripit4me under wine seem incomplete (they all relied on this one forum's post where i initially set mine up. that post along with that section of the forum have been removed it amazes me that the mpaa still belives it can put the genie back in the bottle and eliminate knowlege with FUD. they should stick to fighting the new technologies like bluray and hddvd and let us back up our legally owned old fashion dvds in peace.


try this link for a guide on Ripit4Me as well as some other good dvd programs
[http://forums.afterdawn.com/thread_view.cfm/478357](http://forums.afterdawn.com/thread_view.cfm/478357)

---

