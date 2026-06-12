---
title: "New IceWM theme - IceGil Grey"
date: 2006-12-21
forum: Art &amp; Design
---

### Post by Albi on 2006-12-21
This one was quick.  Doesn't seem to be any major problems with this one. Its basically the Gilouche metacity theme, but with my own touches to it.  Goes well with a grey Murrina theme and a background of a landscape.  It's supposed to be more conservative and professional looking than my last one.

Enjoy!

[[IMG]http://img224.imageshack.us/img224/447/screenshot2006122121232gx6.th.png[/IMG]](http://img224.imageshack.us/my.php?image=screenshot2006122121232gx6.png)

Edit1: Couldnt upload file, separated background from theme

---

### Post by nalmeth on 2006-12-21
Very nice (clean) looking theme!

---

### Post by K.Mandla on 2006-12-21
Albi, that's **very **sharp. You're making me want to use IceWM!

---

### Post by Dubai Lady on 2006-12-24
nice!!! 8)  


thanks

---

### Post by graabein on 2006-12-24
I can't get this to work. I'm probably doing something wrong. I unzipped it to **/usr/share/icewm/themes** and selected it from themes in the start menu. 

The menu line in the bottom looks okay but the window captions are blue and the system buttons for each application are blurred. Do I have to have a certain resolution or colour depth?

:confused:

---

### Post by Albi on 2006-12-24
Are you using the IceWM from the repositories?
(Btw post screenshot)

---

### Post by graabein on 2006-12-25
Maybe it's an old version of IceWM. I'm still using Dapper here.

---

### Post by Albi on 2006-12-25
That's very strange...it looks like it's not finding the pixmap images.  Make sure you unzipped everything, I'm not sure what else to suggest; try unzipping it in /usr/share/icewm/themes instead.  Also, it uses the arial font and you may not have that, causing everything to mess up somehow.  If so, edit default.theme and change 
> TitleFontNameXft		=	arial:size=9:bold
to
> TitleFontNameXft		=	sans-serif:size=9

I don't think changing color depth will solve anything in this case.  Maybe you can try installing the Edgy package instead and see what happens?



Also, I released both of my themes to freshmeat, and a Mac Clone and Vista Clone (2 colors) one should be ready soon.
[http://themes.freshmeat.net/projects/icegilgrey/](http://themes.freshmeat.net/projects/icegilgrey/)
[http://themes.freshmeat.net/projects/thinblack/](http://themes.freshmeat.net/projects/thinblack/)

---

### Post by graabein on 2006-12-29
Hi, my machine broke down so I've not been able to answer before. It's still broken btw. 

I did unzip everything to **/usr/share/icewm/themes** and it's still the same. Changing the font did not do any difference. I'm guessing it's because I run **1.2.23-3ubuntu1** version from Dapper and in Edgy IceWM is version **1.2.28-1ubuntu1**. Does not matter. I will look at it when my machine is back on air.

Another thing I came to think of: What if you included SVG image of buttons and such so it's easy for others to tinker with it? I for one did not want the Windows logo on the start menu button so I had to hack it in GIMP. 

Very nice theme though. It really made me want to check out IceWM! :D

---

### Post by Albi on 2006-12-29
> **graabein said:**
> Hi, my machine broke down so I've not been able to answer before. It's still broken btw. 

I did unzip everything to **/usr/share/icewm/themes** and it's still the same. Changing the font did not do any difference. I'm guessing it's because I run **1.2.23-3ubuntu1** version from Dapper and in Edgy IceWM is version **1.2.28-1ubuntu1**. Does not matter. I will look at it when my machine is back on air.

Another thing I came to think of: What if you included SVG image of buttons and such so it's easy for others to tinker with it? I for one did not want the Windows logo on the start menu button so I had to hack it in GIMP. 

Very nice theme though. It really made me want to check out IceWM! :D

It shouldn't show the windows logo...although I included it, but it seems it's looking for a different pixmap than it should (icewm_win instead of icewm.png). Your screenshot doesn't show this though.... 
What I would do is check the folder for broken symlinks; try replacing the symlinks with copies or fixing them another way if this is the case.

As for SVGs: I don't have any, sorry.  What is in the package is what I made for many things.  But because the image is so small, you can just zoom in very high and edit it easily.

---

