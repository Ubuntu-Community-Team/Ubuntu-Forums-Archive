---
title: "Interactive animation on Website"
date: 2012-02-03
forum: Art &amp; Design
---

### Post by Bromden on 2012-02-03
I'm going to put an interactive animation on my website, but actually i don't know wich way follow.
I've created this animation with blender, and i would like to start it with a single click. Actually I think the best way is using Jquery/javascript, I've found these nice scripts:
[http://spritely.net/documentation/](http://spritely.net/documentation/)
[http://crisp.tweakblogs.net/blog/3881/dhtml-lemmings-primer.html](http://crisp.tweakblogs.net/blog/3881/dhtml-lemmings-primer.html)
[http://www.ajaxblender.com/jani.html](http://www.ajaxblender.com/jani.html)

The only problem is that I should load a lot of frames (the animation is long about 10sec.), and it could slow down the site.

Premising I don't want to use Flash, do I have to work with frames and Javascript or is there an alternative?

---

### Post by aasdfasdfg on 2012-02-05
Using jQuery as in those links you pointed out seems like the most elegant solution.

In terms of simplicity, have you considering using animated GIFs? For instance, render the first frame of the animation as one image, then render the entire animation as a GIF. Have an onclick event on the first image that swaps out its location with the second.

How large are the images you are animating? Are you okay with having GIF artifacts?

---

### Post by baerbelschaefer on 2012-02-07
I just want to test this account

---

