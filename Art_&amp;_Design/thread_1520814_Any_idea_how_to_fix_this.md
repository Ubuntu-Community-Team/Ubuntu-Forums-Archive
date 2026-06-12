---
title: "Any idea how to fix this?"
date: 2010-06-30
forum: Art &amp; Design
---

### Post by TheWeakSleep on 2010-06-30
Maybe I'm just picky, but I'm having an issue with my gtk theme where the space behind the text in the trash can and ubuntu one folder is a light blue color. It's really annoying as the text is a light color, and it's hard to read! I was just wondering if anyone out there has any idea how to fix this.

I've tried gnome color chooser, but it doesnt seem to be able to. Do i have to manually change it?

Heres a picture so you have an idea of what im talking about :)

[[img]http://lh6.ggpht.com/_TZQMMzDEvz4/TCrkthjtHPI/AAAAAAAAANY/JnT498kYe7E/s128/Screenshot.png[/img]]( http://lh6.ggpht.com/_TZQMMzDEvz4/TCrkthjtHPI/AAAAAAAAANY/JnT498kYe7E/s800/Screenshot.png)

hopefully the thumbnail works :) let me know if it doesn't :) 
Also, I appreciate any help you can give me, and I'm sorry if this isn't the place for this question :) thanks!

---

### Post by TheWeakSleep on 2010-07-01
I hate to bump my own thread, but does no one know where in the theme this can be changed? the color has to be defined somewhere :( 

I would appreciate any help : )

---

### Post by Anduu on 2010-07-01
Check through the theme's gtkrc file and look for a color entry which matches that color.

Sorry that's all I got :o

---

### Post by steveneddy on 2010-07-01
Can't change the colors with the theme?

Have you tried changing themes then?

---

### Post by TheWeakSleep on 2010-07-02
Thanks for the replies, i've looked through the gtkrc file but I couldn't find it, would it be anywhere else?

and yeahh I don't always have the problem with other themes.

---

### Post by Anduu on 2010-07-02
Which theme is that?

I'll install it and have a look.

---

### Post by TheWeakSleep on 2010-07-02
It was called Ma.Fa from deviantART
you can grab it from [ here](http://iamfuss.deviantart.com/art/Ma-Fa-GTK-114120258?q=boost:popular+ma.fa.gtk&qo=0)
thanks a lot for your help! :)

---

### Post by Anduu on 2010-07-02
OK I have mucked about with the theme and have discovered a couple of things...hopefully I can make this make sense :o

There is no entry to control the color of that area(...don't know what to call it :p ).It seems that is the default color Gnome gives that area when none is specified.

The main thing I noticed is that Ma.Fa. is a Pixmap engine theme.I tried every Pixmap theme I have and none of them changes the color of that area.My best guess is that the Pixmap engine,being fairly old,does not have the ability to modify that area at all as that area is a fairly new thing.

So...someone correct me if i am wrong...but I think you are best off to find a similar looking Murrine type theme and tweak that if necessary.

---

### Post by TheWeakSleep on 2010-07-02
Okay, thanks a lot for your help! :) It's just disappointing, i really liked this theme :) thanks again!

---

### Post by mcduck on 2010-07-02
> **Anduu said:**
> 
So...someone correct me if i am wrong...but I think you are best off to find a similar looking Murrine type theme and tweak that if necessary.
That's one option, but you can actually use many engines for a single theme, so if you figure out how to theme that element using Murrine (or any other engine) you can just add that to any pixmap-based theme. ;)

But in my experience very dark themes always tend to have this kind of issues. Actually I've never even seen one that wouldn't have light text on light background, or dark text on dark background, in some applications. So it's usually just something you need to live with if you use dark themes.

---

### Post by Anduu on 2010-07-02
> **mcduck said:**
> That's one option, but you can actually use many engines for a single theme, so if you figure out how to theme that element using Murrine (or any other engine) you can just add that to any pixmap-based theme. ;)

But in my experience very dark themes always tend to have this kind of issues. Actually I've never even seen one that wouldn't have light text on light background, or dark text on dark background, in some applications. So it's usually just something you need to live with if you use dark themes.

I was going to throw the hybrid type option out there but that would have opened a whole other can of worms that I don't have the required theming knowledge to offer help with ;)

And yes,very dark themes should be avoided as they usually need you to used special skins/workarounds for stuff like Firefox/Open Office etc.

---

### Post by TheWeakSleep on 2010-07-04
Well guys, thanks for all the help! I'm going to play with a few things, and if not, I'll be looking for a new theme :D I'll be marking this as solved. Thanks again :)

---

