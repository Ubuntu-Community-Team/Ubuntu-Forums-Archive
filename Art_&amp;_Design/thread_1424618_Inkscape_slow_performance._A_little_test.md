---
title: "Inkscape slow performance. A little test"
date: 2010-03-08
forum: Art &amp; Design
---

### Post by aklo on 2010-03-08
Just wondering is it just me or everyone else.

Why is it so slow to have effects in inkscape. I mean it works fine if there are no other effect in inkscape but a simple blur + zoom = slow.

When i zoom in, inkscape will render the image line by line (slow) . 

I have a dual core 2.66mhz processor, 8800gt graphics card. 
I've research and found that inkscape doesn't use the graphic card to process anything but still a simple effect slows down inkscape. What happens for people doing professional art ? Of course this isn't a big deal since i don't use blur very often but i happened to do a ligtning with some blur to achieve the neon glow effect in inkscape.

For now i can only imagine doing plain image in inkscape then bring it over to gimp for other effects.

I've attached a basic inkscape file which consist of:

1 oval.
1 oval (blurred as drop shadow)
1 smaller oval (for fun)
I group the above 3 image and tilt it a little about 30 degrees.

Just zoom in the image and see if yours zoomed in instantly or does it spend like a few secs drawing the image piece by piece.


[ATTACH]149360[/ATTACH]

edit: i'm sure it is the blur effect which lags.

---

### Post by Newfoundlander on 2010-03-08
The blur does tend to take a bit longer to render on my machine as well.

---

### Post by PC_load_letter on 2010-03-10
yep, it brought my old T43 Pentium-M 1.86Ghz, 1.5G Ram to a crawl I had to xkill Inkscape. Will try it on my better equipped desktop when I get home.

---

### Post by aklo on 2010-03-10
I think a faster comp will also show the same signs. I've read up on other source and they often suggest doing blur on another layer so you can turn it off if you need to zoom in / out or move your images around.

I love using blurs in my inkscape art since blur seems to make images look nicer. I guess i have to make do with keeping blur on a different layer and turning them off if i got to zoom in.

This is what i was doing when i create this thread. As you can see i use blur quite a lot and it brings out the neon/lightning effect but it really is a pain to zoom in.
[http://4seasons.deviantart.com/art/Olympia-156593549](http://4seasons.deviantart.com/art/Olympia-156593549)


I'm using intel core 2 duo E6750 @ 2.66Ghz

---

### Post by bonethug on 2010-03-11
I'm using sometimes Inkscape on my mini book with only 1GB of memory and an integrated graphic card and I have to say the performance is slow too (how would't it be), but I've managed everything with a little bit of patience and the good chi, if you know what I'm talkin about :)

Regards,
bonethug

---

### Post by kayosiii on 2010-03-12
The slow down is proportional to the size of the blur used. Try using a smaller blur radius and dropping the opacity a bit. It tends to look quite similar but not slow down the machine any where near as much.

The other thing you can do if you are pretty sure of your intended output size and resolution is to make a bitmap copy of the blurred object (it's in the edit menu) and hide off the original.

Certainly the workflow could improve - inkscape.org would probably be the best place for discussing that though.

---

### Post by anidsign on 2011-07-07
Hi, i have experienced same "zooming problem" in inkscape. i was working on a huge image with lots of blur and gradients (b/c i love inkscape's real time vector blur very much)and whenever i zoom the image to add some detail, inkscape is hung down and i switched back to the 1:2 zoom level. At last i found a simple solution. 

1. switch to display mode>no filters
2. then zoom the area maximum which you want to see detailed 
3. then switch back to  display mode>normal

it worked for me and i was happy :)

---

