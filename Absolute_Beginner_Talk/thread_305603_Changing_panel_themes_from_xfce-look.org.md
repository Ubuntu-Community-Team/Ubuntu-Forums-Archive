---
title: "Changing panel themes from xfce-look.org"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-11-23
Hello, I have Beryl AiGLX installed successfully on my xubuntu 6.10 edgy. It works perfectly and I'm enjoying it.

I did it exactly how it is instructed on this wiki page: [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX) 

What I would like do is to learn how to change the Panels and themes to match my Emerald window themes, without ruining Beryl and Emerald.

I have downloaded and extracted some gtk2 themes from the xfce-look.org page and put them into my usr/share/themes folder. I also "corrected" their file permissions when it said they were incorrect in gksudo thunar usr/share/themes/32768-DarkerTheme.0.3 Properties-->--Permissions. But when I looked for my new themes in my "User Interface Settings", they do not appear.

I have looked everywhere for instructions and can never find any instructions on how to load a theme in xubuntu, other than saying to put the extracted file in usr/share/themes.

What I want to do is change my panels from gray to a "glass" theme like this: [http://www.xfce-look.org/content/show.php?content=32768](http://www.xfce-look.org/content/show.php?content=32768)

Thanks,
-c.

---

### Post by crimesaucer on 2006-11-23
All I want is black "glass" panels. Oh, and the menu boxes.

---

### Post by harryc on 2007-02-24
Same problem here...gtk2 themes are not recognized in /usr/share/themes as viewed from windows settings in xubuntu. Has anyone changed the panel backgrounds?

---

### Post by crimesaucer on 2007-02-26
Well, I rewrote my gtkrc for my overall theme, but I didn't include a different panel handle. I did change my panel's icons to a small and square setting to match the rest of my theme.

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-16-7.png[/IMG]

Everything is my own creation, if you want to learn how to change your panels, then go to your /usr/share/themes/ and then copy your favorite theme to your home folder and then rename it. Then move it back to your /usr/share/themes and start to play with it and compare it to your original theme. Learn where things are by changing the colors, and also by messing with some of the settings like gradient box fills and your x and y settings.

This theme of mine is about my 15th theme variation after playing around with theme for about a month.

This is another view:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-19-5.png[/IMG]

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-20-5.png[/IMG]

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-21-5.png[/IMG]

I was thinking about learning how to make the panel handle into a glass panel similar to my Emerald Theme. Or maybe a gradient fade like the one I used in my browser's tool bars and menu bar.

---

### Post by crimesaucer on 2007-03-06
This is not really about the "glass panel", but it is a "How To" I wrote for gtkrc themes: [http://www.ubuntuforums.org/showthread.php?p=2254490#post2254490](http://www.ubuntuforums.org/showthread.php?p=2254490#post2254490)

---

