---
title: "Cairo Gtk+ themes..."
date: 2005-07-27
forum: Art &amp; Design
---

### Post by jzke on 2005-07-27
So now we have Cairo in use with Gtk, when do you reckon we'll see gtk themes using vector graphics? (as previewed here, [http://www.gnome.org/~seth/blog/xshots#Cairo](http://www.gnome.org/~seth/blog/xshots#Cairo))

---

### Post by bvc on 2005-07-27
when do you reckon we'll see gtk-engine? other than cvs
Then

(I am not a gtk developer)
We've never been shown how to use the pixmap and svg engine and now there's going to be another for us use improperly and at half its potential. What do I mean? Hang in there....there is a method to my maddness.....

One big issue with the other 2 has always been a lack of control over font colors for different widgets. We've always been very limited to a variety of colors and coolness as a result. This past week I spent an hour hacking (if you will....I call it guessing) and found it is possible, though not perfect, yet.
[http://kwh.kernow-gb.com/~bvc/images/test.png](http://kwh.kernow-gb.com/~bvc/images/test.png)

On the left is Alien. You can find it at gnome-look.org
On the right is the result of the one hour of guessing

Alien, like all other pixmap/svg themes, uses the same color font for buttons, tabs, menu, toolbar etc....
On the right, you'll notice diff color fonts on the widgets.

Put quite simply....gtk/svg devel has always known it could do this but did they tell us? Where's the theming howto? No, I don't mean the ones everyone knows about, I mean from devel? Even if devel would release one or two themes showing off all that the engines can do, we in turn would then know what to do. Now, we do not, so for years we've had crap themes.....for absolutely no reason other than laziness. What else can these engines do that we do not know about?

It is amazing to me that someone would spend so much time developing gtk/svg, just to let it look like crap and not ensure it is viewed at its full potential.

Will it happen with cairo? Lets hope not!

---

### Post by bvc on 2005-07-27
Further more, if all we get is slightly better looking images...whoohoo
Once and for all we need to know how to make gnome look better than any other platform/os...or you are wasting my time. Images on buttons ain't gonna cut it in fact that is nothing but tacky and anoying.
Metacity rounded corners will benefit but..........

Here son, a car for you....it doesn't start like any other car, you don't put it in drive like any other car, you don't stop it like any other car, and you don't take care of its finish like any other car.....it's yours, but I'm not going to tell you how to do any of these things, so....just enjoy looking at it on wonder what it would be like to use it as intended by those that spent millions of dollars designing, building and testing it, ok? ](*,)

---

### Post by Gnobody on 2005-07-28
Will future versions of Metacity be enhanced by Cairo?  Will this get rid of the aliasing around the edges of all round metacity themes?

---

### Post by bvc on 2005-07-28
[QUOTE=bvc]
Metacity rounded corners will benefit but...........[/QUOTE] ...so they say. Not with the current gtk, as I understand but it will have to be integrated into mcity. Someone please correct me if I'm wrong.

---

### Post by Gnobody on 2005-07-29
[QUOTE=bvc]...so they say. Not with the current gtk, as I understand but it will have to be integrated into mcity. Someone please correct me if I'm wrong.[/QUOTE]
 So like with GTK 2.8 & Gnome 2.12?

---

### Post by bvc on 2005-07-29
I have no idea. I'm not following cairo devel. Like I said above, until we can specify diff font colors for all the diff widgets, it makes little diff what cairo can do. We'll still have drab, plain, single, base, gray themes or...basic colored themes with colored fonts ...tacky.

I haven't heard anything about how resource intensive the engine is compared to pixmap/svg, has anyone else?

App devel needs to clean up. Now, I can specify the font colors in tabs but....open the volume control and it's using the wrong font colors. Why doesn't it follow proper gtk code? See...the prob with freesoftware is so many apps means, so many developers, which means someone ain't gonna follow protocol. You end up with an mess for a desktop. There's not a lot that can be done about that. Standards.... a wonderful thing.

---

