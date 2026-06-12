---
title: "New IceWM Thin Black theme"
date: 2006-12-19
forum: Art &amp; Design
---

### Post by Albi on 2006-12-19
I originally tried to make this in fluxbox, but it just didn't look as nice, IceWM has much better pixmap support, most themes with a consistent title bar could easily be ported to it.

Credit goes to IYY because I used his IceVista theme as a base.

Enjoy!
[[IMG]http://img505.imageshack.us/img505/2788/screenshot2007020315561sr3.th.png[/IMG]](http://img505.imageshack.us/my.php?image=screenshot2007020315561sr3.png)

Also, here's the Emerald equivalent if anyone wants:
[http://www.gnome-look.org/content/show.php?content=48867](http://www.gnome-look.org/content/show.php?content=48867)

Edit 1: -Fixed the taskbar, shouldn't go weird anymore
-Made selected windows highlight
-Made Icon clearer

Edit 2: -Fixed the button (Now it's more or less centered)
Edit 3: I realized the font was way too big on the title, made it smaller+arial

Edit 4: See last post
Edit 5: Removed the shininess, was ugly.

---

### Post by aysiu on 2006-12-19
That is by far **the** coolest IceWm theme I've ever seen! Thank you so much for that. Most IceWM themes look like crap, but yours is on par with a regular Gnome or KDE theme!

The one thing I do have a gripe with is the Ubuntu logo--it looks a little fuzzy. I'd say everything else in the theme is a 10 out of 10, and the Ubuntu logo looks like a 6 out of 10. Is that just limitation of needing to use .xpm as an image format?

---

### Post by kerry_s on 2006-12-19
Ahh man, no fluxbox, you know a good black theme is hard to find. I finally went with blacklight, but changed the hot pink color to red.

---

### Post by IYY on 2006-12-20
Hey, the toolbar for this theme (or at least just the icons on it) is from my IceVista theme. Looks very cool! I think I'll start using this theme. :)

---

### Post by mordox on 2006-12-20
kewl. does a similar theme exist for gnome ?

---

### Post by Albi on 2006-12-20
> **IYY said:**
> Hey, the toolbar for this theme (or at least just the icons on it) is from my IceVista theme. Looks very cool! I think I'll start using this theme. :)

Lol, I knew I forgot something, should've credited @_@.
I used your IceVista theme as a base, just redid all of the pixmaps and edited the default.theme a bit.

@kerry_s fluxbox doesn't support rounded corners very well, although it should be very easy to make an approximate port.

@mordox I don't know how to make metacity themes, sorry.  However, you can change your window manager to icewm in gnome and use this theme.

aysiu: I don't understand why a lot of the themes for IceWM suck, it has really good pixmap support and most metacity themes you should be able to port to it by just using a screenshot and basic knowledge of gimp, doesn't take longer than an hour.  I'm going to do some more conservative gnome ports in the future.

I mean, look at the guides for Metacity themes and IceWM themes, they're pretty much the same!
[http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html](http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html)
[http://www.icewm.org/themes/](http://www.icewm.org/themes/)

Theme is now updated.

---

### Post by hanzomon4 on 2006-12-20
Wow, this is awesome!!! Good Job...

---

### Post by aysiu on 2006-12-20
I have a question for you, Albi.

Is there an easy way to make the system tray area black? Or is that not controlled by the theme?

I'll keep searching for the answers in the meantime.

---

### Post by IYY on 2006-12-21
I believe it's controlled by your GTK2 theme.

---

### Post by aysiu on 2006-12-21
> **IYY said:**
> I believe it's controlled by your GTK2 theme.
Is it? I'll play around with my GTK themes and see what I can do. Thanks for the tip.

---

### Post by Albi on 2006-12-26
Released new version
-Title bar was made "shinier'
-System tray area had the ugly black pixels removed from the top
-"Start" button should finally be fixed, fits in tray and looks better
Screenshot is of theme running on old computer

---

### Post by BLTicklemonster on 2006-12-29
Wow.

---

### Post by lion1810 on 2007-01-11
Hi Albi, what  icewm's version is in your linux box?

Have you used the patch for IceWM to implement borderless buttons ?

---

### Post by BLTicklemonster on 2007-01-11
Who what where?

Sounds nice how would one make sure they could get that?

---

### Post by lion1810 on 2007-01-11
taskbar with the patch

---

### Post by lion1810 on 2007-01-11
taskbar  without the patch

---

### Post by BLTicklemonster on 2007-01-11
Can't the same results be achieved by merely editing the .init file?

---

### Post by lion1810 on 2007-01-11
> **BLTicklemonster said:**
> Can't the same results be achieved by merely editing the .init file?

I don't know. 
:-k interesting!!:mrgreen:

---

### Post by Albi on 2007-01-11
Wasn't aware of such a patch, my taskbar looks similar though (no buttons however).

Anyways, two things,
1. How did you get beryl to work with IceWM?  I thought Emerald just replaces it altogether, making it useless...
2. Can you send me that theme?  It looks like the author made a custom menu background, I wasn't aware you could do that.

---

### Post by lion1810 on 2007-01-15
> **BLTicklemonster said:**
> Can't the same results be achieved by merely editing the .init file?


Can't the same results be achieved by merely editing the .init file?

---

### Post by lion1810 on 2007-01-15
> **Albi said:**
> Wasn't aware of such a patch, my taskbar looks similar though (no buttons however).

Anyways, two things,
1. How did you get beryl to work with IceWM?  I thought Emerald just replaces it altogether, making it useless...


If you spell about transparency, It's only a trick
> **Albi said:**
> 
2. Can you send me that theme?  It looks like the author made a custom menu background, I wasn't aware you could do that.

I've made myself. Can I help you?

---

### Post by Albi on 2007-01-15
> I've made myself. Can I help you?

Yes,
What is the file for a menu background and how did you find this out?

Edit: I guessed that the file was called menubg.xpm, and it was.  However, the tutorial I used to make my themes had no mention of this, and I couldn't find any other ones, so I want to know where this is documented.

---

### Post by lion1810 on 2007-01-16
> **Albi said:**
> Yes,
What is the file for a menu background and how did you find this out?

Edit: I guessed that the file was called menubg.xpm, and it was.  However, the tutorial I used to make my themes had no mention of this, and I couldn't find any other ones, so I want to know where this is documented.


I apologize for my english :-)))))
there is a translator? :)))))))) :mrgreen: ](*,) ](*,) 


BackgroundImage:

your default.theme

....
DesktopBackgroundCenter = 1
DesktopBackgroundImage = '/home/julia/bg.jpg' 



Options:
DesktopBackgroundImage=""
DesktopBackgroundCenter=1 # 0 / 1
DesktopBackgroundScaled=1 # 0 / 1


ex
DesktopBackgroundImage="background.jpg" 
DesktopBackgroundImage="35857-1.png"

---

### Post by lion1810 on 2007-01-18
The menu has 2 parts 

menubg.xpm 

and 

menusel.xpm 

basically the menubg.xpm and menusel.xpm  are repeated: 

(esempio1)

if you insert them in default.theme in gradiens 

Gradients="menubg.xpm menusel.xpm" 

they are enlarged 

as in icenoir's menu 


look at you must change the options "default.theme" of voice "Look" in "metal" 

# Look 
Look=metal 

:KS

---

### Post by BLTicklemonster on 2007-01-18
> **BLTicklemonster said:**
> Can't the same results be achieved by merely editing the .init file?

After serious consideration, much staring, and heavy thinking, I have finally figured out that no, that borderless button look most likely can't be done with simply editing the .init file. 

But tweaking themes is cool. I have one idea I've been wanting to work out for quite a while, I really want to get it done and share it. Probably end up ugly as sin, but I'm still going to try it out one day.

---

### Post by john280z on 2007-01-21
a really great theme, good job, thanks.

---

### Post by fuscia on 2007-01-27
wow! i didn't think something that pretty would work right in icewm. nice job!

---

### Post by lapsey on 2007-02-02
[[img]http://img0703.paintedover.com/uploads/thumbs/0703/sshot.jpg[/img]](http://paintedover.com/uploads/show.php?loc=0703&f=sshot.jpg)

I really like how this looks with the Tangerine theme. Changed all fonts to 8 point sans, though. 

Anyone know why this theme doesn't draw an outline when OpaqueMove=0 ??

---

### Post by jvc26 on 2007-02-03
Thats really nice work :)
Il

---

### Post by Albi on 2007-02-03
Hey all, thank you for your comments!
 I'm releasing a new version now.  Looks much better than the old, but I removed the shininess (makes it look cheap).  See original post.

---

### Post by vronp on 2007-02-07
Albi,

This is a nice theme but you need to change the last line in the default.theme file.  Or, mention it to people so they can edit it.

I am somewhat of a novice when it comes to thing X related, and it took me a couple days to find the default.theme file !!!!  Anyway, the last line in that file is specific to your system.  I found out that this single line overrides all other "methods" for changing the background image.

Once I fixed the path in that line and restarted, it all worked.

thanks,
Dave

> **Albi said:**
> Hey all, thank you for your comments!
 I'm releasing a new version now.  Looks much better than the old, but I removed the shininess (makes it look cheap).  See original post.

---

### Post by linex on 2007-02-09
when i go to theme preferences and choose install theme, and select the .tar.gz file i get an error "the file format is invalid"

am i installing this incorrectly?

---

### Post by OU812 on 2007-04-20
To install themes (my method)

1. cd /home/john/icethemes

2. tar xzvf theme.tar.gz

3. sudo mv theme /usr/share/icewm/themes

john

---

### Post by OU812 on 2007-04-20
In the screenshot in the first post, there is a program running in the top right corner. It shows a lot of system information. What is the name of this program, please?

This is a beautiful theme. Now I have to customize my desktop again to better complement this new theme. Worth the effort!

Thanks.

john

---

### Post by mech7 on 2007-04-20
How can i get the menu button like that? with me it is just a small icon?

---

### Post by Albi on 2007-04-20
Hi, there is a new version available, I no longer maintain this one:

I'm not sure why it doesn't show, maybe you're using a different version of IceWM

The program is Conky BTW

[http://ubuntuforums.org/showthread.php?t=400509&highlight=thinblack](http://ubuntuforums.org/showthread.php?t=400509&highlight=thinblack)

---

### Post by sorin.stirbu on 2007-05-04
Hey guys ! Nice theme !!  How do I install this theme ?  (I'm new with Ubuntu)

---

### Post by aysiu on 2007-05-04
See post #33.

---

### Post by sorin.stirbu on 2007-05-04
ok..i read that post (#33) but the 3rd line that i have to input in the terminal delivers me :


" mv theme /usr/share/icewm/themes
mv: cannot stat `theme': No such file or directory
"

after this i created the folder "icewm" and "themes" inside of it ...and moved it there but in the Themes (from System->Preferences) does not apear any "ThinBlack"

I am using Ubuntu 7.04 (maybe this helps :( )

---

### Post by aysiu on 2007-05-04
You have to substitute in the actual theme name where it says *theme*. So it'd be something like ```
tar xzvf ThinBlack2.tar.gz
sudo mv ThinBlack /usr/share/icewm/themes
``` instead of ```
tar xzvf theme.tar.gz
sudo mv theme /usr/share/icewm/themes
```

---

