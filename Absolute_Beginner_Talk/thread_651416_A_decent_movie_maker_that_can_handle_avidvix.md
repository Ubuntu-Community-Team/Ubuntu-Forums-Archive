---
title: "A decent movie maker that can handle avi/dvix"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by anewguy on 2007-12-27
After a previous thread I tried the "Kino" movie maker package, but it won't read in my .avi files.  These are files I have downloaded from a video camera.  In Windows I need the dvix codecs to play them and they have the extension of .avi in Linux.  They play back in Totem Movie Player - although since I went to Gutsy EVERYTHING plays back either all choppy or not at all in Totem when they worked fine in Feisty.

Is there another package similar to Windows Movie Maker for Ubuntu besides Kino for me to try?  I want to create a couple of videos from a series of these clips and then burn them on a video cd (hopefully I can do that in Linux as I did in Windows).

Thanks in advance!!:)

BTW - I've seen mention of something called Ubuntu Studio in other posts dealing with video.  Is this a separate version of Linux or is it an add-on to Gutsy?

---

### Post by disturbedite on 2007-12-27
avidemux is stupendous.

Ubuntu Studio is an Ubuntu based (as i'm sure you have guessed ;)) distro geared towards multimedia production.  i believe it is a member of the "official" ubuntu family.

---

### Post by OffAxis on 2007-12-27
you could also try pitivi ([http://www.pitivi.org/wiki/Main_Page]("http://www.pitivi.org/wiki/Main_Page")
(both that and avidemux are in the repos)

---

### Post by dannyboy79 on 2007-12-27
devede. can make video cd's from avi files. I use it to make DVD's for my friends who don't have divx dvd players and who don't have computers. There's also tovid but I am not sure if it does video cd's, it may only do dvd's.

---

### Post by rickycodie on 2007-12-27
no, guys, mandvd is the best. 

getdeb.com

it brings all the boys to yard.

god i'm bored.

---

### Post by anewguy on 2007-12-27
Okay, the first thing I did was install kdenlive - it seems to do the easy "editing" I want to.  However, it does not show an option to save as something like an mpeg file.  I need the resulting video from this to also be playable in Windows with no special codecs.  That is what I was able to do before with Windows Movie Maker.  Also, I don't have a DVD drive - I have a CD drive, and I want to create a video CD, not a DVD.  I hope this all makes sense as it is the best I know with my limited knowledge to explain what I need to do.  After kdenlive, if there is no way to create a "universal" (please excuse the use of that term) video then I need something which can convert the output of kdenlive to something like mpeg3 or something.  When I did this a few years ago with family movies I transferred from old 8mm tape movies into my computer, I used movie maker to create the "reels" I wanted merged, then wrote out a video CD.  That's basically what I need to do now.

Help???  Maybe a little more simplified comments for a newbie at video processing.

Thanks!:)

---

### Post by dannyboy79 on 2007-12-27
open the avi files in kino, you will have to import them. Edit them, saveas mpeg, use Devede to make the videocd.

OR use avidemux, see here:[http://www.arsgeek.com/?p=452](http://www.arsgeek.com/?p=452)

---

### Post by ugm6hr on 2007-12-28
> **anewguy said:**
> Okay, the first thing I did was install kdenlive - it seems to do the easy "editing" I want to.  However, it does not show an option to save as something like an mpeg file.  I need the resulting video from this to also be playable in Windows with no special codecs.  That is what I was able to do before with Windows Movie Maker.  Also, I don't have a DVD drive - I have a CD drive, and I want to create a video CD, not a DVD.  I hope this all makes sense as it is the best I know with my limited knowledge to explain what I need to do.  After kdenlive, if there is no way to create a "universal" (please excuse the use of that term) video then I need something which can convert the output of kdenlive to something like mpeg3 or something.  When I did this a few years ago with family movies I transferred from old 8mm tape movies into my computer, I used movie maker to create the "reels" I wanted merged, then wrote out a video CD.  That's basically what I need to do now.

Help???  Maybe a little more simplified comments for a newbie at video processing.

Thanks!:)

I have been using kdenlive recently.  It allows you to export to loads of formats, but it is mainly designed to export direct to playable DVD format (i.e. so it can burn direct to DVD for a regular player rather than computer).

I am a bit unclear on what you want to do.  You say you want mpeg files to play on Windows etc, but then also wnt a Video CD (presumably to play in VCD / DVD players).

Anyway - hope this helps:
To export to mpeg, select export Timeline (or select the relevant video with the green bar which looks like a first tab marker initially just above the time line next to the time line zoom control, right-click and "Render selected zone").
In the Rendering window - select "Medium quality" tab.  MPEG4 is a good format (and recommended by Youtube), so just click on the + sign and it lists the various resolutions, and then again to give High, Medium, Low qualities.
The click render.

I found that if you multitask (especially with Compiz on), kdenlive aborts the rendering process, altho this may be because my laptop doesn't really have the processing power for video editing).

As for creating a VCD - I think you can do them directly from kdenlive (export to DVD), but I haven't tried.  I would recommend DeVeDe (but make sure you read about MPlayer RC2 here: [http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html))  You can just use the .avi (MPEG4) in DeVeDe, but there may be a higher quality way to do it.

---

### Post by anewguy on 2007-12-28
Yes, you are right on track for what I want to do.  When I used Windows Movie Maker in the past, I think it may have created .wmv files, but I know my Dad and Mom can play one of the .avi's I sent them in the mail.  What I want to do is concantenate a string of video clips (.avi) with a small pause between them, into 1 larger .avi  .  I want to do this for 3 sets of clips, so I would have 3 larger clips (.avi).  Then just a way to burn them to a video CD - and it appears you have answered that question - I just need to figure out how to enable something called "backports" in software sources so I can actually install DeVeDe.  Working on that at the moment.  I'll post back what happens - thanks for the help!:)

---

### Post by disturbedite on 2007-12-28
> **rickycodie said:**
> no, guys, mandvd is the best. 

getdeb.com

it brings all the boys to yard.

god i'm bored.
mandvd has a great interface, but it blows chunks as far as options are concerned.  avidemux is prolly best for making dvds as far as options & flexibility.  qdvdauthor is another one i use, its much better than mandvd too, imho.

---

### Post by anewguy on 2007-12-28
Keep in mind I don't have a dvd drive - I need to create a video CD.  Still working with the export in kdenlive to avi, then will try some more.

I did install the "downgrades" of the 2 pieces (mplayer and something else - mencode??) needed for DeVeDe (didn't install it yet though), then tried playing one of the .avi's in movie player again (it always comes up as totem movie player - is that what I'm supposed to get??).  Again, everything is either VERY choppy, or else it acts like it is playing (the timer goes up and everything stops at end) but only shows the opening frame.  I don't get it because all of that worked in Feisty but after I did a clean install of Gutsy it has never worked since!  Anyone else have that problem?  Even with the "downgrades?

Thanks for the help!  I'll post back after the conversion finishes and I have a chance to try it out.:)

---

### Post by anewguy on 2007-12-28
Okay, here's the latest.  Kdenlive finally finished exporting the timeline to a .avi file in the middle of the night, at least until it filled my disk up and died!  Admittedly I don't have much free space (4 gig), but how did it turn a timeline containing 39 clips with a total of 60 meg in all the clips into 4 gig?  Any ideas?

Thanks!:)

---

### Post by ugm6hr on 2007-12-28
> **anewguy said:**
> Okay, here's the latest.  Kdenlive finally finished exporting the timeline to a .avi file in the middle of the night, at least until it filled my disk up and died!  Admittedly I don't have much free space (4 gig), but how did it turn a timeline containing 39 clips with a total of 60 meg in all the clips into 4 gig?  Any ideas?

If the originals were divx, then an mpeg4 file will always be larger, although not that much larger.  Certainly the final file will not be anything like that size - but I think it does require free space for temporary files for the encoding process.  To be honest, I'm not 100% certain - but if drive space is an issue, try encoding at low quality with 640x480 resolution to make sure it works OK.  A 10min video should be under 100MB at that quality.

---

### Post by anewguy on 2007-12-28
Thanks - I'll give that a try.  Since it takes quite a while to do it, I'll post back when it finishes.:)

---

### Post by dannyboy79 on 2007-12-28
well if Kdenlive is anything like kino, it imports it as a DV file, I imported a 6mb wmv file and it made a 600mb DV file. So, you're going to need a hell of a lot of room IF kdenlive is anything like kino.

---

### Post by dannyboy79 on 2007-12-28
> **ugm6hr said:**
> If the originals were divx, then an mpeg4 file will always be larger, although not that much larger.  Certainly the final file will not be anything like that size - but I think it does require free space for temporary files for the encoding process.  To be honest, I'm not 100% certain - but if drive space is an issue, try encoding at low quality with 640x480 resolution to make sure it works OK.  A 10min video should be under 100MB at that quality.
avi is a mpeg4, avi is only a container for the audio and video put together. DV is digital video and is huge. You ever record HD over firewire? The files are ginormous. I record SDTV over s-video using mythtv and 30 min show is around 1gb in size.

---

### Post by anewguy on 2007-12-28
Okay, here is the latest, and I need more help!

I used kendlive to export the timeline as just mpeg at 640x480 (I thought mpeg would be the one that my relatives tv-top dvd-players might be able to handle) - it was a LOT faster and came out at roughly 90meg.  I then used DeVeDe to "convert" that file into a video CD (not DVD) ISO .bin file.  Then I used k3b (reminds me of a very prominent Windows app - very good interface, etc.) to burn that ISO to a CD.  It worked - kind of.  The sound starts out about 2 seconds behind the video and by the end of 10 minutes it is a good 15 seconds behind the video.  Obviously that won't do.  I haven't tried just using the "create video cd" feature of k3b yet, as it would appear the clips would be individual videos, and I need them concantenated together (with a small gap between each).

Maybe a brief outline of the "project" would help:  I sent my parents and each of my sisters small cheap camcorders to record some video to send out to everyone of the grandkids, etc..  Everyone made several little clips.  For each group, say for instance my parents, I want to join all of the clips into 1, bringing the total number of videos to 3 (my parents and both of my sisters).  Then I want all these burned together on a video CD so they can play them on their PC or on the TV-top dvd player.  I have no DVD drive on my computer, so it must be video CD as output.

Any ideas on keeping the sound in sync?

Thanks again!:)

EDIT:  videoCD in k3b (I think this is actually a "standard") is mpeg1 or mpeg2 only, so I can't just directly load the .avi files into k3b.  Is there a DECENT .avi to mpeg (not mpeg3 or mpeg4) converter that will keep sound, etc., in sync with the video?

---

### Post by ugm6hr on 2007-12-29
Where was the sound lag problem?  Does the mpeg created in kdenlive run OK?  Or is it just the VCD conversion that messes it up?

I have never had this problem, but then I've only made one video. I suspect one of the things that can cause problems is if you switch from NTSC to PAL (or vice-versa), since the video frame rates are different, but obviously not the sound.  Are all the original recordings in a single format?  If so - try and keep kdenlive and DeVeDe in the same format too.

If it is kdenlive causing the problem - perhaps keeping a separate track for audio might work:
[http://en.wikibooks.org/wiki/Kdenlive/FAQ#How_can_I_split_the_audio_from_the_video_in_a_clip.3F](http://en.wikibooks.org/wiki/Kdenlive/FAQ#How_can_I_split_the_audio_from_the_video_in_a_clip.3F)

---

### Post by Irihapeti on 2007-12-29
A couple of things that I've read about but haven't actually tested myself:

I seem to recall that Kdenlive has audio/video sync problems in NTSC. I've only ever needed to use PAL, so I can't verify this.

I saw a post that said to enable Gutsy backports in the repository settings, install those versions of Mplayer/Mencoder and then lock the versions of those two packages if you don't want to keep the repository enabled. Again, I've done no video editing in Gutsy to be able to verify this.

Mencoder and ffmpeg do conversion from the command line, if you don't mind messing around with that. The mplayer docs (the html version from the repositories) give some sample commands that look as though they might do what you are looking for. I have used ffmpeg this way, but only to convert PAL .vob files to PAL .dv

---

### Post by ugm6hr on 2007-12-29
> **Irihapeti said:**
> I seem to recall that Kdenlive has audio/video sync problems in NTSC. I've only ever needed to use PAL, so I can't verify this.

I saw a post that said to enable Gutsy backports in the repository settings, install those versions of Mplayer/Mencoder and then lock the versions of those two packages if you don't want to keep the repository enabled. Again, I've done no video editing in Gutsy to be able to verify this.


I have only used PAL on kdenlive too - and it works fine.  Not sure about NTSC.

And I think he has already installed the correct mplayer - if you don't, you just get continuous noise rather than sound.

@anewguy:
Shame you are having problems with such an easy task...

---

### Post by fiddledd on 2007-12-29
Apologies if already mentioned in previous thread (that I haven't found yet ), but I found someone with a very similar problem to you that has solved it:

[http://linuxgeekboy.wordpress.com/2006/06/26/windows-movie-maker-for-linux-users/](http://linuxgeekboy.wordpress.com/2006/06/26/windows-movie-maker-for-linux-users/) 

Incidentally all my encoding (avi to dvd) is done using wine with avisynth / quenc(or cce) / tmpgenc dvdauthor. I have tried for over a year doing the same tasks with Linux apps but I can't get the same speed and quality, which is a shame because I'd love to just use Linux (especially Ubuntu) as all my other tasks are handled without any problems. In fact if I didn't need to convert video I would never touch a Windows app again.

---

### Post by anewguy on 2007-12-29
I have a problem isolating where the problem is coming from because, as I've noted, I have problems with mplayer either not playing and/or skipping and being jumpy.  Can't hardly test the output of a program with it.  This is even after installing the mplayer_fixed package (mplayer and mencode) as noted at the DeVeDe site.  So one way or the other I have to burn it to CD in order to try it on my TV.  Hence the problem - no way to really isolate.  I would strongly suspect it comes from the conversion in kdenlive, as I have seen many other posts on the net with similar problems with it and really not much (at least that I understand) to fix it.

I'm about ready to install wine and try an app in there as mentioned by fiddledd, as I have a lot of time and a lot of patience, but something this fundamental should already have a working solution.  Some have said to try Cinella (sp?), but from what I've read it is nearly impossible to set up and get working, so - does anyone have this working in Gutsy?

Thanks for the help - please keep it coming!:):)

---

### Post by ugm6hr on 2007-12-29
Have you tried playing the video in VLC (in Synaptic)?  Is mplayer jumpy for all videos, or just your personal one?  Do the original video clips jump in mplayer?

Just some thoughts that might help isolate the problem.

If kdenlive is the problem (which is a shame, cos I found it great), these might help:
[http://ubuntuforums.org/showthread.php?t=529759](http://ubuntuforums.org/showthread.php?t=529759)
[http://ubuntuforums.org/showthread.php?t=596160](http://ubuntuforums.org/showthread.php?t=596160)

Just to let you know - I couldn't get cinelerra to work.  It is apparently very good (semi-professional), but has a much steeper learning curve than kdenlive.

---

### Post by anewguy on 2007-12-29
Everything is jumpy/broken in mplayer since I went to Gutsy - I can't even play things like news clicks off of Yahoo!'s main page.  I'll try installing VLC, and I'll go back and recreate everything to see if it makes any difference.  This will all take quite a while so I'll post back later.

Thanks for the help!!:)

---

### Post by Irihapeti on 2007-12-29
> I saw a post that said to enable Gutsy backports in the repository settings, install those versions of Mplayer/Mencoder and then lock the versions of those two packages if you don't want to keep the repository enabled. Again, I've done no video editing in Gutsy to be able to verify this.

I've since done some experimenting, and I can verify that I can use DeVeDe to make both PAL and NTSC vcd files. The Gutsy backport version of Mencoder/Mplayer seems to have fixed the horrible sound problems. The original video files were in PAL; I don't know if that affects anything or not.

---

### Post by anewguy on 2007-12-29
Man, I think I've got even more problems - perhaps they are behind some of this.  A brief background:

I tried installing/using desktop effects but of course my old old OLD cheap video card won't run it (didn't think it would).  using apt-get I remove everything with compiz*.  Well, that made some strange things start happening on my screen so I went back in with synaptic and found a compiz-gnome package I reinstalled and that fixed those problems.  This was AFTER I went to Gutsy but BEFORE I tried anything with video under Gutsy.

With the background in mind, and given my video playback problems, I did try VLC as suggested.  It works okay when in a small screen, but in full screen in jumps.  Then I tried just creating a mpeg from one of my avi) via DeVeDe to my hard disk and tried playing it.  Same thing.  So I tried mplayer - same thing.  Then I tried mplayer via the command line - it aborts out with some message about no default glx xvideo handler on display 0.  So, I tried mplayer again at the command line but added -vo ggi (i.e., the video output is a generic graphics device) and it plays fine - though I can't figure out how to try it in full screen from just mplayer.

So.....what does all of this have to do with my post?  Well, I know glx was what was trying to be used by the failed desktop effects.  I have a feeling somewhere in the system things think they should be using glx (I even took it out of xorg.conf !) and I think that is messing some of this up - especially video playback.  Whether it has something to do with audio delays I'm in the dark.

Soooo......does anyone know enough about desktop effects, it's ties into the various packages, and if my failure and removal of such may have goofed some things up?

I'm at a blank here, and I need this to work in Ubuntu as the only Windows I could fall back to if I had to is an OLD version of Wind98SE on a CD around here somewhere.

Thanks!:)

PS - I tried Viderella and had to put in a link to make it find a gl library, then when it finally was going to start it aborts and gives a crash dump.  This simple task is getting very disheartening.

---

### Post by ugm6hr on 2007-12-30
Honestly, I am not sure about your video problems.

I should have thought about that before too - kdenlive didn't like compiz on my laptop - I had to disable it to render video.

My answer would be to just re-install Ubuntu, cos I've found it a lot faster than trying to correct problems.  But I'm sure someone will be able to help.  Video playback should not be such an issue on any moder-ish computer....

---

### Post by carusoswi on 2007-12-30
Ok, I downloaded Kdenlive.  Finally, a video ap from Linux that installed onto my machine and works.  However, the help files are missing, and I could not even figure out how to do a simple crossfade - should be a fairly intuitive task.

FWIW, I have a lot of experience with top-shelf proprietary audio/video packages on the XP side.  Need for Mutli-media (and the wide gap between XP/Ubuntu functionality in this area) is the major hurdle preventing me from extricating myself from the XP world.

I'm not certain Kdenlive is the answer, but, until I can figure out the simple stuff, I'll never be able to give it a fair evaluation.

Can someone here help?

I have two clips on the timeline, one on track 0, the other on track 1.  I want to cross fade them.  Overlapping doesn't seem to do the trick, clickin on the transition icon, then crossfade icon doesn't seem to work, either.

What am I missing.

Thanks in advance for your assistance.

Caruso

---

### Post by ugm6hr on 2007-12-30
> **carusoswi said:**
> I have two clips on the timeline, one on track 0, the other on track 1.  I want to cross fade them.  Overlapping doesn't seem to do the trick, clickin on the transition icon, then crossfade icon doesn't seem to work, either.

Left-click on the TimeLine just above where you want the transition (not sure if this is necessary - but I like to see the correct image in Monitor).  Then right-click in the white space between Tracks 0 and 1 and select Add Transition->Crossfade.

This will put a little yellow box with arrow in that white space.  You can change the direction of crossfade (although it normally gets this right), and also move the transition, and make its duration longer or shorter.

Now if you move the TimeLine marker left and right, and have the Monitor on TimeLine Monitor, you should see the effect.

If that doesn't make sense - post a screenshot of your kdenlive for me to work out.

This has some helpful videos: [http://www.kdenlive.org/tutorials/](http://www.kdenlive.org/tutorials/)

---

