---
title: "First time lapse"
date: 2014-10-20
forum: Art &amp; Design
---

### Post by guine on 2014-10-20
I just wanted to share my first attempt at a time lapse video that I shot over the summer at Sequoia National Park in California.

[https://vimeo.com/109294029](https://vimeo.com/109294029)

I used RawTherapee and Gimp for photo editing, then used avconv to put each individual sequence together and then used OpenShot to combine all the sequences into one video.

---

### Post by JazzPotato on 2014-10-22
That's pretty awesome, well done! I'm interested, what framerate did the photos end up being displayed at?

---

### Post by guine on 2014-10-22
Thanks, I ended up using 25 fps since that was one of the options that openshot wanted to use for saving.  I didn't look around too much to see if there was a was to save it in the 24 fps that I originally did for each segment.

---

### Post by tgalati4 on 2014-10-23
Impressive.  How about reading a poem or a John Muir passage as a voice-over?

---

### Post by hg-knight on 2014-11-03
Very good,
 some shots better than others, i.e the clouds / sunset.
impressed with how to did it

---

### Post by lisati on 2014-11-03
Well done!

---

### Post by shuichi on 2014-11-22
Nice! im interested into time lapses, even if have not a good equipment for it yet, was checking for this avconv, need to ask you how did you used, cant get it yet! thanks!

---

### Post by coldraven on 2014-11-22
Very well done! I liked the soundtrack but at one point a thought that a ship was going to appear, I don't suppose you get many of those in that park :)
I'd like to try time-lapse myself one day.

---

### Post by guine on 2014-11-25
> **shuichi said:**
> Nice! im interested into time lapses, even if have not a good equipment for it yet, was checking for this avconv, need to ask you how did you used, cant get it yet! thanks!

This is the command that I was able to get to work with avconv  ```
avconv -f image2 -i DSC_%04d.JPG -r 25 -s hd1080 test.mp4
```

You will need to replace DSC_%04d.JPG with whatever format your camera uses to name its files and the files will need to be in numerical order starting at 1.
Changing the -r number will change the framerate and -s lets you set the size.

Unfortunately avconv, like ffmpeg, seems to be very termperamental so I can't guarantee this command will work for other people(if you do a google search there are plenty of pages where people are giving different commands for both programs saying this was the only way they were able to get the program to work and couldn't figure out why the commands that other people had success with didn't work for them).  Good luck

---

### Post by shuichi on 2014-11-26
> **guine said:**
> This is the command that I was able to get to work with avconv  ```
avconv -f image2 -i DSC_%04d.JPG -r 25 -s hd1080 test.mp4
```

You will need to replace DSC_%04d.JPG with whatever format your camera uses to name its files and the files will need to be in numerical order starting at 1.
Changing the -r number will change the framerate and -s lets you set the size.

Unfortunately avconv, like ffmpeg, seems to be very termperamental so I can't guarantee this command will work for other people(if you do a google search there are plenty of pages where people are giving different commands for both programs saying this was the only way they were able to get the program to work and couldn't figure out why the commands that other people had success with didn't work for them).  Good luck

Thank you very much! now is my time to try!!

---

### Post by shuichi on 2014-11-28
failed to install avconv... wonder if somebody else with lubuntu experienced the same (sorry to disturb the thread)

---

### Post by Bandit on 2015-01-17
> **guine said:**
> I just wanted to share my first attempt at a time lapse video that I shot over the summer at Sequoia National Park in California.

[https://vimeo.com/109294029](https://vimeo.com/109294029)

I used RawTherapee and Gimp for photo editing, then used avconv to put each individual sequence together and then used OpenShot to combine all the sequences into one video.

Very nice, congrats..

---

### Post by Super-Wisdom on 2015-01-19
Very good! I bet your proud of your work. Good choice of background music.

---

### Post by john387 on 2015-03-23
nice one.....impressive!

---

### Post by stephen_ward on 2015-03-23
Looks great! Well done!!!!

---

### Post by kurja on 2015-04-17
I tried to make a time lapse this winter, had never tried it before from a series of photos. I had made some simple animations with gimp though. I couldn't get the obvious cli offerings to work, but luckily there are gui alternatives in software center. Here's the video: [https://vimeo.com/122651015](https://vimeo.com/122651015)

---

### Post by sudodus on 2015-04-17
Nice video-clips :KS

---

