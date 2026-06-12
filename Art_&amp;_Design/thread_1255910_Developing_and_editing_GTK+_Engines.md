---
title: "Developing and editing GTK+ Engines"
date: 2009-09-02
forum: Art &amp; Design
---

### Post by wersdaluv on 2009-09-02
I am in love with the look of Aurora but it has some bugs that make me go back to Clearlooks, an established standard. Many prefer Murrine because of its options, constant development and popularity. However, I think that it's gradients need to be much deeper. Clearlooks has deeper gradients than Murrine, while Aurora has deeper gradients than the two mentioned.

I want to edit Clearlooks or Aurora to have an engine that combines the conservative features of Clearlooks and the modern features of Aurora. So far, the things I don't like about Aurora are the arrows, scrollbars, and the text of inactive menus on Firefox. I am not sure about Aurora's development so I'll just fork Clearlooks (or Murrine if it would work) to apply deep gradients so it would look like Aurora's.

I considered simply making a gtk theme that uses both engines but that may not work because I want a very consistent look. Arrows and other elements should be consistent in every widget.

Where do I start? I'm new to this and I do not know much about editing/developing GTK+ engines.

---

### Post by xl_cheese on 2009-09-02
Do what I did.

I took the clearlooks engine and made my own version.  I wanted to have a smooth gradient that merged the menubar and toolbar.  I also did a bunch of other little things.  I even borrowed the ubuntulooks code for the checkboxes because I liked those better.

Another change I figured out was to make the scrollbars highlight to the prelight color you set in the gtkrc.

[http://www.gnome-look.org/content/show.php/xl_cheeselooks+gtk-engine?content=73163](http://www.gnome-look.org/content/show.php/xl_cheeselooks+gtk-engine?content=73163)

My engine is ready to be compiled so you are more than welcome to take it and make your changes.

---

### Post by wersdaluv on 2009-09-02
You know what? This is funny but I just realized that I just had to get the tarball of an engine then open its scr to play with its code. lol. I never thought of that until you mentioned "compile." 

Now, the thing is, I don't know where to start. Is there an engine howto/tutorial that you can recommend to me? I don't know what to do with this code. 

Thanks, btw.

---

