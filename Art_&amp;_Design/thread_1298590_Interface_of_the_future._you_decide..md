---
title: "Interface of the future. you decide."
date: 2009-10-23
forum: Art &amp; Design
---

### Post by ub520 on 2009-10-23
hey, I'm a bit of a spare time artist, and I have been cooking up ideas from an artistic point of view of the world. now I'm saying is that Ubuntu, windows xp, and Mac os x are very unfriendly to customness. 

Gnome makes you jump through hoops to customize, and KDE4 while customizable is kinda weak in it's themes. and so it occured to me that theming is more than just look. because a custom is for than just paint, it may be changing the furniture too, or going from a high end desktop, to a little netbook because you want lightness.


Now here is the question. How do we make a desktop enviroment that themeing is more than just changing the looks, but also changing fuctionality and design.

like some people like the wbar, but others don't, so maybe one widget has a w-bar interface whilest others have a standerd taskbar. maybe you prefer right or middle clicking for your menu, and maybe you want something brand new and never thought of before.

basicly how do you make a desktop enviroment that also includes widgets, and includes an easy way to mix and match themes.

throw anything out there. wether it's a widget Idea or a technical answer, or maybe even some Gimped images to show off your ideas, I want us to sit here right now design the interface of the future.

---

### Post by alex.rayu on 2009-10-23
That was way serious. You probably asked in the wrong place. And if you are not ready to offer any specific solution, this will not go anywhere from here.

---

### Post by ub520 on 2009-10-23
forgive me for asking, but what is the right place?

I was going to provide some examples of what I was talking about, but I ran into a problem with Gimp. Kinda frustrating.

---

### Post by Shpongle on 2009-10-23
well in my opinion we gotta beat os x in terms of looks they have the nicest gui in my opinion!, windows looks horrible in my opinion! like a kids toy or something!, i know we can easily change the looks but the first impressions count. just my 2 cents!!

---

### Post by ub520 on 2009-10-23
well yeah that is my opinion too. From my expiriance it isn't that easy to theme gtk/gnome. I've always found it to be stiff and rigid. E17 actually comes close to what I'm talking about with total customization, but it isn't stable at ALL, and it isn't widget oriented.

KDE4 is widget oriented, but it lacks the customization i was talking about.

---

### Post by alex.rayu on 2009-10-24
Probably where the developers are.

---

### Post by Tux Aubrey on 2009-10-24
> **ub520 said:**
> E17 actually comes close to what I'm talking about with total customization, but it isn't stable at ALL, and it isn't widget oriented.

I think you should take another look at e17 - the [latest builds]("http://packages.enlightenment.org/ubuntu/dists/karmic/") (and [installs built from source]("http://cafelinux.org/OzOs/content/how-install-ozos-desktop-existing-os")) are very stable and the modules and "gadgets" are extensive and themable. 

e17 _will_ do what you are talking about - with a combination of themes and profiles -  but right now theming is more like a programming task than art. You would need to "get into" the edje programming language to do anything more that just mod an existing theme - although there are a couple of basic gui tools that might help (edge-editor and edje-viewer).

Check out [Toma's Blog]("http://edjy.wordpress.com/") for some ideas and tips.  [Exchange]("http://exchange.enlightenment.org/") also has quite a few themes for e17.

The field is wide open and a serious themer would have a field day!

---

### Post by Rob2687 on 2009-10-24
"Total customization" is possible but not without diving into the coding side.

It's pretty hard to make an interface that customizable to the last detail yet easy to manipulate. Mostly because the more customizable it is the more complex it becomes under the hood. So it's harder simplify it back to something Joe Schlub can play with and not have to delve into the coding side.

Also changing the functionality of specific GUI elements may require changes in an applications source code. This is kind of hard to make customizable from the user side without modifying the code yourself. Something like that would probably require some pretty leet coding to build a GUI that is so customizeable like that.

The underlying graphics and functionality subsystems that make up interfaces are very complex beasts. Right now many things have been abstracted to higher level languages, scripts and stuff to make modding, themeing and customization easier. That's pretty much where we're at now. As mentioned above themeing and customization as well tends to deal more with programming these days.

There are restrictions when creating the GUI APIs, Toolkits and what not. How are the developers supposed to know that some Jill Schlub wants a w-bar interface (wtf is that anyways?) on their widget. It's not easy to code functionality for something which has never been though of before. That's why we end up with the GUIs that we have today.

If you want something new and never thought of before it's likely the code was never written for it before.



It does seem like E17 is trying to take this approach. Though the last time I tried E17 I found myself jumping through hoops.

---

### Post by vinutux on 2009-10-25
total rewriting form scratch..... Very hard one.........

---

### Post by moe_syzlak on 2009-10-25
> **alex.rayu said:**
> That was way serious. You probably asked in the wrong place. And if you are not ready to offer any specific solution, this will not go anywhere from here.

stop attacking the man. He's one of us! All opinions are welcome. And yes this is the right place!

---

