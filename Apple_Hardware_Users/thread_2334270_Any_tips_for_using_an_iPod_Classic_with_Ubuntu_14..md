---
title: "Any tips for using an iPod Classic with Ubuntu 14.04.5 LTS?"
date: 2016-08-17
forum: Apple Hardware Users
---

### Post by AbleTassie on 2016-08-17
I was just given an iPod Classic, 60GB. In looking at posts on these forums, there does not seem to be any posts since 2014 on using an iPod classic. All I want to do is transfer MP3 and WAV files from my PC to the iPod and listen to them. The File Manager in Lubuntu senses (sees) the iPod, but that appears to be the extent of it. So I am not sure how to proceed.

There is this link [https://help.ubuntu.com/community/PortableDevices/iPod](https://help.ubuntu.com/community/PortableDevices/iPod) that talks about gtkpod, Amarok, Rhythmbox and  Banshee. And this link ( [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone) ) that seems to recommend Banshee for newer iPods. I tried to download gtkpod, Amarok, Rhythmbox and  Banshee from the Lubuntu Software Center, but it says they all require trusting unauthenticated sources. So I cancelled the downloads/installations. I am not sure if I should download gtkpod, Amarok, Banshee or Rhythmbox given the lack of authentication. 

QUESTION(S): Does anybody have any comments or suggestions?

Thanks,

A.

---

### Post by mörgæs on 2016-08-18
I have never used an Ipod but transferring files to and from an Iphone using 16.04.1 works without problems.

---

### Post by AbleTassie on 2016-08-18
Thanks Morgaes. Do you use software such as gtkpod, Amarok, Rhythmbox or  Banshee to make the transfers? Do you or anybody else have any comments about downloading and installing gtkpod, Amarok, Rhythmbox and  Banshee (all of them are in the Lubuntu Software Center) even though the source is not authenticated? Does anybody else have any comments?

Thank you,

A.

---

### Post by mörgæs on 2016-08-19
I just made a standard install of 16.04.1, applied all updates and transferred the files (mostly photos) using PcManFM.

---

### Post by AbleTassie on 2016-08-19
Thanks Morgaes. I have been trying to avoid updating to 16.04 because of the time required. Among other things I would have to download and reinstall software including a virtual boxing of Windows.

Regarding downloading unauthenticated software from the Lubuntu Software Center, it appears I solved this. I installed another program (Audacity) using the Terminal Commands and I think this required some kind of consent for PPA updating. After the Audacity installation I was able to download and install Banshee from the Lubuntu Software Center without any warnings about unauthentication. 

However, I can only get the iPod Classic to work partially with Banshee. I can "Sync" and add WAV file tracks from my PC to the iPod, but only 10 tracks (out of a total of 16 tracks for a particular audio program) can be added. This happened twice now. And for some reason track 10 is placed second in the sequence at which tracks are played. The syncing process also seems to hang and never finish. I think this is a 5th generation iPod classic (circa 2005) with 60GB memory.

QUESTION(S): Anybody have any idea what is wrong? Why can't I get all 16 tracks added to the iPod, and why is track 10 out of order? Why is the syncing process hanging? Do you think another program like gtkpod, Amarok, or Rhythmbox would work better?  

Thanks,

A.

---

### Post by AbleTassie on 2016-08-19
This link [http://www.omgubuntu.co.uk/2016/04/how-to-upgrade-ubuntu-14-04-to-ubuntu-16-04-lts](http://www.omgubuntu.co.uk/2016/04/how-to-upgrade-ubuntu-14-04-to-ubuntu-16-04-lts) indicates that I can upgrade from Ubuntu 14.04 LTS to Ubuntu 16.04 LTS without a major time commitment and need to reinstall software. It also suggests waiting a while until the inevitable kinks in 16.04 are worked out.

Thanks,

A.

---

### Post by howefield on 2016-08-20
> **AbleTassie said:**
> It also suggests waiting a while until the inevitable kinks in 16.04 are worked out.

Which is about now with the first point release 16.04.1.

I'd tentatively suggest trying Rhythmbox before upgrading the whole operating system, unless of course that is what you want to do. I say tentatively because I haven't used it in about a year and a half. Any ipods I have set up for family or friends have been the classic model with Rhythmbox. Always worked a treat, but as I say, that is some time ago.

---

### Post by AbleTassie on 2016-08-22
OK, thank you howefield. I have actually downloaded and installed both Rhythmbox and Banshee. I will try to work with them. The Ipod classic I have is, I think, about 10 years old.

A.

---

### Post by AbleTassie on 2016-08-23
I seem to be able to use Rhythmbox pretty well now and have learned to add (import) to and delete lectures from (not really songs) the music library. I then sync the iPod with the music library and that allows me to listen to the sequence of lectures on the iPod in the correct order.

I have one final problem. I have CD files on my PC in the form of WAV files (e.g., numbered track1, track2, track3, etc). iPod apparently does not support WAV files, as I cannot sync the music library with WAV files with the iPod. (At least I cannot do the sync with "songs.") So apparently I need to convert the WAV files to MP3 files (or possibly to AIFF files). 

I have been able to make this conversion using Audacity and this allows me to play the WAV files from the CDs on the iPod. But it is a laborious process to convert multiple WAV file tracks one by one to MP3 files using Audacity.

QUESTION(S): Is there any way to **(1)** speed up the process of converting successive WAV files to MP3 files using Audacity or **(2)** use other software to efficiently convert successive WAV files to MP3 files?

Thanks,

A.

---

### Post by &amp;KyT$0P# on 2016-08-23
If the WAV files are all the same format you can use [ffmpeg]("https://ffmpeg.org/download.html") to convert the WAV files the same way you're doing it in Audacity.  Once you have a ffmpeg command you like you can use it in [[FONT=Courier New]for[/FONT] loop]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-7.html") to batch run it on all your files.

---

### Post by AbleTassie on 2016-08-24
Thanks halogen,

I notice that ffmpeg is not in the Lubuntu Software Center repository. Do you or others think this is much of a potential problem?

Thanks again,

A.

---

### Post by howefield on 2016-08-24
Another option(s) for you, either Soundconverter which is in the repositories or if you have the lame encoder installed, something like the following run from the folder that contains the wav files..

```
mkdir mp3 && for f in *.wav; do lame --vbr-new -V 3 "$f" ./mp3/"${f%.wav}.mp3"; done
```

Example.
```
hugh@xenial-laptop:/Data/Music$ mkdir mp3 && for f in *.wav; do lame --vbr-new -V 3 "$f" ./mp3/"${f%.wav}.mp3"; done
LAME 3.99.5 64bits (http://lame.sf.net)
Using polyphase lowpass filter, transition band: 17960 Hz - 18494 Hz
Encoding 01 - Okie From Muskogee.wav to ./mp3/01 - Okie From Muskogee.mp3
Encoding as 44.1 kHz j-stereo MPEG-1 Layer III VBR(q=3)
    Frame          |  CPU time/estim | REAL time/estim | play/CPU |    ETA 
  6231/6231  (100%)|    0:04/    0:04|    0:04/    0:04|   38.053x|    0:00 
 32 [  43] %*
 40 [   3] %
 48 [   4] %
 56 [   0] 
 64 [   1] %
 80 [   6] %
 96 [   8] %
112 [  11] %
128 [ 373] %%%%**********
160 [3556] %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%*********************************************************************
192 [1375] %%%%%%%%%%%%%%%%%%%%%%****************************
224 [ 320] %%%%%*******
256 [ 367] %%%%%%%%******
320 [ 164] %%%%**
-------------------------------------------------------------------------------------------------------------------------------------------
   kbps        LR    MS  %     long switch short %
  177.0       44.8  55.2        88.1   5.9   6.0
Writing LAME Tag...done
ReplayGain: -3.0dB
hugh@xenial-laptop:/Data/Music$
```

---

### Post by &amp;KyT$0P# on 2016-08-24
> **AbleTassie said:**
> I notice that ffmpeg is not in the Lubuntu Software Center repository. Do you or others think this is much of a potential problem?
It's a bit individualised whether it's potential problem or not.  How specifically do you think it could be a problem for you?

EDIT
There is in the repositories a package [libav-tools]("http://packages.ubuntu.com/trusty-updates/libav-tools") containing the [FONT=Courier New]avconv[/FONT] program which is a fork of ffmpeg..

---

### Post by AbleTassie on 2016-08-24
Halogen and Howefield,

Thank you very much. I have been able to play podcast lectures (each lecture is an MP3 file) on my "new" (second hand from a relative) iPod classic (circa 2005, I think). No problem. But, I have literally spent several hours trying to come up with a reasonable solution to the latest problem I am having here.  

THE LATEST PROBLEM: I also want to play lectures from multiple CDs on the iPod Classic. Each lecture was on a separate CD in the form of multiple numbered WAV files that must be played in a sequential order. I have copied the WAV files for each CD onto my PC. I wanted to use a program like Banshee or Rhythmbox to get the WAV files onto the iPod. 
The only way I can see to do this right now is by making each WAV file be a "song" in music. Unfortunately when I try to sync the music library, the WAV files are all over the place in terms of order. Initially I thought the Rhythmbox did not mix up the order of tracks (as Banshee was doing). On the other hand , but Rhyhmbox could not sync WAV files to the iPod. So I tried converting the WAV files to MP3s, then I tried syncing in Rhythmbox. Unfortunately now Rhythmbox is now mixing up the order of the tracks on the iPod as well.

I have tried learning about playlists and play queus, etc, all to no avail.

BEST SOLUTION SO FAR:

---

### Post by howefield on 2016-08-25
So you have a CD with multi tracks, ripping the tracks gives you a load of files which do not easily play sequentially in the ipod, is that correct ?

How about ripping the CD to a single track with something like abcde. This will rip the cd to a single .wav file and then encode to mp3. (silence between the tracks is preserved)

Example :
```
hugh@yakkety:~$ abcde -c ~/.abcde.conf -1 -a default -o mp3 /dev/cdrom
[WARNING] ONETRACK mode selected, grabbing all tracks...
Executing customizable pre-read function... done.
Getting CD track info... Querying the CD for audio tracks...
Grabbing entire CD - tracks: 01 02 03 04 05 06 07 08 09 10
Obtaining Musicbrainz results...
Retrieved 1 Musicbrainz match...done.
---- Spice Girls / Spiceworld ----
1: Spice Up Your Life
2: Stop
3: Too Much
4: Saturday Night Divas
5: Never Give Up on the Good Times
6: Move Over
7: Do It
8: Denying
9: Viva Forever
10: The Lady Is a Vamp

Edit selected CDDB data [y/N]? 
Is the CD multi-artist [y/N]? 
Grabbing tracks 01 - 10 as one track ...
cdparanoia III release 10.2 (September 11, 2008)

Ripping from sector       0 (track  1 [0:00.00])
	  to sector  174321 (track 10 [3:09.31])

outputting to /home/hugh/abcde.eVRCNarv5bAKxYw71ewJAysmEnY-/track01.wav

 (== PROGRESS == [                       +++    | 174321 00 ] == :^D * ==)   

Done.


 echo Encoding track 01 of 01: Spiceworld...
Encoding track 01 of 01: Spiceworld...
encodetrack-mp3-01 nice -n 10 lame -V 2 /home/hugh/abcde.eVRCNarv5bAKxYw71ewJAysmEnY-/track01.wav /home/hugh/abcde.eVRCNarv5bAKxYw71ewJAysmEnY-/track01.mp3
LAME 3.99.5 64bits (http://lame.sf.net)
Using polyphase lowpass filter, transition band: 18671 Hz - 19205 Hz
Encoding /home/hugh/abcde.eVRCNarv5bAKxYw71ewJAysmEnY-/track01.wav
      to /home/hugh/abcde.eVRCNarv5bAKxYw71ewJAysmEnY-/track01.mp3
Encoding as 44.1 kHz j-stereo MPEG-1 Layer III VBR(q=2)
    Frame          |  CPU time/estim | REAL time/estim | play/CPU |    ETA 
 88978/88978 (100%)|    1:03/    1:03|    1:03/    1:03|   36.550x|    0:00 
 32 [  130] %
 40 [    0] 
 48 [    0] 
 56 [    0] 
 64 [    1] %
 80 [    1] %
 96 [    1] %
112 [   15] %
128 [  994] %**
160 [22644] %%%%%%%%%%%%******************************************
192 [43318] %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%**************************************************************
224 [12031] %%%%%%%%%%%******************
256 [ 7180] %%%%%%%**********
320 [ 2663] %%%****
------------------------------------------------------------------------------------------------------------------
   kbps        LR    MS  %     long switch short %
  196.2       33.5  66.5        89.8   5.6   4.6
Writing LAME Tag...done
ReplayGain: -8.9dB
encodetrack-01 true
 echo Tagging track 01 of 01: Spiceworld...
Tagging track 01 of 01: Spiceworld...
tagtrack-mp3-01 nice -n 10 eyeD3 --set-encoding utf16-LE -A Spiceworld -a Spice Girls -t Spiceworld -G 255 -n 01 -N 01 --comment=::abcde version 2.7.2 /home/hugh/abcde.eVRCNarv5bAKxYw71ewJAysmEnY-/track01.mp3

track01.mp3	[ 54.30 MB ]
-------------------------------------------------------------------------------
Time: 38:44	MPEG1, Layer III	[ ~195 kb/s @ 44100 Hz - Joint stereo ]
-------------------------------------------------------------------------------
No ID3 v1.x/v2.x tag found!
Setting artist: Spice Girls
Setting album: Spiceworld
Setting title: Spiceworld
Setting track: 01
Setting track total: 01
Setting track genre: 255
Setting comment: []: abcde version 2.7.2
Writing tag...
ID3 v2.4:
title: Spiceworld		artist: Spice Girls
album: Spiceworld		year: None
track: 1/1		genre: Unknown (id 255)
Comment: [Description: ] [Lang: eng]
abcde version 2.7.2
tagtrack-01 true
movetrack-01 mv /home/hugh/abcde.eVRCNarv5bAKxYw71ewJAysmEnY-/track01.mp3 /home/hugh/Music/mp3/Spice Girls-Spiceworld/Spiceworld.mp3
movetrack-output-mp3 true
Finished.
hugh@yakkety:~$ 
```

Using abcde with a .conf file from the excellent [http://www.andrews-corner.org/abcde.html](http://www.andrews-corner.org/abcde.html)

---

### Post by AbleTassie on 2016-08-25
SORRY, MY PREVIOUS POST WAS INCOMPLETE LAST NIGHT BECAUSE I LOST MY INTERNET CONNECTION WHILE WRITING THE POST. 

**Regarding your suggestion Howefield to use abcde:** First, the CDs are already "ripped" in the sense that the WAV files have been copied from the CDs onto my PC in a separate folder for each CD. There were so many CDs that it would not be practical for me to go back and re-rip them. Second, I am not very familiar with command line code. But I do use terminal commands as necessary. I am willing to consider using abcde, but it looks like it would take a lot of time to learn to use. More details of my current situation, which were composed off line before signing on to the forum, are below. Thanks A.

   Halogen and Howefield,

Thank you very much. I have been able to play podcast lectures (each lecture is a single MP3 file) on my "new" (second hand from a relative) iPod classic (circa 2005, I think). No problem, because each lecture is a single audio file.  
 
 But, I have literally spent several hours trying to come up with a reasonable solution to the problem of playing lectures copied from CDs, because each CD lecture is a series of WAV files. And I have concluded (as I explain below) that the best solution may be to combine the 20 or so WAV files on each CD into a single WAV file (or other audio file) before “syncing” onto the iPod.  
 
 QUESTION(S): So my main question at this point: Is there an efficient way to combine WAV files (or another type of audio file) in the correct order into a single audio file?

Would Winff for avconv or ffmpeg, as mentioned by Halogen, work to combine audio files?

MORE DETAILS IF DESIRED: I want to play lectures from multiple CDs on the iPod Classic. Each lecture was on a separate CD in the form of multiple numbered sequential WAV files that must be played in a sequential order. I have copied the WAV files for each CD onto my PC. I wanted to use a program like Banshee or Rhythmbox to get the WAV files onto the iPod. 

The only way I can see to do this right now is by making each WAV file be a "song" in music. Unfortunately when I try to sync the music library, the WAV files are all over the place in terms of order. Initially I thought Rhythmbox did not mix up the order of tracks (as Banshee was doing). But Rhyhmbox could not sync WAV files to the iPod. So I tried converting the WAV files to MP3s, then I tried syncing in Rhythmbox. Unfortunately now Rhythmbox is now mixing up the order of the tracks on the iPod as well.

I have tried learning about playlists and play queues, etc, all to no avail.

BEST SOLUTION SO FAR: Clear the music library in Banshee and clear the music in the iPod > Import the WAV files from a single CD as music into the music library of Banshee > sync the iPod. (This gives the WAV files on the iPod in a jumbled order) > finally manually use the iPod buttons to make an "on the go playlist" with the WAV file tracks playing in the right order. It takes some time, but is doable. 

 At this point I am only making one "on the go playlist" at a time using WAV files from a single CD. But I think I could make two or more “on the go playlists” by relabeling WAV files from different CDs in order to distinguish different CD tracks, so I can manually make multiple “on the go” playlists. But this is laborious.

PROPOSED SOLUTION: I think the best solution is to combine the WAV files from each CD in the correct order into a single WAV file. (The WAV files from each CD are numbered Track 1, Track 2, Track 3, etc.) Alternatively Sound Converter (which works well, thanks, Howefield) could be used to convert each CD WAV file into another type of file, which could then be combined – again in the right order. I know that Audacity can be used to combine WAV files, but combining 20 WAV files with Audacity is laborious.  

 I know ffmpeg can be used to combine WAV files in some way using Terminal commands. But ffmpeg is not in the repos and also requires a lot of terminal commands. To answer your question Halogen about ffmpeg, I am trying to stay away from software not in the repos. The ffmpeg website does mention security as a potential problem. I know the people at ffmpeg are probably doing a great job, but I want to stay with repos software as much as possible. But this may not be possible.

 I think there is a program or command called sox that can combine audio files. But I would like suggestions.

 AGAIN, MY QUESTION(S): Is there an efficient way to combine WAV files (or another type of audio file) in the correct order into a single audio file?

Would Winff for avconv or ffmpeg, as mentioned by Halogen, work to combine audio files?
 
 Thanks again,
 
 A.

---

### Post by howefield on 2016-08-26
> **AbleTassie said:**
> ... I think there is a program or command called sox that can combine audio files. But I would like suggestions.

```
sox path/to/source/files/*.wav /path/to/destination/output.wav
```

would do it, however you may need to be mindful of the file naming, ie, use a leading zero, eg, track01 track02 ect.[/QUOTE]

---

### Post by AbleTassie on 2016-08-26
OK, thank you to everybody especially lately Howefield, and Halogen. We have covered a lot of ground here and I hope this will be helpful to people. In reading about sox (sound exchange) somebody said: "If you want a GUI, use Audacity." So I started reading more about Audacity.

 I think I have figured out how to combine many (e.g., 20) separate sequential audio tracks quickly using Audacity :P (see under my name below). And it seems to work, so I will continue to play around with this more, but will likely mark this thread a SOLVED very soon. 

Thanks again,

Able

**Here is the link that taught me the procedure** [http://manual.audacityteam.org/man/faq_editing.html#join](http://manual.audacityteam.org/man/faq_editing.html#join)

It reads:

**How do I combine two files into one longer file?**

 Follow these steps to splice two files together: 
 
[LIST=1]
[*]Use File > Import > [Audio...]("http://manual.audacityteam.org/man/file_menu.html#import") to import both files into separate Audacity tracks one above the other 
[*]Select the second file by clicking above the Mute/Solo buttons on its [Track Control Panel]("http://manual.audacityteam.org/man/audio_tracks.html#panel") (where the ***[sample rate]("http://manual.audacityteam.org/man/glossary.html#sample_rate")*** in ***[Hz]("http://manual.audacityteam.org/man/glossary.html#hz")*** is shown) 
[*]Choose Edit > [Find Zero Crossings]("http://manual.audacityteam.org/man/edit_menu.html#zero") 
[*]Choose Edit > [Cut]("http://manual.audacityteam.org/man/edit_menu.html#cut") 
[*]Place the cursor at the end of the first track by clicking in it then pressing K 
[*]Choose Edit > [Paste]("http://manual.audacityteam.org/man/edit_menu.html#Paste") 
[*]Optionally, click the X track close button top left of the [Track Control Panel]("http://manual.audacityteam.org/man/audio_tracks.html#panel") on the tracks you cut the audio from. 
[/LIST]
 A time-saving alternative if you have many tracks to combine is to choose Edit > Select > [All]("http://manual.audacityteam.org/man/edit_menu_select.html#all"), then Tracks > Align Tracks > [Align End to End]("http://manual.audacityteam.org/man/tracks_menu.html#consec"). This aligns the selected tracks one after the other so they follow the [Timeline]("http://manual.audacityteam.org/man/timeline.html"). If it's more convenient to make the result into one Audacity track, you can then choose Tracks > [Mix and Render]("http://manual.audacityteam.org/man/tracks_menu.html#mix").
     Press the green "Play" button to hear the result, and use the File > [Export Audio...]("http://manual.audacityteam.org/man/file_menu.html#export") command to save it as an audio file.

[U][B]Cautions and Experiments:
[/B][/U]
As a caution, I think you have to wait until all the tracks are loaded  into Audacity, which takes a little time (i.e., not done in a few  seconds). 

As another caution, when importing into Audacity, I found that the track  order was, again, not maintained. So you should scroll down to make  sure the tracks are in the right order. The "boundary" between Track 9  & Track 10 seems to be some kind of marker for the audio software in  Audacity, the iPod, Banshee and Rhythmbox. Why I don't know, but this  seems to have caused the sequence difficulties I ran into with the iPod,  Banshee and Rhythmbox. So in order to get the right order in Audacity I  had to import tracks 1-9 first, then import tracks 10-18 second. I  think that took care of the problem.

I am also starting to experiment: exporting as an MP3 file instead of a  WAV file reduces the memory space from 1.1 GB down to 54.6 MB without  adversely affecting sound quality. 

The lectures are in stereo as well. I think that converting them into mono would probably reduce the memory  space even more.  This is accomplished in Audacity by going to  Tracks>Stereo Track to Mono then exporting the audio file. **I tried this:** when  exported as an MP3 file, the memory space went from 54.6 MB (stereo)  down to 47.1 MB (mono), about 13.5% reduction, without any noticeable  change in sound quality.

---

### Post by AbleTassie on 2016-08-31
As described in my previous post I have been using Audacity to convert multiple audio WAV sequential stereo files to a single mono audio file, wherein the tracks have been joined sequentially. (I have found that it is unnecessary to "select all tracks" prior to converting the tracks from stereo to mono or to aligning the tracks end to end.) There is a caution in the previous post about first importing tracks 1-9, then later tracks 10-last to get the correct track order. I then add the single mono MP3 to the music library of a syncing software (e.g., Rhythmbox or Banshee) and then "sync" the iPod classic with  the music library. And I listen to each lecture (MP3 file) as a "song." 

I have been using that procedure I described in my last post is working well, except for one caution. For some reason Banshee truncates (cuts off the end) of the MP3 files when I use it (Banshee) to sync to the iPod. Rhythmbox does not truncate like this. So I have been using Rhythmbox to sync the iPod. 

It is easy to check for this problem, just (1) look at the duration of the MP3 file on the harddrive (you may need to open the MP3 file in "listening" software such as GNOME Mplayer to see the duration and then (2) check the duration on the iPod and in the Syncing program. If (1) is longer than (2), then the Syncing program is truncating the MP3 file.

In summary, this procedure allows me to listen to individual lectures as a single "song" and works well. 

Another procedure is to import the individual multiple (e.g., 20) tracks into the music library of the syncing program (like Banshee) and then sync the iPod classic. But in this procedure, each track is a "song," but the tracks were usually out of order. So I had to make sure the tracks played in the right order. To make this happen I constructed an "on the go" playlist for playing the songs. This is done by selecting each track (or "song") in the order in which you want it to play and then pressing & holding the center button down until the track (or "song") flashes. Similarly, a track or song can be removed from the playlist by selecting the track and then pressing & holding the center button down until the track flashes.

A diagram (or picture) of an iPod classic showing the click wheel ( [https://en.wikipedia.org/wiki/IPod_click_wheel](https://en.wikipedia.org/wiki/IPod_click_wheel) ) with center button is at this link [https://en.wikipedia.org/wiki/IPod_Classic](https://en.wikipedia.org/wiki/IPod_Classic) 

I will mark this thread as SOLVED. Thanks again to everybody. :P

Thanks,

Able

---

