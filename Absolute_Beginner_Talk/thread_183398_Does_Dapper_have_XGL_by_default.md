---
title: "Does Dapper have XGL by default?"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by uzi09 on 2006-05-27
i read somewhere that dapper includes XGL in it by default. is this true??

i'd really like to use some of the the things this guy is running in his linux :D
[http://video.google.com/videoplay?docid=-2626198040635992645&q=linux](http://video.google.com/videoplay?docid=-2626198040635992645&q=linux)

---

### Post by Belathor on 2006-05-27
It didn't for me. I had to follow a tutorial and download some stuff to get it working. It is still pretty buggy though. :(

---

### Post by joshrobinson on 2006-05-27
[QUOTE=Belathor]It didn't for me. I had to follow a tutorial and download some stuff to get it working. It is still pretty buggy though. :([/QUOTE]

yeah xgl isnt set up on default, but you need a decent ati or nvidia card to get it up and running.. one that supports openGL.. i ran it without a video card on one computer and it ran totally choppy and crappy

but when you get it up and running, its great

---

### Post by joshrobinson on 2006-05-27
oh yeah.. this is the tutorial i used


[http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_%28or_KDM%29]("http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_%28or_KDM%29")

---

### Post by uzi09 on 2006-05-27
o well, i've seen a few guides, so i don't think it should be too much trouble to install.

now as far as the card, that was the second thing i was worried about. i (unfortunately) have an integrated vid card on my dell inspiron 6400. i believe it does support openGL, but unsure how well. anyone know what the minimum specs should be to be able to get XGL running? or should i just try to install it and see how well it works?

---

### Post by joshrobinson on 2006-05-27
[QUOTE=uzi09]o well, i've seen a few guides, so i don't think it should be too much trouble to install.

now as far as the card, that was the second thing i was worried about. i (unfortunately) have an integrated vid card on my dell inspiron 6400. i believe it does support openGL, but unsure how well. anyone know what the minimum specs should be to be able to get XGL running? or should i just try to install it and see how well it works?[/QUOTE]

well the guide i posted was for ati i think.. but it sets it so you can switch between xgl and gnome at the login menu

you can attempt to try it without hardware acceleration and openGL but i garuntee it will run like a slow turd
there is a different guide you should try for your situation though.. if i can dig it up ill post it

if you have the money,  you can grab a cheap video card for like $100 USA to get it up and running

---

### Post by Belathor on 2006-05-28
> i (unfortunately) have an integrated vid card on my dell inspiron 6400. i believe it does support openGL, but unsure how well. anyone know what the minimum specs should be to be able to get XGL running? or should i just try to install it and see how well it works?

I am not sure but I think it does run on intel integrated graphics. Give it a try! And post how it went! I would like to put Ubuntu/XGL/Compiz on my little X41 Tablet with intel 900 integrated graphics. So, that info would be useful!

Thanks!

---

### Post by Belathor on 2006-05-28
grrr... browser problem.

---

### Post by uzi09 on 2006-05-28
thanks for the replies guys...

i really want to go forward with this, so i went hunting to see if there are any requirements, or if intel vid cards can handle it.

according to this thread, they seem to:
[http://ubuntuforums.org/showthread.php?t=148351](http://ubuntuforums.org/showthread.php?t=148351)


EDIT:
also, if you want to test whether your hardware can handle it, there is also a live cd available that was built for XGL. [http://kororaa.org/index.php](http://kororaa.org/index.php)

---

### Post by nalmeth on 2006-05-29
For intel cards you need to use AIGLX rather than XGL.

---

### Post by uzi09 on 2006-05-29
what is aiglx??

EDIT: never mind....[http://en.wikipedia.org/wiki/AIGLX](http://en.wikipedia.org/wiki/AIGLX)

---

### Post by uzi09 on 2006-05-31
hey all,

k, so i gave it a try on my intel. it works, but it is still quite buggy. it tripped out when i ran a movie full screen with xine. would show a blue screen and i could hear some sounds in the background, but nothing else would show. i even tried to kill X by hitting CTRL+ALT+BKSP, but it didn't respond. neither did control alt delete.

it isn't TOO big of an issue since it's very easy to turn it off and then watch a movie.

one other, big problem i encountered was that when i shut my lid, it kept the screen on for some reason. it was really odd. so i usually just turn aiglx off before i shut my lid -- kind of annoying :S.

guess theres still work to be done, but in the mean time, it looks pretty good.

---

