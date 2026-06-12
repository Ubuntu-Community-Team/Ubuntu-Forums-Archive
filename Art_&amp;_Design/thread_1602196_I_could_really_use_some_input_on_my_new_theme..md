---
title: "I could really use some input on my new theme."
date: 2010-10-21
forum: Art &amp; Design
---

### Post by SkiesOfAzel on 2010-10-21
After two years on inactivity i got the urge to create something new. It will share some elements with my previous theme (Azel), but it will also look more KDEish, with softer shadows, gradients etc. I haven't skinned everything yet, but you can get a general idea of how it will look [here:]("http://skiesofazel.deviantart.com/art/Work-in-progress-182964856")

  What do you think on the scrollbars? Do they blend well with the rest of the theme, or are they too in your face?

  Thanks in advance.

---

### Post by Anutesyn on 2010-10-24
It's very clean, I like that. It's pretty OSXy, but not in that cheesy way!

---

### Post by Gremlinzzz on 2010-10-24
Not bad sort of like mine
[http://ubuntuforums.org/attachment.php?attachmentid=173403&stc=1&d=1287956206](http://ubuntuforums.org/attachment.php?attachmentid=173403&stc=1&d=1287956206)

---

### Post by DeadSuperHero on 2010-10-24
To be totally honest, the scrollbars remind me a bit of Google Wave's scrollbars. I had always wanted that in a GTK theme, so I say go with it. Well done!

Also, the dark tabs remind me a bit of Bespin. :)

---

### Post by SkiesOfAzel on 2010-10-27
> **DeadSuperHero said:**
> To be totally honest, the scrollbars remind me a bit of Google Wave's scrollbars. I had always wanted that in a GTK theme, so I say go with it. Well done!

Also, the dark tabs remind me a bit of Bespin. :)

  Unfortunately i've changed the scrollbars :P sorry. Although i hadn't seen Google wave or its scrollbars, i did indeed took the tabs style from Bespin.

  The theme has been published [here]("http://skiesofazel.deviantart.com/art/Orta-184118297") btw.

---

### Post by jurialmunkey on 2010-10-27
Full window gradients, buttons and indents/shadows frame borders on notebooks and content etc looks beautiful. Although personally, I think the whole metal-grey-gradient thing is getting really tired fast. 

The tab style is interesting, but I really dislike the white selection circle. It should have the same amount of rounding as the actual tabs, in my eyes. And it looks really ugly when there is a single tab open (I understand this is due to limitations in GTK2).

On the whole, I think the best feature is the indents and shadows on the buttons and entryboxes and frames etc etc. Bordering on perfection in that department. 

Its just such a shame that its a pixmap theme. I wonder how much could be recreated with Murrine, but I suppose that is pointless when the window background has to be a pixmap anyway.

BTW - you got an article feature on [WebUpd8]("http://www.webupd8.org/2010/10/orta-gtk-theme-stylish-theme-based-on.html"). Congrats :D

---

### Post by SkiesOfAzel on 2010-10-28
> **jurialmunkey said:**
> Full window gradients, buttons and indents/shadows frame borders on notebooks and content etc looks beautiful. Although personally, I think the whole metal-grey-gradient thing is getting really tired fast. 

The tab style is interesting, but I really dislike the white selection circle. It should have the same amount of rounding as the actual tabs, in my eyes. And it looks really ugly when there is a single tab open (I understand this is due to limitations in GTK2).

On the whole, I think the best feature is the indents and shadows on the buttons and entryboxes and frames etc etc. Bordering on perfection in that department. 

Its just such a shame that its a pixmap theme. I wonder how much could be recreated with Murrine, but I suppose that is pointless when the window background has to be a pixmap anyway.

BTW - you got an article feature on [WebUpd8]("http://www.webupd8.org/2010/10/orta-gtk-theme-stylish-theme-based-on.html"). Congrats :D

  Thanks you for your kind words!

About the metal look:
 I like the silver/dark combination, i've always liked it since i first saw it used effectively on a game series ([Panzer Dragoon]("art.thewilloftheancients.com")) back when i was 15, and that's the art style that has influenced me the most in my works. This is a personal preference and won't change soon :P.

About the pixmap engine:
  Because i realize that not everyone has the same color preferences as me, this time instead of using my own code, i started by modifying Elementary with the purpose to use the murrine engine instead of the pixmap engine. To answer another question of yours, it's just not possible to achieve shadows like the ones you see on Orta with murrine or any other cairo engine. It's not just the engines fault, gtk2 was just not build with things like that in mind. The same goes for full window or any kind of gradient for that matter. Allot of widgets paint their own background, creating a visual mess. Still, i used transparent pixmaps in order to allow some color tweaking, but if you go too far it will look ugly, since transparency or no transparency they are still pixmaps ;).

  About the tabs:
As you already said yourself, gtk is the most limiting factor in this regard. I do intend to offer alternatives in the future though (different gradients to choose from, different tab styles, different scrollbar sizes, panel color etc), i just don't have the time right now to complete it according to my initial vision. These thing will probably land sometime in the future, and recommendations like yours really help me in order to make it better.

  About the WebUpd8 post:
It feels a little surreal and is kind of unexpected that my theme managed to gather so much attention in such a short time. It's very rewarding though, as i put every second of my spare time for the last month on this project. What bothers me a little is the part about being inspired by Elementary in the Blogger's description. Elementary is certainly the most successful gnome theme out there, but not every other theme tries to look like it or even compete with it for that matter. If the Blogger had bothered looking on my previous works (which by the way are allot older than Elementary) he would see where i get my influences from.

Cya!

---

