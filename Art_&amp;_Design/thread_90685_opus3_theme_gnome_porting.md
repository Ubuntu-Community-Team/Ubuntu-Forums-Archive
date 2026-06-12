---
title: "opus3 theme gnome porting?"
date: 2005-11-15
forum: Art &amp; Design
---

### Post by lizardking on 2005-11-15
Viewing new clearlooks engine that support libcairo[(tutorial here)]("http://www.ubuntuforums.org/showthread.php?t=89056") I found in the clearlooks developer a real nice window manager:[COLOR="Black"][SIZE="3"]**Opus3.**[/SIZE][/COLOR]
 Moreover it look like very cool and smooth with new clearlooks engine default color:
take a look of this here:
[IMG]http://www.stellingwerff.com/cl-cairo/clearlooks-cairo1.png[/IMG]
but there is a problem: **the theme is for XFCE not Gnome.**
So there is somebody who have tried to port a Xfce theme into metacity and can do that?
[here the "xfce source"]("http://www.xfce-look.org/content/show.php?content=29504")

bye 
lizardking

---

### Post by dude2425 on 2005-11-15
If you wan't it so bad, why not just kill metacity and replace it with XFWM? I believe theres a tutorial out there somewhere on how to do it, just search.

Thnx for the link to the theme though, been looking high and low for it ever since I first saw that screenshot.

---

### Post by bvc on 2005-11-15
Threw this together from the xfce source. My original intent was to have the bg change with the loaded gtk theme, which worked everywhere except the right edge of the titlebar, so if I find the time I'll draw the right titlebar edge with metacity code.

download
[http://kwh.kernow-gb.com/~bvc/theme/mcity/Opus3-MCity.tar.gz](http://kwh.kernow-gb.com/~bvc/theme/mcity/Opus3-MCity.tar.gz)

screenie
[http://kwh.kernow-gb.com/~bvc/theme/screenshots/Opus3-MCity.jpg](http://kwh.kernow-gb.com/~bvc/theme/screenshots/Opus3-MCity.jpg)

---

### Post by bvc on 2005-11-15
[screenie of smooth engine opus]("http://kwh.kernow-gb.com/~bvc/theme/screenshots/Opus3-MCity.jpg")
[Simply_Smooth-Opus]("http://kwh.kernow-gb.com/~bvc/theme/gtk/Simply_Smooth-Opus.tar.gz")

---

### Post by lizardking on 2005-11-16
[QUOTE=bvc][screenie of smooth engine opus]("http://kwh.kernow-gb.com/~bvc/theme/screenshots/Opus3-MCity.jpg")
[Simply_Smooth-Opus]("http://kwh.kernow-gb.com/~bvc/theme/gtk/Simply_Smooth-Opus.tar.gz")[/QUOTE]
well done:KS

---

### Post by tvoss on 2005-11-16
To replace metacity as default window-manager:

[FONT=Courier New]killall metacity && yourPreferredWindowManagerExecutable

[FONT=Verdana]Then save your current gnome-session and on next startup, metacity will be replaced with your preferred wm.
[/FONT]
[/FONT]

---

### Post by bvc on 2005-11-16
[QUOTE=bvc][screenie of smooth engine opus]("http://kwh.kernow-gb.com/~bvc/theme/screenshots/Opus3-MCity.jpg")
[Simply_Smooth-Opus]("http://kwh.kernow-gb.com/~bvc/theme/gtk/Simply_Smooth-Opus.tar.gz")[/QUOTE]
[updated] I changed the 'edge' from smooth to thin.

---

### Post by bvc on 2005-11-17
[http://kwh.kernow-gb.com/~bvc/theme/mcity/Opus3-MCity.tar.gz](http://kwh.kernow-gb.com/~bvc/theme/mcity/Opus3-MCity.tar.gz)
[updated] added maximized state and prelight buttons

---

### Post by bvc on 2005-11-18
[updated-mcity] didn't like the prelight buttons, so changed them
[http://kwh.kernow-gb.com/~bvc/theme/mcity/Opus3-MCity.tar.gz](http://kwh.kernow-gb.com/~bvc/theme/mcity/Opus3-MCity.tar.gz)

[updated-gtk]Added a lighter/tanish version of the gtk
[http://kwh.kernow-gb.com/~bvc/theme/gtk/Simply_Smooth-Opus.tar.gz](http://kwh.kernow-gb.com/~bvc/theme/gtk/Simply_Smooth-Opus.tar.gz)

---

### Post by plb on 2005-11-18
You should upload it to gnome-look for all to enjoy :p

---

### Post by bvc on 2005-11-19
I'm going to work on it a little more ...maybe give it a better border. In the current version the entire_background and border is metacity, but the buttons and titlebar are pixmap. If I make the titlebar transparent only leaving the blue, the main titlebar image tiles all the way through the right side of the titlbar, and I don't know how or if I can stop it at the right side image. You'd think it would by default. Then you could use any color gtk theme.

---

### Post by dude2425 on 2005-11-19
An inactive or unfocused titlebar would be great with this too, and it's not that hard to setup. I modified it on my own so it's olive green (matches my theme) and has an inactive titlebar. I'll include it in this post. I renamed it to Opus3-Olive so not to confuse with yours, as mine is green.

---

### Post by plb on 2005-11-19
BTW, nice work. Look forward to seeing the finished product

---

### Post by bvc on 2005-11-20
[http://gnome-look.org/content/show.php?content=31549](http://gnome-look.org/content/show.php?content=31549)
Everything except the main/colored part of the titlebar is pure metacity now!

[IMG]http://kwh.kernow-gb.com/~bvc/theme/screenshots/Opus3-Pre.png[/IMG]

---

### Post by bvc on 2005-11-20
[QUOTE=dude2425]An inactive or unfocused titlebar would be great with this too, and it's not that hard to setup.[/QUOTE]
Done! Enjoy!
[http://gnome-look.org/content/show.php?content=31549](http://gnome-look.org/content/show.php?content=31549)

[IMG]http://gnome-look.org/content/pre2/31549-2.png[/IMG]

---

### Post by dude2425 on 2005-11-20
Sweat! I'm lovin' it!

Creapy though. I was playing around with clearbox just yesterday (about 9 at night IIRC) and was just about to login and suggest using clearbox's buttons. I decided instead to go to bed and post the next day, which would be today, and now posting the suggestion would be quite redundant. I even had a little hack-up of it working, kinda. It's kind of amazing how people can just think of something and somebody else already knows what it is. I guess I don't need the little hack-up anymore.

Same thing happend yesterday (kinda)
I sent my mom a list of all the Black Friday sales, just a half hour before her freind sent her an email asking for the info on black friday (or black thursday if your as blonde as her friend)
I'm waiting for a third experience to actually say it's anything more than a coincidental coincidence.

---

### Post by bvc on 2005-11-20
:p 
The Clearbox buttons was the plan from the beginning. I also thought about Clearbutt buttons
[http://gnome-look.org/content/pre1/26914-1.png](http://gnome-look.org/content/pre1/26914-1.png)
but decided Clearbox buttons looks better.

I'm pretty much done theming, but I saw this request and thought..."I've always wanted to do a more 'pure'/gtk color metacity with images like Bluecurve". Took me all day yesterday to figure it out :???: but it felt good to theme again and do something I've never done.

---

### Post by dude2425 on 2005-11-20
I'm glad you decided against that butt one lol. Clearbox looks a whole lot more fun than that other one.

---

### Post by missynay on 2005-11-20
is anyone getting a line accross the bottom of the inactive titlebar on the default version w/o an titlebar image?

---

### Post by plb on 2005-11-20
nicely done

---

### Post by MetalMusicAddict on 2005-11-20
Hey bvc. Do you know if b0se uses linux yet? I loved his themes in windows. Opus was/is great.

---

### Post by bvc on 2005-11-20
[QUOTE=MetalMusicAddict]Hey bvc. Do you know if b0se uses linux yet? I loved his themes in windows. Opus was/is great.[/QUOTE]
Haven't a clue. Never talked with him/her/it. Jerk has never returned any of my emails in the past concerning ports, so I didn't even ask on this one. Heh, it's not like I can't make that titlebar image in 5 minutes anyway, and it's the only thing in the theme from him, if it was even from him, and not made by whoever ported to xfce4....I don't know...don't have time to screw with it. I noticed a theme with the name 'OSX' in it so I don't know if he went mac or if it's just in the theme name.

---

### Post by bvc on 2005-11-20
[QUOTE=missynay]is anyone getting a line accross the bottom of the inactive titlebar on the default version w/o an titlebar image?[/QUOTE]
Hey wife!
Yeah, I fixed it!
[Updated]("http://gnome-look.org/content/show.php?content=31549")

---

### Post by MetalMusicAddict on 2005-11-20
I used to see b0se at Aqua-Soft alot but now hes most active at DeviantArt. He's a good guy but busy. Youll find his page at DeviantArt if you search.

---

### Post by bvc on 2005-11-20
[http://b0se.deviantart.com](http://b0se.deviantart.com)

---

