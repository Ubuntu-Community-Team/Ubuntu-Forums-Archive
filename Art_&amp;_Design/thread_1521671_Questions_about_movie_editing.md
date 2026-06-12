---
title: "Questions about movie editing"
date: 2010-07-01
forum: Art &amp; Design
---

### Post by Sockerdrickan on 2010-07-01
[IMG]http://img200.imageshack.us/img200/1209/viktora.png[/IMG]

Hi! I have a few questions.

I am going to produce an animated series with the images being drawn in the gimp and exported as png's. I was thinking a resolution of 1280x720. The series will be on youtube but I want to be able to (in the future) "port" it to dvd or blu-ray or whatever. Just for safeness.

What is the industry frame rate standard? 24 or 30 fps?

The editor needs to be able to handle a lot of png's and I have 4gb ram. I was thinking maybe 15 minutes max per episode.

I researched several editors and I found OpenShot to be looking good, is it the best way to go for my kind of work?

One problem I'm facing is that since I will be having a lot of separate frames, a transition effect span over 2 frames. How would I do if I wanted it do span over several seconds?

:guitar:

---

### Post by Thryn on 2010-07-08
As to framerate... it's complicated. You see, (older) TVs don't draw a full frame each time, but half a frame, alternating lines. This is known as a 'field'. And LCD screens don't work this way, which is why, when playing a DVD on your computer or an LCD TV, you have to deinterlace it, so that it draws full frames. Otherwise you get weird horizontal lines when the fields are different.

Then there's PAL vs NTSC. PAL (Europe etc.) is 25 frames per second, 50 fields per second. NTSC (US, Canada, Japan...) is 29.97 frames per second, 59.94 fields per second. Then film is 24 frames per second. There are of course conversion processes available, which is how we can watch European shows in the US and movies on our TVs (for example).

Unfortunately I don't know anything about editing video on Ubuntu - I was into making music videos back before I had my own computer, and I was therefore stuck on XP at the time.

---

### Post by Sockerdrickan on 2010-07-08
> **Thryn said:**
> As to framerate... it's complicated. You see, (older) TVs don't draw a full frame each time, but half a frame, alternating lines. This is known as a 'field'. And LCD screens don't work this way, which is why, when playing a DVD on your computer or an LCD TV, you have to deinterlace it, so that it draws full frames. Otherwise you get weird horizontal lines when the fields are different.

Then there's PAL vs NTSC. PAL (Europe etc.) is 25 frames per second, 50 fields per second. NTSC (US, Canada, Japan...) is 29.97 frames per second, 59.94 fields per second. Then film is 24 frames per second. There are of course conversion processes available, which is how we can watch European shows in the US and movies on our TVs (for example).

Unfortunately I don't know anything about editing video on Ubuntu - I was into making music videos back before I had my own computer, and I was therefore stuck on XP at the time.
Okay thanks. So if I'm drawing at 24fps I should be ok with conversion to any regional format?

---

### Post by mcduck on 2010-07-09
PAL, NTSC and interlacing are really SD standards, and haven't got anything to do with HD material. So if you plan making your video in 1280x720 then you'll definitely want to make your video using progressive scan instead of interlaced scan. This also helps if you need to convert the video to different framerates, and also makes editing it a lot cleaner.

The 720p standard allows for 24, 25, 30, 50  or 60 frames per second. The 25 and 30 fps options are pretty much just a reminder from the SD standards, so you should ignore them. Also any TV capable of doing 720P will also be able to handle 60fps, so you are left with two options, 24 fps (the movie industry standard) and 60fps (the best possible termporal definition).

And since it's animation you are making, doing 60fps for the perfectly-smooth movement would be a lot of work for something most people aren't really even expecting from a hand-drawn animation. So I recommend going for 24 frames per second. Of course many HDTV's lack native support for 24fps, but it converts reasonably well to other speeds as you can see from any DVD or blu-ray movie you watch.

What comes to programs, instead of going for some video editor you might also want to consider some software that's intended for 2D animations. Like [Pencil]("http://www.pencil-animation.org/") or [Synfig Studio]("http://www.synfig.org/") (although the latter is mainly for vector-based animation).

Also if you already have drawn the images for every individual frames you don't really need a video editor to combine them into animation, you could do that directly with ffmpeg, mplayer, vlc or any other command-line capable video tool. This way you wouldn't have to worry about memory requirements and such things..

(to sum it up, what I'd do is a 720p24 video file, created directly from the drawn image files with ffmpeg. That would give a good quality video file that could then easily be converted into a Blu-ray, or some lower quality format like DVD or web video. Remember, you'll never be able to convert the video you made to better quality, it only works the other way.. So it's a good idea to make the original version as good quality as you reasonably can.)

---

### Post by Sockerdrickan on 2010-07-10
> **mcduck said:**
> PAL, NTSC and interlacing are really SD standards, and haven't got anything to do with HD material. So if you plan making your video in 1280x720 then you'll definitely want to make your video using progressive scan instead of interlaced scan. This also helps if you need to convert the video to different framerates, and also makes editing it a lot cleaner.

The 720p standard allows for 24, 25, 30, 50  or 60 frames per second. The 25 and 30 fps options are pretty much just a reminder from the SD standards, so you should ignore them. Also any TV capable of doing 720P will also be able to handle 60fps, so you are left with two options, 24 fps (the movie industry standard) and 60fps (the best possible termporal definition).

And since it's animation you are making, doing 60fps for the perfectly-smooth movement would be a lot of work for something most people aren't really even expecting from a hand-drawn animation. So I recommend going for 24 frames per second. Of course many HDTV's lack native support for 24fps, but it converts reasonably well to other speeds as you can see from any DVD or blu-ray movie you watch.

What comes to programs, instead of going for some video editor you might also want to consider some software that's intended for 2D animations. Like [Pencil]("http://www.pencil-animation.org/") or [Synfig Studio]("http://www.synfig.org/") (although the latter is mainly for vector-based animation).

Also if you already have drawn the images for every individual frames you don't really need a video editor to combine them into animation, you could do that directly with ffmpeg, mplayer, vlc or any other command-line capable video tool. This way you wouldn't have to worry about memory requirements and such things..

(to sum it up, what I'd do is a 720p24 video file, created directly from the drawn image files with ffmpeg. That would give a good quality video file that could then easily be converted into a Blu-ray, or some lower quality format like DVD or web video. Remember, you'll never be able to convert the video you made to better quality, it only works the other way.. So it's a good idea to make the original version as good quality as you reasonably can.)
Thank you for explaining. I have two more questions now. I am still planning on using Gimp.

Is there a good source of how to use VLC to encode a video from a series of images?
What is the best way of syncing the audio track as I am drawing the matching images? (basically how do "debug" my drawing without having to encode the movie for every frame and check it out)

---

### Post by d3v1150m471c on 2010-07-10
you mean something like this? [http://www.youtube.com/watch?v=-XccUMOQ978](http://www.youtube.com/watch?v=-XccUMOQ978)

...because that would be awesome

---

### Post by mcduck on 2010-07-10
> **Sockerdrickan said:**
> Thank you for explaining. I have two more questions now. I am still planning on using Gimp.

Is there a good source of how to use VLC to encode a video from a series of images?
What is the best way of syncing the audio track as I am drawing the matching images? (basically how do "debug" my drawing without having to encode the movie for every frame and check it out)

I didn't actually mean replacing Gimp with something else, but instead replacing OpenShot, at least for the part of converting your images into video. Draw allows you to import your own images, so you could still do the drawing in Gimp and then just use Draw to animate them.

For the VLC part, even though I'm quite sure it can do that I couldn't find a guide for it. But here's one for ffmpeg: [http://electron.mit.edu/~gsteele/ffmpeg/]("http://electron.mit.edu/~gsteele/ffmpeg/")

For the audio part, that pretty much depends how you plan making your audio. For lip-syncing the animation to already-recorder speech you might actually want to do what traditional animators do, grab a sheet of paper and a stopwatch, listen to the speech track and make a table of the accurate timings for for each letter in the speech. That will give you all the information you need when drawing the images and animating them, and they should sync pretty well with the speech when you combine the video and sound afterwards.

Then just add soundtrack and other audio effects as their own audio tracks. Any decent video editor should allow you to use multiple audio tracks for your video, so you can adjust the audio timings of each sound/song/spoken part separately to fit the video and you don't need to adjust the animation itself.

Another option is of course to forget about simple video editors and go for some more hard-core application. They will usually allow you to import your images, animate them, create effects and add multiple audio tracks. Of course you'll need to spend some time learning the program itself first. Blender, for example, allows you to do all that, and some additional post processing and compositing as well, but I must admit that the NLE video editor in Blender isn't the easiest one to use. But if you want to give it a try you'll find great tutorials from the web.

---

### Post by Sockerdrickan on 2010-07-10
Thanks for hinting **ffmpeg**, I checked it out and I now got this command line:
```
ffmpeg -alang swe -r 24 -i %d.png -i audio.flac -acodec flac -vcodec libx264 -vpre lossless_max out.mkv #-vlang swe
```Which takes all numbered PNG files in the current directory + audio.flac and creates a Matroska container with the avc1/flac data. No need for OpenShot anymore.

I do have two problems with this command line.

*The actual framerate is reported as 48 by VLC even though I set -r 24 in ffmpeg (reported as 24 when I set it to 12). Is this relevant to some interlacing perhaps? Or maybe ffmpeg/x264 being buggy?
*The -vlang argument doesn't work, at least with ffmpeg 0.5.1 from Ubuntu repositories, so I get an undefined video language. Might be fixed in Ubuntu 10.10?

Oh, and I also looked at Blender´s capabilities. I have used Blender myself several times for creating 3d models but I never looked at its other capabilities. It looks good for serious work with movies but frankly I am planning on doing the fading effects and such manually. So I don't think I need Blender as a dependency for **this** project.

Again thanks for hinting ffmpeg it looks like what I was really after.

---

