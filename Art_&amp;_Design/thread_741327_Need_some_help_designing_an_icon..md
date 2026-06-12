---
title: "Need some help designing an icon."
date: 2008-03-31
forum: Art &amp; Design
---

### Post by Engnome on 2008-03-31
I'm working on a small project of mine, it's a sound player but it's not geared to the common user but for people that needs to be able to quickly reach a desired sound.

Anyway the program is coming along fine but I need a logo and an icon for it. Tried dabbling with inkscape but this really is not my stuff. Care to help me? You will of course be given credit for your work. The program will be licensed under the GNU GPL v.3.

I was thinking something along the lines of Audacitys logo, sound waves perhaps? Maybe the W in WAFE could be a sound wave?

Screenshot:
[IMG]http://engnome.dyndns.org/WAFE/wafe_screenshot.png[/IMG]

//Yes it's written in Java, yes Python is superior, no I won't rewrite it in Python.

---

### Post by days_of_ruin on 2008-03-31
I'll give it a try.

---

### Post by smartboyathome on 2008-03-31
Something like this?

---

### Post by Engnome on 2008-04-01
> **days_of_ruin]I'll give it a try.[/QUOTE]

Much appreciated.

[QUOTE=smartboyathome said:**
> Something like this?

Hmm perhaps, but maybe not all around the W? If there are lines all around you often (at least I do) associate it with vibration. Look at the speaker icon in my app, those lines are clearly supposed to represent sound.

Originally I thought something along the lines of [_this_]("http://aura3.gaia.com/photos/14/139070/large/Sound_Wave.jpg") but formed as a W.

---

### Post by days_of_ruin on 2008-04-01
> **Engnome said:**
> Much appreciated.



Hmm perhaps, but maybe not all around the W? If there are lines all around you often (at least I do) associate it with vibration. Look at the speaker icon in my app, those lines are clearly supposed to represent sound.

Originally I thought something along the lines of [_this_]("http://aura3.gaia.com/photos/14/139070/large/Sound_Wave.jpg") but formed as a W.
Lol I downloaded that image whilst searching for inspiration!

---

### Post by Engnome on 2008-04-01
> **days_of_ruin said:**
> Lol I downloaded that image whilst searching for inspiration!

Yeah looks cool doesn't it? (plus it's the third hit for "sound wave at images.google)

BTW if anyone wonders where I got the speaker icon from it's part of the Crystal KDE theme. It's licensed under LGPL 2 so I think it's compatible... gotta include the license text though.

---

### Post by Crafty Kisses on 2008-04-01
The W is awesome.

---

### Post by Engnome on 2008-04-02
Well I experimented some and here's the result.

One without effects, 
one with some glow,
one with glow + gradient

Not really happy with the glow. Any pointers?

---

### Post by days_of_ruin on 2008-04-02
This isn't exactly what you wanted but...

---

### Post by smartboyathome on 2008-04-02
Why not use a w instead of 2 separate v's?

---

### Post by Engnome on 2008-04-02
> **days_of_ruin said:**
> This isn't exactly what you wanted but...

Didn't really start this thread with a clear Idea of what I wanted, (would have been pointless then wouldn't it?) except that I wanted a nice icon for my app.

That icon is pretty good, I took the liberty of modifying it into a 128x128 pixel big svg, (you painted on a 744.09x1052.36px canvas ;) )

What font did you use? When I select the text it says "ubuntu title" but it renders as Bitstream Vera. What fonts you have installed fonts matters to svg? :confused:

---

### Post by smartboyathome on 2008-04-02
He used the Ubuntu Title font, but you don't have it installed, so it renders wrong. He has to make the text a path via Path > Object to path.

---

### Post by days_of_ruin on 2008-04-02
> **smartboyathome said:**
> He used the Ubuntu Title font, but you don't have it installed, so it renders wrong. He has to make the text a path via Path > Object to path.

will do:P

---

### Post by days_of_ruin on 2008-04-02
Does this work now?

---

### Post by days_of_ruin on 2008-04-02
> **smartboyathome said:**
> Why not use a w instead of 2 separate v's?

It looks different.kerning to "v"s together makes a w but not as rounded.

---

### Post by smartboyathome on 2008-04-02
> **days_of_ruin said:**
> Does this work now?

Yes, it works now. And I would say it looks good, though may want to be a different color than black, so it cna be seen on multiple window border/panels.

EDIT: Took your svg, simplified it, and added color. Tell me what you think. :)

---

### Post by days_of_ruin on 2008-04-02
I don't really like the colors.Right now I am trying to add gloss to it
by putting a semi transparent circle over it.Is there a way to merge
the parts where they overlap and remove the parts where they don't?
Because right now if you put that on top of anything but white, it will
look dumb.

---

### Post by smartboyathome on 2008-04-02
> **days_of_ruin said:**
> I don't really like the colors.Right now I am trying to add gloss to it
by putting a semi transparent circle over it.Is there a way to merge
the parts where they overlap and remove the parts where they don't?
Because right now if you put that on top of anything but white, it will
look dumb.

You need to cut the semicircle so that it doesn't show up when on a black background.

---

### Post by days_of_ruin on 2008-04-02
> **smartboyathome said:**
> You need to cut the semicircle so that it doesn't show up when on a black background.

Exactly but I don't know how.:confused:

---

### Post by smartboyathome on 2008-04-02
Use Path > Division while they are both selected.

---

### Post by days_of_ruin on 2008-04-02
> **smartboyathome said:**
> Use Path > Division while they are both selected.

I figured that part out but how do I merge all the black parts into one path?Otherwise it doesn't work.

---

### Post by days_of_ruin on 2008-04-02
lawl, there was like ten different layers of the curvy lines.
problem solved!

---

### Post by smartboyathome on 2008-04-03
That still has the problem of being on a black/dark window border.

---

### Post by days_of_ruin on 2008-04-03
> **smartboyathome said:**
> That still has the problem of being on a black/dark window border.
You probably shouldn't be using an svg for a window icon though.

---

### Post by NullHead on 2008-04-03
I'm a n00b at this kind of stuff, but here is my two cents.

---

### Post by natehall on 2008-04-03
Here's my version.

---

### Post by smartboyathome on 2008-04-03
> **days_of_ruin said:**
> You probably shouldn't be using an svg for a window icon though.

I thought this was going to be the program's icon, and if so, then it *should* be used as the window icon.

---

### Post by Engnome on 2008-04-03
Yes the "winning" icon will be the official icon for the 1.0 app, the winning icon being the one I happen to like the most. Or maybe I'll post a poll in the cafe or something. If more people get involved there will definitely be a poll. (Nice and democratic ;) )

I plan to release an alpha as soon as I have the time, I'm a bit loaded with studies now and I have only a few days left to decide what to continue studying (should I try computer science or go for a master of science in engineering?)

On topic I like both natehall and NullHead's design. days_of_ruin's icon is coming along pretty good to. Just remember that it has to look good when it's 22x22 pixels so it has to be a really simple design. (Which I guess rule out my design :-|)

Edit: oh and yeah it should preferably be a scalable vector graphics (.svg)

Window icon? you mean the small java coffe cup in the corner then yes that would be replaced by the icon for WAFE.

---

### Post by days_of_ruin on 2008-04-03
> **smartboyathome said:**
> I thought this was going to be the program's icon, and if so, then it *should* be used as the window icon.

I know but you could export a 22x22 png and then add white around it or something.It will look better that way no matter what color it is.

---

### Post by days_of_ruin on 2008-04-03
Added white glow, tell me what you think.

---

### Post by smartboyathome on 2008-04-03
I like. That also takes care of the dark background problem.

---

### Post by Engnome on 2008-04-03
> **days_of_ruin said:**
> Added white glow, tell me what you think.

Looking good :D

I wonder if there is an accepted standard when it comes to the gradient (direction, colour etc.) to make your desktop look uniform. Human eyes are good at detecting things that are out of place such as shadows coming in from different angles.

Edit: looks even better when added on a .desktop file, works great in dark themes, like the one my laptop which is a must. (That it work in a dark theme, not on my laptop with my specific theme ;) )

---

### Post by days_of_ruin on 2008-04-03
> **Engnome said:**
> Looking good :D

I wonder if there is an accepted standard when it comes to the gradient (direction, colour etc.) to make your desktop look uniform. Human eyes are good at detecting things that are out of place such as shadows coming in from different angles.

Edit: looks even better when added on a .desktop file, works great in dark themes, like the one my laptop which is a must. (That it work in a dark theme, not on my laptop with my specific theme ;) )

Window icons are never consistent so I wouldn't worry about it.Did you try adding it to your program to see how it looks as a window icon?

EDIT:oh you already did.Care to post a screenshot?

---

### Post by Engnome on 2008-04-03
> **days_of_ruin said:**
> Window icons are never consistent so I wouldn't worry about it.Did you try adding it to your program to see how it looks as a window icon?

EDIT:oh you already did.Care to post a screenshot?

Much obliged.

You can see it in the apps top left corner, on the grey default sidux background and as a button on a KDE panel.

Looks great :D

Oh and by the way WAFE stands for WAFE ain't Fast Edit. FastEdit was a program for quickly editing files or something, never used it but my father did and so when it didn't work on XP (it came on something called a "floppy disc":confused:) he asked me to do something about it. He didn't use any edit functions, only the preview function or something like that so I set out to make a replacement for that feature only, hence my program is not FastEdit. :)

---

### Post by days_of_ruin on 2008-04-03
> **Engnome said:**
> Much obliged.

You can see it in the apps top left corner, on the grey default sidux background and as a button on a KDE panel.

Looks great :D

Oh and by the way WAFE stands for WAFE ain't Fast Edit. FastEdit was a program for quickly editing files or something, never used it but my father did and so when it didn't work on XP (it came on something called a "floppy disc":confused:) he asked me to do something about it. He didn't use any edit functions, only the preview function or something like that so I set out to make a replacement for that feature only, hence my program is not FastEdit. :)

Haha fits right in!
I was thinking wafe was for WAvE Find

---

### Post by days_of_ruin on 2008-04-03
Bad news, google "wafe".
Looks like its already used a lot.

---

### Post by Engnome on 2008-04-04
> **days_of_ruin said:**
> Bad news, google "wafe".
Looks like its already used a lot.

Yes but i haven't found any program called WAFE or anything related to sound. Might not be the first hit on google but I can live with that.

---

