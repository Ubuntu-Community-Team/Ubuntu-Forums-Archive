---
title: "Looking for &quot;Debian Free&quot; Tiling Textures"
date: 2008-03-14
forum: Art &amp; Design
---

### Post by calimer on 2008-03-14
Hi, I'm currently working on a game project that I'm trying to get into Edubuntu and all the content needs to be "Debian Free" where it can be used for any purpose, even commercial with Creative Commons BY SA being the most restrictive license that can be on it.  I was wondering if any of you know any good places for me to get textures that would meet those restrictions.  I'm especially looking for some nice nature ones like textures for grass/ground and also stuff that would be nice for caves and such.  Any help would be greatly appreciated.  Thanks for your time!
-mike

---

### Post by dmn_clown on 2008-03-14
Make your own, these three sites license their photostock free for personal and commercial use, so derivative artwork can be dfsg-free:
[http://www.imageafter.com](http://www.imageafter.com)
[http://www.textureking.com](http://www.textureking.com)
[http://www.cgtextures.com](http://www.cgtextures.com)

---

### Post by calimer on 2008-03-14
Thanks so much!!  Those look like some great sites.  For anyone that is interested in this thread, I found a gimp plugin that makes textures tileable and seamless and some other cool things:
[http://registry.gimp.org/node/77](http://registry.gimp.org/node/77)

Thanks again for your help, take care.
-calimer

---

### Post by dmn_clown on 2008-03-15
> **calimer said:**
>  I found a gimp plugin that makes textures tileable and seamless

I don't suggest using plugins to make tileable images, ctrl+shift+o to offset the edges to the center and then a combination of the healing brush, clone brush, and the blur tool to make the edges disappear.

You can also duplicate the layer twice, flip one horizontally one vertically, and use varying levels of transparency to achieve a seamless tile.

(the seamless plugins will often give you an ugly diamond pattern in the texture)

---

### Post by calimer on 2008-03-15
Thanks for the heads up.  I think I found a tutorial that is similar to what you are talking about:
[http://highpoly3d.com/writer/tutorials/tileable/seamless.htm](http://highpoly3d.com/writer/tutorials/tileable/seamless.htm)

Take care.
-mike

---

### Post by H264 on 2008-03-17
> **dmn_clown said:**
> 
You can also duplicate the layer twice, flip one horizontally one vertically, and use varying levels of transparency to achieve a seamless tile.


You stole my idea you (insert word)... lol.. I was thinking about how to make a program that would make a slightly different tile every time I run the program. One morning just as I was waking up the idea hit me, I then went and figured out how to use cairo in C and me the program :)

[http://pastebin.com/m4ceacee9](http://pastebin.com/m4ceacee9)

but enh... just solid black lines for a website background looks... bad. So I added some imagmagick commands to pretty up the tile...
> 
./test
convert -blur 0x4 -edge 15 -fx G -shade 120x45 -fill black -colorize 50% tile.png -quality 90 tile2.jpeg


Really tile2.jpeg did not turn out too bad for a website... still a little rough looking, but a good start.

---

