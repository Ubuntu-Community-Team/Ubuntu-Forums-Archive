---
title: "Gimp brushes"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by makz 18 on 2006-04-29
Hi, i'm new to linux and i don't know a whole lot about it.

I was playing around with gimp trying to make some brushes, but i can't save them in the brush folder. When i try to, it comes up with this message:

[http://i37.photobucket.com/albums/e97/makz18/Screenshot.png]("http://i37.photobucket.com/albums/e97/makz18/Screenshot.png")

Does anyone know how i can save my brushes because i'm quite a keen gfx artist and i rely heavily on gimp.

Cheers

---

### Post by Perfect Storm on 2006-04-29
You can't save it there. As you don't have permission. (security reasons).
Instead look/save it in /home/<username>/.gimp-2.2/brushes

To see hidden folders in your home directory with the file-browser click the view tab and select show hiddens. If you want to write the path in gimp press <ctrl>+<L>.
In the terminal to list all + plus hidden files/folders
```
ls -a
```

All your work and stuff you should keep in your /home directory

---

### Post by makz 18 on 2006-04-29
ok, thanks, i got it working.

I knew i didn't have permission, but i didn't know about any other places to save it, and i thought i might be able to change access priveleges and get permission to save it there.

---

