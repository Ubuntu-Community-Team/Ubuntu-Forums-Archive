---
title: "Nautilus annoyances"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by hackle577 on 2007-05-07
I'm having several problems with Nautilus. They aren't too serious, but are really annoying, so I'm hoping someone has some solutions. I'm running a fully updated Feisty install.

1- Nautilus will not preview my some of my files correctly. I have several videos in ~/vids, ranging in size from  92MB to 177MB. Some of them are previewed and some aren't. My preview settings ("Other Previewable Files") are for local files only under 10MB in size. However, *all* of the videos are over 10MB and some are being previewed and others are not.

I tried "cd vids" then "touch * " in terminal and Nautilus re-thumbnailed all the videos. Now, only one video is not previewed. But it is 137MB is size. Weird. Shouldn't Nautilus not preview *any* of them?

2- My attempts to control-click multiple items to select them is not working. Control-clicking and holding moves the window, but control-clicking items doesn't select multiple items anymore. I think this has to do with problem #3.

3- I'm trying to install the [nautilus-wallpaper extension]("http://battleaxe.net/projects/nautilus-wallpaper/"). After extracting it, I try to run "./configure --prefix=/usr" but it stops and gives me this error:

```
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
```

Is there a way to fix this, or some other way I can add the "Set as wallpaper" functionality? Also, I didn't notice that control-click was malfunctioning until after I tried to install this script. Could that maybe be the cause of problem #2?

Thanks for your help!

---

### Post by fakie_flip on 2007-05-07
sudo apt-get install build-essential

---

### Post by hackle577 on 2007-05-07
Problem #3 solved! Thanks!

PS- Problem #2 still exists BTW.

---

### Post by fakie_flip on 2007-05-07
Holding alt click is what moves windows for me. I don't know how you did it with control+click.

---

### Post by fakie_flip on 2007-05-07
Open nautilus. Click on Edit>Preferences. Then click on the Preview tab. Change "Only for files smaller than: " to whatever you like. Let me know if this helps.

---

### Post by hackle577 on 2007-05-07
Changing the preview threshold to 5MB did nothing different, even after "touch * "

Changing the preview threshold to 100MB then "touch * " previewed all but two files (125MB and 137MB in size).

Hmm...

---

### Post by hackle577 on 2007-05-08
Bumpity bump. Help would be *greatly* appreciated. :-)

---

### Post by SeanHodges on 2007-05-08
I've had problem 2 before, its because the Ctrl key is assigned to both multiple selecting AND window movement.

System->Preferences->Windows

Change the movement key from "Control" to "Alt"...

My guess is that at some point you may have changed this value and not noticed the side-effect till now. This will return the behaviour to the default.

---

### Post by SeanHodges on 2007-05-08
Also, are the files that are not being previewed always the same, even after a touch?

I suspect it might be a codec thing, try looking at the Audio/Video tab in the Properties of one of the files not previewing, and compare the reported codec against some of the videos that ARE previewing.

I dont have a solution right now if that is the case, but at least it might explain what is going on...

---

### Post by hackle577 on 2007-05-08
Yay! Problem #2 fixed! Thanks!

The codecs for all of the videos are the same: Microsoft Windows Media 9.

---

### Post by fakie_flip on 2007-05-08
You should create seperate threads for each problem. You'll get more help that way. What problem do you have left?

---

### Post by hackle577 on 2007-05-08
New thread: [http://ubuntuforums.org/showthread.php?t=437147](http://ubuntuforums.org/showthread.php?t=437147)

---

### Post by fakie_flip on 2007-05-08
Did you create the vids from Devede?

---

### Post by hackle577 on 2007-05-08
No.

---

