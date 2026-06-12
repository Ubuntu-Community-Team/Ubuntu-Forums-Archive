---
title: "[SOLVED] divx to dvd?"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by tjwoosta on 2008-02-17
i have been trying to find a way to convert divx to dvd but so far i have been unsuccessful.
I have found devede but it always makes little purple lines go horizontally across the picture

So is there any other way i can convert divx to dvd  and maybe have a menu?

---

### Post by julian67 on 2008-02-17
you can do this with tovid, iir it's available from the repos

---

### Post by nonewmsgs on 2008-02-17
ntsc-> ntsc or are you also mixing pl with that.

purple lines might  be the result of that shift.  really you are converting mp4 to mp2 and that transcoding isn't ideal.

---

### Post by tjwoosta on 2008-02-17
how do i get tovid ?  i looked in synaptec but i couldn't find it 
I also tried sudo apt-get install tovid

also what is ntsc-> ntsc  what does that mean?

---

### Post by bumanie on 2008-02-17
I was going to suggest devede, but you have found that unsuccessful. Did you download it from the repo's, raftersoft or getdeb. I usually use the getdeb version and have found it fine (make sure you have the medibuntu repository enabled to get the 3.6 version). There are two main transmission formats for tv pictures. Ntsc is used primarily in the US and Japan, whereas PAL is used in Europe, Australia and most of Asia. So which output format you choose depends on where you live.

---

### Post by julian67 on 2008-02-17
> **tjwoosta said:**
> how do i get tovid ?  i looked in synaptec but i couldn't find it 
I also tried sudo apt-get install tovid

also what is ntsc-> ntsc  what does that mean?

you're right, it isn't in the repos, but you can get it from getdeb.net

---

### Post by sleepingdragon on 2008-02-17
Here's some tricks to remove the purple lines from DeVeDe.

Firstly, ensure the frame rate of the film is correct. 25fps for PAL, 29.97fps for NTSC and 23.976fps for FILM. Try using Avidemux to convert.

When you add a film in DeVeDe, you should see the "Advanced Options" tab at the bottom of the file properties page. Click on this and some more options should be made available.

On the advanced options, make sure the tick is removed from the "Use 16:9 aspect ratio for output". Under the "Quality Options" tab, remove the tick from the "Use Trellis Searched Quantization" and click on the "Use MBCMP" option in the Macroblock section. Playing around with the Linear Blend options can also help, but I rarely use them.

I've found this combo removes the purple lines in most cases, but you should also try playing around with the options mentioned above until the lines disappear. The preview option in DeVeDe will help determine the effects before wasting time with the whole thing.

If you can get away with not having the Trellis and Macroblock options selected, you'll find the conversion time is reduced by about half.

---

### Post by tjwoosta on 2008-02-17
> julian67: you're right, it isn't in the repos, but you can get it from getdeb.net

i also can't find it here

> sleepingdragon:
Here's some tricks to remove the purple lines from DeVeDe.

Firstly, ensure the frame rate of the film is correct. 25fps for PAL, 29.97fps for NTSC and 23.976fps for FILM. Try using Avidemux to convert.

When you add a film in DeVeDe, you should see the "Advanced Options" tab at the bottom of the file properties page. Click on this and some more options should be made available.

On the advanced options, make sure the tick is removed from the "Use 16:9 aspect ratio for output". Under the "Quality Options" tab, remove the tick from the "Use Trellis Searched Quantization" and click on the "Use MBCMP" option in the Macroblock section. Playing around with the Linear Blend options can also help, but I rarely use them.

I've found this combo removes the purple lines in most cases, but you should also try playing around with the options mentioned above until the lines disappear. The preview option in DeVeDe will help determine the effects before wasting time with the whole thing.

If you can get away with not having the Trellis and Macroblock options selected, you'll find the conversion time is reduced by about half. 

thanks i will try to do this but it will take a while because i cannot watch the preview because i cant get any video players to work on my computer, I have tried mplayer, vlc, and totem but as soon as i click play everything disapears

---

### Post by julian67 on 2008-02-17
> **tjwoosta said:**
> i also can't find it here

you can use the feisty package, it works fine in gutsy

---

### Post by tjwoosta on 2008-02-17
i did what sleeping dragon said and it worked for me so thank you guys for all  your help.

---

