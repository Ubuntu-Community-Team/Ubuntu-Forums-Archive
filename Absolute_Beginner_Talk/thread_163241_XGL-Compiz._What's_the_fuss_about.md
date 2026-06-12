---
title: "XGL-Compiz. What's the fuss about?"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by pbaehr on 2006-04-20
I've been hearing a lot of buzzing about how exciting this whole XGL-Compiz thing so naturally I'm tempted to try it.

Before I go through the rigors of installing it, though, I'd like to know:

What exactly is it?!

I understand it has something to do with the video card handling some sort of 3d processing for the window manager. Or at least, I think I understand that. But I've been doing a lot of reading lately and no one seems to go into WHY I should use it.

Can someone give some specific examples of things that it does which might make me want it?

[P.S. - I really did look long and hard but everything I found was either too technical for me to comprehend or too vague to be useful]

---

### Post by William the Conquerer on 2006-04-20
well ok, so first of all Xgl is in no way some new essential component that everyone needs immediately or anything rediculous like that.  There is a huge amount of hype surrounding it in fact.  BUT, I really, really like it =).  Ok, so you will need to read some of the technical documents to understand it, such as: [http://principe.homelinux.net/](http://principe.homelinux.net/).  BUT a simplified version of it is pretty much that (as I understand it) of course everyone knows that computers these days have typically powerful 3d video cards that can do all sorts of awesome looking 3d effects and blah blah blah all that, BUT they were always just used almost exclusively in video games.  Xgl is kinda a way of using that powerful 3d graphics chip to draw and manipulate your desktop.  It uses something called openGL that has access to the chip instead of software rendering using the systems cpu.  (anyone correct me if I left out anything or missed the target on any points).  So what does all this result in?  A pretty sweet lookin' desktop...  quick rendering of windows and a more physical feel of your desktop.  You can quickly render REAL transparency and have windows that wobble all around the screen when you move them, so on and so on.  Honestly I kinda see it as linux's response to "eyecandy" in vista and os x.  I know I'm biased, but after using all three I think Xgl has some of the most potential... It's highly unstable and there's alot more to it (Xgl replaces the xserver which is usually viewed as flawed in design, etc.)

So anyway, xserver-xgl lets you have that access to the 3d chip on the card.  Compiz is a compisite manager/window manager that USES that access to draw the funky cool effects =).  So anyway hope that helped a little.

---

### Post by pbaehr on 2006-04-20
So does that mean Compiz would replace Gnome? Or am I misunderstanding/misusing the term "window manager"?

Also, thanks for the info. It's very helpful and has made it a lot more clear for me.

---

### Post by pbaehr on 2006-04-20
I guess I should've looked before I asked. I found this on wikipedia.

"Compiz conforms to the ICCCM standard and as such can substitute the default Metacity in GNOME or Kwin in KDE."

But it WAS listed under "window managers" along with Gnome and KDE. Is there some kind of distinction  between primary and secondary window managers I'm unaware of?

---

### Post by Nordoelum on 2006-04-20
[QUOTE=pbaehr]So does that mean Compiz would replace Gnome? Or am I misunderstanding/misusing the term "window manager"?

Also, thanks for the info. It's very helpful and has made it a lot more clear for me.[/QUOTE]
That is how windows behave. Like gloss in Vista, and etc.

---

### Post by Qrk on 2006-04-20
Compiz will replace Metacity, which is Gnome's window manager. You can still switch between the two.

---

### Post by pbaehr on 2006-04-20
Okay, so Metacity is Gnome's Window Manager. Gnome is XWindows DESKTOP ENVIRONMENT. That's where I was getting confused. I had a little term mismatch going on.

---

