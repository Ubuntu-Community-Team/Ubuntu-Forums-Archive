---
title: "Animation Program???"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by insub2 on 2006-12-06
I need to make a film for a class (due next week)...My idea is a stop animation using a potato.


My question to the community is:

Is there a linux program (or a free microsoft program) that will take a collection of photos and turn it into an animation that i can dub and burn to dvd?


Does any one have an idea how to do this?

THANK YOU!!!

---

### Post by richiewrt on 2006-12-06
This may not be exactly what you are looking for, it is a easy 3d object oriented program that you could make a film in. its free so you can check it out. [www.alice.org](www.alice.org) it is pretty neat and really simple to do simple little movies and stuff like that in.

---

### Post by azkehmm on 2006-12-06
A standard video editing program that can integrate still shots into a video should be able to do it. Just cut the time the photo is displayed down to 1 or 2 frames. I believe there's a video editor in the repositories in Ubuntu. Otherwise, Movie Maker should be able to do the trick.

---

### Post by CarpKing on 2006-12-06
You could try the Gimp Animation Package (gimp-gap).  I don't have any experience with most of its features, but I know it can output an avi.  I think you can even tack on a pre-recorded .wav for the sound, but there might be more convenient programs for dubbing.

---

### Post by insub2 on 2006-12-07
Gimp-GAP didn't work for me.  I think i may not have the mpeg2encoder....

but i don't think that will work out because i will be taking photos (camara saves them as .jpg) and if do it gimp style i'd have to ... i don't know what i'd have to do, but it doesn't seem very easy.


i also found out about and tried to no joy ffmpeg, mencoder, and transcode.

i don't know how those work.  i just followed (as best as i could) the instructions in the forums.

I'd really like a program like Stopmotion...but it didn't work.  there was a forum discussion that had no solution to the problem i was having (not exporting.)


to sum up:  nothing i tried produced any .avi or anything.  i might not have the right encoders--i don't know how to get them.  i wish stopmotion worked.  and i'm going to bed.  let me know if you guys have any solutions.  thanks.

---

### Post by uuwatti on 2006-12-07
[http://frameworks.polycrystal.org/](http://frameworks.polycrystal.org/) you might want to try this one similar to stopmotion. Also, did you try both installing stopmotion with aptitude and the deb from their website. 
EDIT: Oops, I didn't notice that there is an I/O error when exporting the film sorry.

---

### Post by insub2 on 2006-12-07
> **uuwatti said:**
> [http://frameworks.polycrystal.org/](http://frameworks.polycrystal.org/) you might want to try this one similar to stopmotion. Also, did you try both installing stopmotion with aptitude and the deb from their website. 
EDIT: Oops, I didn't notice that there is an I/O error when exporting the film sorry.
took a look at that page...doesn't look like it will work for my case because i do not have a vid4lin camera.  I was intending on taking pictures with my digital camara or scanning in drawings.

My troubles (from a very novice viewpoint) seem to be i don't have encoders (i don't really know what an encoder would be...).  If it matters, i'm running dapper.

---

### Post by uuwatti on 2006-12-07
well.. cinelerra and jahshaka can definitely do that. Neither of them are for beginners though. Here's how to install Jahshaka [http://www.jahshaka.org/forum/viewtopic.php?t=1736&highlight=ubuntu](http://www.jahshaka.org/forum/viewtopic.php?t=1736&highlight=ubuntu)
And instructions for cinelerra
[http://www.ubuntuforums.org/showthread.php?t=294007&highlight=howto+cinelerra](http://www.ubuntuforums.org/showthread.php?t=294007&highlight=howto+cinelerra)
Be warned: Jahshaka is pretty awful.

---

### Post by nhandler on 2006-12-08
Here is a simple to use, free, windows animator. You import gif images, and it will put them into an animated gif. You can adjust the delay to your needs.

[http://www.jhepple.com/gif_animator.htm](http://www.jhepple.com/gif_animator.htm)

---

### Post by insub2 on 2006-12-09
> **uuwatti said:**
> well.. cinelerra and jahshaka can definitely do that. Neither of them are for beginners though. Here's how to install Jahshaka [http://www.jahshaka.org/forum/viewtopic.php?t=1736&highlight=ubuntu](http://www.jahshaka.org/forum/viewtopic.php?t=1736&highlight=ubuntu)
And instructions for cinelerra
[http://www.ubuntuforums.org/showthread.php?t=294007&highlight=howto+cinelerra](http://www.ubuntuforums.org/showthread.php?t=294007&highlight=howto+cinelerra)
Be warned: Jahshaka is pretty awful.
I have Cinelerra installed, i'll see what i can manage, thanks.

> **Cheater said:**
> Here is a simple to use, free, windows animator. You import gif images, and it will put them into an animated gif. You can adjust the delay to your needs.

[http://www.jhepple.com/gif_animator.htm](http://www.jhepple.com/gif_animator.htm)

thanks for you assistance but if i just wanted to make an animated gif i would use G.A.P.  i'm looking to make something that i could add sound to and burn to dvd.

---

### Post by muhkayoh on 2006-12-19
fwiw -

I'm also trying to do animation with cinelerra.  I'm using inkscape to draw frames and cinelerra to stitch them together with sound.  I'm a long way from being able to do good animation, but here's a short proof of concept (so to speak) I did last night:

[http://www.sketch.mattjordan.com/2006/12/19/happy-birthday-de/](http://www.sketch.mattjordan.com/2006/12/19/happy-birthday-de/)

I had a fairly frustrating time putting even such a short clip together.  I''d beinterested in hearing how anybody else is succeeding at this sort of thing.  Maybe I'll get it with more study and working out of the kinks.

Matt

---

