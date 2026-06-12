---
title: "Breezy Update stole my icons"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by mlhudson on 2006-04-20
After upgrading to Breezy Badger (which revealed to me how very little I know about linux) and finally getting back into the GUI (thanks to other posts!), I have no trash can icon and no home icons. When I look in the 'Panel' options, there is no image there. Can anyone help me get these back?

---

### Post by cleverselfreferentialname on 2006-04-20
OK, my guess is that something in your previous configuration wasn't much liked by the new desktop environment. Run rm -rf .gconf and your panels should return to the default. This will wipe out your application settings, I believe, but it will fix it.

---

### Post by mlhudson on 2006-04-20
>  Run rm -rf .gconf

As a complete and total novice, I need help to even do this. Run it with what? Sorry to be a newbie.

---

### Post by cleverselfreferentialname on 2006-04-21
Alright, no problem, go to Applications -> Accessories -> Terminal
In the terminal, type ```
rm -rf .gconf
``` then reboot.

---

