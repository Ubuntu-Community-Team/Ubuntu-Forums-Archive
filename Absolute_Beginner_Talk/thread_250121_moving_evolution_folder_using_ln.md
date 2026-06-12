---
title: "moving evolution folder using ln"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by Episteme on 2006-09-03
I would like to move my evolution file /home/.evolution to /mnt/sdb1_storage/personal/email/.evolution so that i don't lose my email when/if I need to restore from diskimage.

I've copied .evolution to mnt/sdb1_storage/personal/email and rm /home/.evolution

I've also done ln --help, but am a little confused - 

am I right in presuming that ln /home/.evolution /mnt/sdb1_storage/personal/email/.evolution will create the necessary hard link?

---

### Post by Miademora on 2006-09-03
I think its more like:
```
ln /mnt/sdb1_storage/personal/email/.evolution /home/.evolution 
```

You think a hardlink is neccessary? A softlink should usually be enough.

---

### Post by Episteme on 2006-09-03
Thanks!

soft vs. hard link?  ok, didn't know there was a difference... this site set me streight.

[http://linuxgazette.net/105/pitcher.html](http://linuxgazette.net/105/pitcher.html)

so, should I use:
```

sudo ln -s /mnt/sdb1_storage/personal/email/.evolution /home/.evolution 
```
?  How can I test if it worked properly?

---

### Post by Miademora on 2006-09-03
Yes thats what i would use. 

When you do ```
ls -la /home/
``` you should see something like ```
.evolution -> /mnt/sdb1_storage/personal/email/.evolution
```

---

### Post by Episteme on 2006-09-03
Thanks mia! 

ok, I got it to work... but not the way I wanted it to...

after copying my .evolution file, i rt-clicked it, and selected 'make link', then moved it to my /home and renamed it from "link to .evolution" to ".evolution"... yes, i know it's cheating... but it worked.

then, ls -la /home/ to see what's up, and sure enough it showed me the link worked.  Fired up evolution, and it didn't know the difference! YEAH! (I was half expecting evolution to rm the link and create a new .evolution file).

Peace and stable code,

Sean

---

