---
title: "How to record RealAudio/streaming media?"
date: 2005-06-08
forum: Absolute Beginner Talk
---

### Post by agger on 2005-06-08
There's an interview which is sent as streaming video on an indie TV channel (in Real Audio format - a ".rm" file) - however, I'd like to record it to a file in order to be able to see it offline. How do i do this? I'm seeing the show in xine, but I can find no "save as file" or "record/grab" option on the menu.

Perhaps some other application exists which can do it?

I'd like to "grab" and save it to disk in RealAudio or (preferrably) MPEG-format.

Thanks in advance,
Carsten

---

### Post by shof2k on 2005-06-08
There's a forum topic on how to do this.  I think it's in the HOW TO section.  Good luck!

---

### Post by agger on 2005-06-10
[QUOTE=shof2k]There's a forum topic on how to do this.  I think it's in the HOW TO section.  Good luck![/QUOTE]
 This is the forum and I don't see a HOWTO section? But perhaps you mean the Wiki?

regards and TIA

Carsten

---

### Post by tiglionabbit on 2005-07-05
[http://ubuntuforums.org/showthread.php?t=28356](http://ubuntuforums.org/showthread.php?t=28356)

This thread explains how to rip a stream to mp3s using streamripper.  The last post mentions that using a feature of mplayer, you can rip as the original .rm files.  Hope this helps, go read up on mplayer!  ( [their website](http://www.mplayerhq.hu/homepage/design7/news.html) ,   #mplayer on freenode )

---

### Post by shof2k on 2006-04-30
Try the following from a command line:

1)Dump the stream to your PC
```
 mplayer -playlist *your real stream url* -dumpstream -dumpfile output.ram
```

2) Convert the dump to a WAV file.
```
mplayer pov -ao pcm:file=file.wav 
```

3) Convert to WAV to mp3.
```
lame -f file.wav filem.p3
```

Don't forget to pay attention to any legal implications of where you do this.

Hope that helps

---

### Post by shof2k on 2006-05-05
Also a nice HOWTO here:
[http://www.ubuntuforums.org/showthread.php?t=169278](http://www.ubuntuforums.org/showthread.php?t=169278)

---

### Post by ftmichael on 2007-06-10
I just tried that and it worked perfectly; I tried again half an hour later and it didn't create the dump file.  I didn't change any settings.  I have no idea why it just magically didn't work the second time.  Rebooting didn't help.

Thoughts?

**Edit:** This worked:
> $mplayer -ao pcm:file=test url-of-streaming-audio

So what happened?

Michael

---

### Post by andrew.46 on 2007-09-11
Hi,

 There is a slightly more polished way of doing that which means you do not have to extract the address of the .rm / .ra file:

> **ftmichael said:**
> 

```
$mplayer -ao pcm:file=test url-of-streaming-audio
```



Simply find the address of the *.ram* file and then:

```
mplayer -playlist address.ram -ao pcm:file=filename.wav -vo null -vc null
```

 Let me know if this works for you?

              Andrew

---

### Post by xrdguy on 2007-12-13
I used vlc and it was damn easy to save video. for example i  tried to save video from 

[www.rajshri.com](www.rajshri.com)

when the page is loaded press ctrl+u to view source in firefox and u will get some url 
mms://rajshri-96.wmod.llnwd.net/a1005/d1/secure/musicvideos/highbw/Ho Gayi Hai Mohabbat_WMV_512Kbit_stream.wmv?e=1197590400&h=a2f32898b09d91578c183b42ef88fb30

here is the key is to copy those numbers as well. i guess that is some sort of encryption key. if u copy till wmv then it will give u error. then open vlc and follow this tutorial

[http://forum.videohelp.com/topic316907.html](http://forum.videohelp.com/topic316907.html)

i saved the video in asf and it works perfectly.. hope this might help

---

### Post by rex_the_first on 2008-07-12
Hi, I just read this thread and wanted to say thanks.  Here is a bash script to do all of this automatically (made in Hardy but should work in other versions).

To run it in the terminal type
```
bash RunRadioRip.sh
```


It encodes with the default lame option as "--preset voice" and to change that use
```
bash RunRadioRip.sh "-V 3 --vbr-new"
```
see [http://www.hydrogenaudio.org/forums/index.php?showtopic=28124]("http://www.hydrogenaudio.org/forums/index.php?showtopic=28124") for more lame options.

---

### Post by AnonCat on 2008-07-12
You can use Audacity to record any output being processed by the sound hardware.  You want to set the mixer to mono basically.  The following sites tell you how:

For KDE:
[http://liquidat.wordpress.com/2007/05/07/howto-record-soundcard-output-with-audacity-in-kde/](http://liquidat.wordpress.com/2007/05/07/howto-record-soundcard-output-with-audacity-in-kde/)

For Gnome:
[http://jjjunk.com/2008/04/30/howto-record-soundcard-output-in-audacity-gnome/](http://jjjunk.com/2008/04/30/howto-record-soundcard-output-in-audacity-gnome/)

---

