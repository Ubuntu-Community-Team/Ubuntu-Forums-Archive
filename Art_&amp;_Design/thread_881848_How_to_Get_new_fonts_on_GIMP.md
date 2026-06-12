---
title: "How to Get new fonts on GIMP"
date: 2008-08-06
forum: Art &amp; Design
---

### Post by jjmono987 on 2008-08-06
**_[CENTER][SIZE="4"]He here is a Beginners Guide on how to Put fonts on GIMP.[/SIZE][/CENTER]_**
[B][COLOR="Blue"]
1).First Choose a font from the font site. (dafont.com is reccommended)


2).Then Click download and wait till the file opens. 


3).After it opens you should have 3 documents the only one that matters is the .ttf file.


4).Next go to Places and open the Home folder.

 
5).it should be on the username w/e it is. Now go to View and Show Hidden files.


6).Now scroll until you see a folder called .gimp-2.4. Open it.


7).Then Look for a folder called Fonts. Open it.  you should have something like this:

/home/yourusername/.gimp-2.4/fonts


8.Just place the thefontname.ttf file in the this folder.


9).Now Open the Terminal under Accessories. This is to refresh the Font cache.


(Optional) 10).Now after the terminal opens type in this code here:[/COLOR][/B]

```
sudo fc-cache -f -v
```
[B][COLOR="Blue"]

i have used the codes and it worked after i did that but in some cases u have to but you normally dont have to do it. All you do is close gimp and start it up again.


11). After you enter the code it will ask you for your password (the password is what you use to login with) and after you enter your pass word it will refresh the cache 

And you should be good to go with GIMP.[/COLOR][/B]
[B]

If you have any questions about how to do this please ask me here or through PM.[/B]
[CENTER]
**Hope This Guide Helps out all members.**[/CENTER]

---

### Post by days_of_ruin on 2008-08-06
Or just stick it in the .fonts folder.I don't see why you have
to use the command line.You definitely do not need to use sudo to 
install fonts to a single user.

---

### Post by jjmono987 on 2008-08-06
Accually you do need to do the sudo because if you dont they will not show up on gimp.

---

### Post by AJB2K3 on 2008-08-07
> **jjmono987 said:**
> Accually you do need to do the sudo because if you dont they will not show up on gimp.
You DON'T need the command in my experience.
There is a very good guide to font installation already available.
EDit, well there was but it seams the  hosting has gone.

---

### Post by days_of_ruin on 2008-08-07
> **jjmono987 said:**
> Accually you do need to do the sudo because if you dont they will not show up on gimp.

You just have to close gimp and open it up again.I never used sudo to add
fonts to gimp.

---

### Post by jjmono987 on 2008-08-08
well i have tried closing it and then opening it back and it didnt work but i have used the codes and it worked after i did that but in some cases u have to but you normally dont have to do it. All you do is close gimp and start it up again.

---

### Post by Crafty Kisses on 2008-08-09
> **days_of_ruin said:**
> Or just stick it in the .fonts folder.I don't see why you have
to use the command line.You definitely do not need to use sudo to 
install fonts to a single user.

Yeah, that's the easiest way, or use kfontview.

---

### Post by stevepoppers on 2012-01-28
I understand this is a necro and I apologize for that, but I was just having the problem of new fonts not appearing within gimp. I placed them in the ~/.gimp-<version>/fonts folder and refreshed and restarted gimp, but they would not show up. Ran that command and restarted gimp and they did. So, thanks to OP, poo to his detractors.

---

