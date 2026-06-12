---
title: "E17 theming anybody?"
date: 2005-12-16
forum: Art &amp; Design
---

### Post by super on 2005-12-16
no i don't have any, i'm looking for some.

take a look at the e17 screenshot in my sig.

the gtk theme is a quick clearlooks hack to (kinda) match the e17 theme? -fine
the icons are a slight edit of ricebowl (again, not quite perfect but...) -fine
the fonts are just vera sans bold (which i actually like) -fine

here are my problems:
1. i can't figure out how to change the fonts or icons on the e17menu

2. eclair themes are (extremely) rare and the default one just doesn't match. has anybody tried theming this yet?

any help would be great!
thanks!

---

### Post by super on 2005-12-19
another question:

does anyone know if idesk will work with e17?

---

### Post by Juippisi on 2005-12-20
Have you tried [http://get-e.org/E17_User_Guide/English/_pages/3.9.html](http://get-e.org/E17_User_Guide/English/_pages/3.9.html) <- this tutorial?

I doubt about getting iDesk to work in E17. 

I personally have used the E17 since March and I can say that lately it has developed a lot! Hope they get soon notes and those "old and legendary" modules back to work. If they do, I bet that some "desktop icon" -module will be developed. So, basically you just need a little patience my friend.

Btw, you have a beatiful desktop. I used to use Winter-theme some time ago, but, not just anymore. If you manage to get some theme made, remember to inform me about it ;-).

---

### Post by Juippisi on 2005-12-20
Now I'm at home, finally. So basically you can change the menus font to something by typing

cd ~/.e/e/themes
edje_decc winter.edj
cd winter
nano default_menu.edc (edit to your needs)
./build.sh
cp theme.edj ../.

and that should do it. You can edit other .edc -files for your needs too. Hope this helps :-).

---

### Post by super on 2005-12-21
thanks for the tip! it worked!

i changed the ibar and nautilus icon theme to [this one]("http://oceanic.wsisiz.edu.pl/~slabosz/wordpress/?p=566").

i'm not much of a themer, but i'm gonna try to gonna try to get some rounded corners for the winter theme.

i'll give idesk a shot to see for sure if it works or not.

---

