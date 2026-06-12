---
title: "Blender into web whitout flash?"
date: 2010-01-29
forum: Art &amp; Design
---

### Post by c001os on 2010-01-29
Hey guys! 

My question is: when i made a video with blender and i want it to build into a webpage, how can i do this in ubuntu whitout  flash? Is there any flash replacement solution (graphical)?? :?: I dont want to  use in my workflow a cracked application!

Thx for the help!

---

### Post by durand on 2010-01-29
You can convert the video into an flv and use a flash video player.
[http://snipplr.com/view/288/flash-video-player-html-code/](http://snipplr.com/view/288/flash-video-player-html-code/)

---

### Post by Psumi on 2010-01-30
> **durand said:**
> You can convert the video into an flv and use a flash video player.
[http://snipplr.com/view/288/flash-video-player-html-code/](http://snipplr.com/view/288/flash-video-player-html-code/)

What about converting it to MP4 or OGG and using HTML5? :|

---

### Post by durand on 2010-01-30
> **Psumi said:**
> What about converting it to MP4 or OGG and using HTML5? :|

Probably a better method, shame that it isn't supported by some browsers :(

---

### Post by mcduck on 2010-01-30
> **Psumi said:**
> What about converting it to MP4 or OGG and using HTML5? :|

That takes kind of lots of work if you want it to work for everybody, since you'd need *both* OGG and H.264 versions of the video, and then some script or other way to serve them based on the browser used. Otherwise you simply can't make the video work for everybody.

I'd say converting to .flv and then using some flash-based player is still the most compatible way. There are many flash-based video players available that don't actually require you to do any work with Adobe Flash, but instead accept all configurations directly from HTML tags or Javascript..

---

### Post by Psumi on 2010-01-30
> **mcduck said:**
> I'd say converting to .flv and then using some flash-based player is still the most compatible way. There are many flash-based video players available that don't actually require you to do any work with Adobe Flash, but instead accept all configurations directly from HTML tags or Javascript..

Flash without flash or even a embedded player that utilizes an installed program on your OS (IE: GMplayer)?

Do tell! Or... link.

---

### Post by mcduck on 2010-01-30
[Flowplayer]("http://flowplayer.org/"), for example. I've seen others but I kind of like the configurability of this one.

You simply put the included flash and script files to somewhere on your server, link the script to the page and after that all the configuration can be done in your page's code without having to even touch Flash. :)

---

### Post by Psumi on 2010-01-30
> **mcduck said:**
> [Flowplayer]("http://flowplayer.org/"), for example. I've seen others but I kind of like the configurability of this one.

*golfclap* I get the following error when trying to play their front page video in midori:

> Error - [http://e1h13.simplecdn.net/flowplayer/flowplayer.flv?](http://e1h13.simplecdn.net/flowplayer/flowplayer.flv?)

The page 'http://e1h13.simplecdn.net/flowplayer/flowplayer.flv?' couldn't be loaded.

Plugin will handle load

---

### Post by mcduck on 2010-01-30
Since I have nothing to do with that project I'm not the right person to say anything about your problem, but it definitely works fine on every browser I have available. (IE6,7 & 8, Safari, Epiphany, Opera and Firefox). Perhaps some issue with your connection or soemthing else like that?

Anyway, that was just a suggestion and like I said, I've seen numerous other players more or less like this one, so feel free to find another one if you want to. :)

---

### Post by hessiess on 2010-01-31
Im also using flowplayer on my website and its worked fine for me.

---

### Post by c001os on 2010-02-01
I need to add this video some interactivity (texts, and click-able buttons). Some idea for that? (adobe flash is forbidden :) )

---

### Post by durand on 2010-02-01
Thats possible with svg and javascript. You'll need to look up the details though because I don't know much about it.

---

### Post by c001os on 2010-02-01
Thx, that looks good. I will investigate and post the result as soon i can. ;)

---

### Post by 23dornot23d on 2010-02-02
> **hessiess said:**
> Im also using flowplayer on my website and its worked fine for me.


I like your work and the  links .... great work .... and the flowplayer works great ....... 

cheers ..... nice animation .........

[http://www.hessiess.com/portfolio_reel.php](http://www.hessiess.com/portfolio_reel.php)

will investigate .... ;)

---

### Post by Mustache Villain on 2010-02-04
I suggest going with Therora/OGG with the [Cortado]("http://www.theora.org/cortado/") Java fallback player for browsers that don't support HTML5. Stay free, and try to minimize dependency on Flash.

---

