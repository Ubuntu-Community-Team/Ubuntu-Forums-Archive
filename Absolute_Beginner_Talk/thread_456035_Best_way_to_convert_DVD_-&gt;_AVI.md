---
title: "Best way to convert DVD -&gt; AVI?"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by Catfish81 on 2007-05-27
What is the easiest way you have found to convert a DVD to AVI?

I've tried vobcopy (which worked, but I couldnt find how to get VOB to AVI).
I tried dvd::rip which didn't work really well. The target file size was 700Mb and it came out at about 450, with no sound and the frame rate was too great. Probably my fault not knowing how to configure it properly but hey... I've been looking for tutorials all day and can't find anything suitable for beginners.
I even tried Gordian Knot under Wine but that just doesn't work. Not for me anyway. I read on Doom9 forums it works but I don't know how.

The best I've found is SimpleRip: [http://f0rked.com/projects/simplerip](http://f0rked.com/projects/simplerip)
It encoded the movie over the target file size (it was about 845Mb or something) I don't know why, but this doesn't bother me really because I just watch from HDD. The quality came out good but the audio stream was the wrong one. I think it took track 1 which is French on the DVD instead of track 0 (English). So I am currently re-encoding to see if I can get it to do it with English audio.


What does anyone recommend for a t0t4l n00b to convert a DVD movie to AVI in Linux?

---

### Post by Bachstelze on 2007-05-27
This is the only thing for which I still have a use of Win, video encoding tools are still far superior there. I usually just fire up a vmware ;)

---

### Post by stuples on 2007-05-28
AcidRip is simple to use. Though it encodes on the fly.

I've had no luck finding a tutorial for dvd::rip. If you are a total noob then you will struggle to use it. I did use Gordian Knot (NOT AutoGK) when I had WinXP and have found it to be similiar, tho GK being the more complicated.

If you want a windows app to do DVD -> AVI then I recommend AutoGK. While for Linux just use AcidRip.

---

### Post by AAM on 2007-05-28
I have used VLC and find it rather simple. Put the DVD in and open up VLC. Go to:
**File | Open disc ...**
At the top select your DVD drive device name. Look at the bottom half and you will see a check box for [B]
Stream/Save[/B]
Check the box. The settings rectangle becomes active. Select this and another window opens. In Outputs, select the **File** checkbox and put in its filename (e.g., */home/aam/Desktop/Spiderman3.avi*). Select the encapsulation method, etc. and then OK. The DVD will start encoding. If you want to watch it at the same time, just above the filename tick the **Play locally** option also.

I haven't found anything simpler. There are more options to use, and this suits me.

VLC is great!

---

### Post by Catfish81 on 2007-05-28
Gordian Knot (the normal one) for Windows wasn't too hard to use mainly because they have rather good tutorials to go with it. I never got to use AutoGK, it is after my encoding days... until now since I am doing some again.

mencoder has been the best for me so far under Linux, only I have trouble getting it to keep the filesize to a size I want. It always goes over the limit fairly substantially and it appears to put AC3 sound in the AVI when all I want is MP3. It rips the sound out and puts it in MP3 format in a file, but I don't know if it then muxes that audio into the video AVI.

I guess I should take a long hard reading of TFM for mencoder...


anyone used mencoder much?

---

### Post by ron999 on 2007-05-28
-

---

### Post by glennph93 on 2007-05-28
What I use is acidrip, it uses mencoder, its easy once you have all the options set right.

install acidrip

Below is what I use to encode my movies

**Under general tab**:Hit load button to load dvd and highlight title you want to encode. Audio/Language  = 1:english (if use <default> English it may not be correct), Codec = lavc (mp3lame doesn't sync correct), Options acodec=mp3:abitrate=128 (whatever bitrate you want)

**Under video tab**: Video codec=x264 1 pass, I use about 850 bitrate(good for widescreen movies when cropping out black bars)  with the lock check (if not, it doesn't use bitrate it choses its own according to general tab File Size, I don't use this method I like keeping a standard bitrate), The crop section is important so it doesn't waste time encoding black area and keeps file size down.Click detect, if you notice Bits/Px value turns red(bitrate might be too low or too high) you may have to adjust Bitrate to make it turn black again.  Next I leave scale on the default 480 width since I'm viewing on a standard tv. 
If you don't use this next step your video may seem jumpy looking (very slight my wife doesn't see it but I do) check post filters and add this  *-ofps 24000/1001* ( it corrects for progressive scan dvds, although I use it for all my encodings)
Hit the Queue button (not sure if this is needed but kind of cool to look at the queue tab to see the actual mencoder command)
click start about hour and half later its done(example casino_royale 513 mb)

This gives me perfect results everytime.

---

### Post by ron999 on 2007-05-28
Thanks glennph93, that acidrip how-to works for me.
But it would not allow me to enter -ofps 24000/1001
It freaked out, have you spelt it correctly?

---

### Post by glennph93 on 2007-05-28
Not sure why it freak out its spelt correct. You did put it in the post filters. the queue should look like this:
mencoder dvd://1 -dvd-device /dev/dvd  -aid 128   -info srcform="DVD ripped by acidrip.sf.net" -oac lavc -lavcopts acodec=mp3:abitrate=128  -ovc x264 -vf crop=704:352:10:62,scale=480:-2, **-ofps 24000/1001**    -o "/media/sdb1/mythvideos/Movies/minority_report2.avi"

---

### Post by glennph93 on 2007-05-28
I think I found the problem sort of weird it didn't happen to me before (lucky) if you don't put a space before the -ofps 24000/1001 it freaks out.

---

### Post by ron999 on 2007-05-28
> **glennph93 said:**
> I think I found the problem sort of weird it didn't happen to me before (lucky) if you don't put a space before the -ofps 24000/1001 it freaks out.

Hi glennph93
Yes, that space has cured the trouble. It works OK now. Also I set language to 1:Unknown.
This is my queue, very similar to yours:-

mencoder dvd://5 -dvd-device /dev/dvd  -aid 128   -info srcform="DVD ripped by acidrip.sf.net" -oac lavc -lavcopts acodec=mp3:abitrate=128  -ovc x264 -vf crop=720:560:0:10,scale=480:-2, -ofps 24000/1001    -o "/home/ron/appeal_o6.avi"

Thanks for your help.
:cool:

---

### Post by robertpolson on 2007-05-30
How come no one mentioned Avidemux ?

[http://fixounet.free.fr/avidemux/](http://fixounet.free.fr/avidemux/)

Works well for me.

---

### Post by ron999 on 2007-05-30
> **robertpolson said:**
> 

Works well for me.

Well go on then, explain how-to.:confused:

---

### Post by Catfish81 on 2007-05-31
> **glennph93 said:**
> What I use is acidrip, it uses mencoder, its easy once you have all the options set right.

**Under video tab**: Video codec=x264 1 pass, I use about 850 bitrate(good for widescreen movies when cropping out black bars)  with the lock check (if not, it doesn't use bitrate it choses its own according to general tab File Size, I don't use this method I like keeping a standard bitrate), 

Hi Glenn,

Thanks for the help. I'm trying out acidrip right now. Hope it works.

I didn't understand your directions for the first part of the video tab. I like to encode the feature to a set filesize - 700Mb. This is more ideal to suit a CD - not that I often will put movies on CD but you never know.

If I leave the "Lock check" unticked does this mean that acidrip will encode the video with a determined bitrate to produce the desired filesize as it's found on the General tab? I guess I'll find out tomorrow when I check after the encode.

I'm currently trying to encode to xvid, 2pass with 160kbps mp3 audio. Hopefully it works.


Re: Avidemux - yes, its one thing to install the software on the computer easy enough but finding documentation that explains how to use it is hard.

---

### Post by ron999 on 2007-05-31
> **Catfish81 said:**
> 


Re: Avidemux - yes, its one thing to install the software on the computer easy enough but finding documentation that explains how to use it is hard.

Yes, I don't think that he read the question properly.
Avidemux will convert an mpg file into an avi file - but that's only half of the job.
;)

---

### Post by Catfish81 on 2007-05-31
I have an idea...

You see how AcidRip has the "Path:" text box option at the top right? Could you rip a DVD using vobcopy so you get the movie VOB files off the DVD first, then put the path to the VOBs in there and encode to AVI from that?

This would be better for queuing and encoding  rather than having rip from DVD and encode then change disc.

Also, does anyone know whether you can resume a broken encode? Will mencoder do that? Because my computer can be a piece of shi-takes sometimes and freezes for no good reason without warning. 4 hour encodes being done twice don't sit well with me.

---

### Post by Bigdog60 on 2007-05-31
Just use acidrip for linux if you know what you are doing.

---

### Post by Styx on 2007-05-31
acidrip looks very good but allways wen i tell it do use a file size of lets say 700 it tells me that the Bits/PX are to low if i use a different file size it tells me that is is to hight well wat ever i do i can not finde the right setting. I have to say that is is a video that some one made an put on a dvd an yes it is in dvd formate. Ist some project. 
I hope that some one can tell me how to put the setting so it will work. And i dont know the resolution it was made in. 
Thanks

---

### Post by Catfish81 on 2007-05-31
If you rip the DVD first with vobcopy and then load the .vob file it makes into acirip it should show you the resolution.

Also try playing the DVD in Totem Movie Player (Applications -> Sound and Video -> Movie Player) and press F9 (or View -> Sidebar) to bring up the "Sidebar" which will show video dimensions.

---

### Post by Styx on 2007-05-31
thanks for the info 

And i have an nother question i am trying to cut a short part out of the movie and make a avi or mpg (that dnot matter to me) out of it. I have tryed it with kino but that is drivning me crasy any good and easy programs for that and i am happy as can be

---

### Post by glennph93 on 2007-05-31
> **Catfish81 said:**
> Hi Glenn,

Thanks for the help. I'm trying out acidrip right now. Hope it works.

I didn't understand your directions for the first part of the video tab. I like to encode the feature to a set filesize - 700Mb. This is more ideal to suit a CD - not that I often will put movies on CD but you never know.

If I leave the "Lock check" unticked does this mean that acidrip will encode the video with a determined bitrate to produce the desired filesize as it's found on the General tab? I guess I'll find out tomorrow when I check after the encode.
.

Yes that is correct.

---

### Post by Catfish81 on 2007-06-01
Styx,

I havent played with cutting into video files yet. I know you can get avisplit but that s for chopping a file at desired filesizes, not sure if it cuts at time locations in the file and it sounds like you want a GUI program not a console based one. If I find something in the future I will post it back in here

On another note:
AcidRip also works if you use vobcopy to rip the VOBs from DVD first. I think you have to use the -l (that's an ELL) switch to make one big .vob file. And of course you need large file support filesystem to do this (no VFAT).

---

### Post by Styx on 2007-06-01
That would be good.
A GUI program would make it easyer but till then i have found mencoder to be a good alternative;)

I dit use acidrip to make an avi file and then mencode to cut te part out of it that i need.
```

mencoder -oac mp3lame -o 2new-file.avi -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=1000:vhq:vpass=1 -vop scale=640:480 -ss 15:20 -endpos 0:30 /styx/home/in-file.avi
```

Note that if you wont to use it this way the -endpos ist the time it will end AFTER the -ss option. So i just took the part from 15:20 to 15:50

There are better ways to do this i am sure but it will work that way. Any ideas pleas post them.

---

### Post by ron999 on 2007-06-01
Now then Styx
If you have ripped your DVD with Acidrip to make an AVI file then you can definitely use Avidemux to edit out sections.
It has a GUI and it's not so difficult to use.
Just load in your AVI file using File > Open then set the A and B markers and then use Edit > Cut.
The hardest part was ripping the DVD in the first place.

---

### Post by Styx on 2007-06-01
Oh ok
Thanks for the reply 
I will try this later.

---

### Post by Catfish81 on 2007-06-07
I've been paying around with acid rip, mencoder for a bit... i find it hard to get mencoder to output a file to an exact filesize. GKnot on Win32 does this well. I don't know what processing is required but. I will keep trying as I have got a few that have gone rather close (~10Mb).

I'm considering writing a bit of a HOWTO after i've sat down and read the mplayer man page a bit and looked around the net for more info. I feel there is a lacking of guides on how to convert from DVD to MPEG4 format (mainly xvid I would focus on)


Latest little thing Ive found is the 'turbo' option for xvid encoding (also available with lavc i think) which has seemed to speed my encoding up quite a bit.

When I have encoded from acidrip it takes about 10hrs, but today when I used the turbo option it seems like it halved the encode time.

---

### Post by sefs on 2007-07-13
Do you select a size in the general tab?  if so whats a good size.

under video tab my bitrate is 5000, and I am unable to change it do you know why?

I also had to increase my scaling so that the lock bits per pixel goes black.  is that normal i had to increse it to width 714 which sounds large... i've attached two pics one of general  tab and one of the video tab for guidence





> **glennph93 said:**
> What I use is acidrip, it uses mencoder, its easy once you have all the options set right.

install acidrip

Below is what I use to encode my movies

**Under general tab**:Hit load button to load dvd and highlight title you want to encode. Audio/Language  = 1:english (if use <default> English it may not be correct), Codec = lavc (mp3lame doesn't sync correct), Options acodec=mp3:abitrate=128 (whatever bitrate you want)

**Under video tab**: Video codec=x264 1 pass, I use about 850 bitrate(good for widescreen movies when cropping out black bars)  with the lock check (if not, it doesn't use bitrate it choses its own according to general tab File Size, I don't use this method I like keeping a standard bitrate), The crop section is important so it doesn't waste time encoding black area and keeps file size down.Click detect, if you notice Bits/Px value turns red(bitrate might be too low or too high) you may have to adjust Bitrate to make it turn black again.  Next I leave scale on the default 480 width since I'm viewing on a standard tv. 
If you don't use this next step your video may seem jumpy looking (very slight my wife doesn't see it but I do) check post filters and add this  *-ofps 24000/1001* ( it corrects for progressive scan dvds, although I use it for all my encodings)
Hit the Queue button (not sure if this is needed but kind of cool to look at the queue tab to see the actual mencoder command)
click start about hour and half later its done(example casino_royale 513 mb)

This gives me perfect results everytime.

---

### Post by glennph93 on 2007-07-13
sefs you can change the 5000 bitrate by checking the lock button(which overides the size set under the general tab) at the right and you should be able to put any value you want.

For the scaling I leave at a 480 width for Standard Def. to adjust the bits/pixel I change  the bitrate after I push the detect button(so acidrip doesn't have to encode black area) to adjust for croping (widescreen movies need a lesser bitrate).See Attachment
[ATTACH]38101[/ATTACH]

---

### Post by sefs on 2007-07-13
Thanks for you quick response....i went with the x264 encoding as you suggested ... and it grayed out things like bitrate and lock bits/px .  Is that normal.  since it grayed them out I could not change the bitrate.

see attachment.

PS: Do you think a 500 - 700 meg file is too big for google videos?

---

### Post by glennph93 on 2007-07-13
Huh thats strange must be a bug. I was just playing around with the encoding type and went back to x264 and my settings grayed out also. So I saved my settings(@x264) under the settings tab and closed then reopened acidrip and the options were back(not grayed out).

Not sure on size for google videos. I downed a video from one that was about 400mb.

---

### Post by sefs on 2007-07-14
Great, thanks for the tip, they do come back after saving and re-oping.

> **glennph93 said:**
> Huh thats strange must be a bug. I was just playing around with the encoding type and went back to x264 and my settings grayed out also. So I saved my settings(@x264) under the settings tab and closed then reopened acidrip and the options were back(not grayed out).

Not sure on size for google videos. I downed a video from one that was about 400mb.

---

### Post by jmusso on 2007-07-18
Hey, I'm using Acid Rip to rip dvds, but they all come out sub-par quality... I'm not sure how to make the quality better? I want them to be ripped in a higher resolution, the same resolution as they play on my computer... any clues please?

---

### Post by glennph93 on 2007-07-18
Not sure what  to recommend, I guess your viewing the rip vids on the computer full screen which makes a big difference in the way they appear.
Might want to try mpeg4(lavc) at higher bitrate 3000(5000 is what a dvd is at but the mpeg4 compresion will help) with scale set to 720 width. This should help but file sizes are going to be larger.

Anyone else have any ideas?

---

### Post by haroldwordup on 2008-06-28
OGMRip is the best you can have it over there : E-Z to use on ubuntu and gnome interface :-)

---

