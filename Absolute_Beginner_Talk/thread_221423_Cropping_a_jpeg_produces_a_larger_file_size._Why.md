---
title: "Cropping a jpeg produces a larger file size. Why?"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by hanzj on 2006-07-23
Using gThumb to crop the pictures that I've downloaded from my digital camera. The cropped jpeg has a file size larger than the original jpeg. It doesn't make sense to me.

In the save settings, I have 100% Quality and 0% smoothing.

Regardless whether Progressive or Optimize is selected, the resulting files are still bigger.

---

### Post by woedend on 2006-07-23
is your camera saving them as jpg also?  If so, it obviously isnt saving them at 100% quality.  weird eh?  If you take a picture, open it, then save it as 100% quality, it is very likely it will be larger than the original while not of better quality.  Think of it as ripping a song off of a cd to 128 kbps, then you reencoding it at 320 kbps and wondering why its larger.

---

### Post by hanzj on 2006-07-23
Yes, camera is saving them as jpg, too.

I noticed that when I dropped down the Quality Percentage a notch, to around 93%, I get a file size which seems more common sense with the file size.

But I still don't get why saving at 100% quality adds a bigger file size.

---

### Post by woedend on 2006-07-23
sorry, i edited my post to include more info.  let me know if that doesnt help.

---

### Post by hanzj on 2006-07-23
So based on what you've said, seems like the issue is not with my digital camera, but with the photo software, which is gThumb, in my case.

I'm wondering if all other photo-editing software will produce tha same results, though.

---

### Post by woedend on 2006-07-23
well...both really.  When you go to save the file, its making a whole new file and needs a quality number to use.  Jpg is like the mp3 of pictures you could say.  Lets say you camera was saving them at a very high bitrate(256 kbps).   You open it, take off a bit, then resave it using 100% quality.  This doesn't mean use the original quality, it means resave the file using perfect quality(320 kbps).  So even though you may have a removed a piece, you are making it larger by using a different quality rate.  Er this doesnt make much sense and I apologize.  But in short, there may be a setting in your camera to use highest quality(youll have to check, mine has this)...yet its a limitation of the software that you cant just crop and save the existing file as is.
But I have to get to work and back before I fall asleep..hopefully someone else can clear it up if you need take care friend.

---

### Post by hanzj on 2006-07-23
> **woedend said:**
>  yet its a limitation of the software that you cant just crop and save the existing file as is.


Is it a limitation, or is it the way jpeg format work? If it's a limitation, it would be nice if the developers of the software (and/or JPEG algorithm)  should fix this bug.

---

### Post by hanzj on 2006-07-23
> **woedend said:**
> is your camera saving them as jpg also?  If so, it obviously isnt saving them at 100% quality.

My camera is Canon PowerShot SD100. Would anyone know if the camera isn't saving at 100% quality? All I know is that I can choose the resolution (sharp or fuzzy, or middle-of-the-road) and the imagedimensions. I haven't seen an option for jpeg quality, unless Resolution and Quality are the same thing. If so, I choose the highest resolution.

---

### Post by jjstwerff on 2006-07-23
The extra size is just the way JPEG works. The camera probably saved it originally at 95% quality so the 100% is bigger.

The program has to unpack the JPEG to show and change it and repack it into JPEG on saving. So 100% means no loss of quality after the last change.

---

### Post by hanzj on 2006-07-23
So, any successive saves of the jpeg would not show an increase  in filesize, I suppose.

---

