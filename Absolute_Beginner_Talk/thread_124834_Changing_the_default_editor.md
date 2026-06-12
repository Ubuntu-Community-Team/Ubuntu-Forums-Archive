---
title: "Changing the default editor"
date: 2006-02-02
forum: Absolute Beginner Talk
---

### Post by average on 2006-02-02
After skipping a lot of classes to learn the basics of vi, I find the Ubuntu installation to have pico as the default text editor. How can I change that? Sorry if this is too basic, but I have very limited knowledge of bash/linux/whatnot and would like to learn more.

---

### Post by bonzodog on 2006-02-02
Vi is installed on ubuntu, and you can use either that or nano (pico's successor). I personally, as a highly experienced linux user, prefer nano as it is easier to use. There is also gedit that you can use in gnome.

---

### Post by Iowan on 2006-02-02
I think **gedit** is the default GUI editor.  **nano** seems to be the preferred CLI editor, but **vim** is also available.

---

### Post by average on 2006-02-02
I have noticed vim also being installed. My trouble is getting it to be the default for console-based operations. For instance, when editing the body of an email using mutt, I would like vim instead of pico. If I'm not mistaken (although I probably am), there is an environment variable to do this.

Thanks for the input so far.

---

### Post by kabus on 2006-02-02
I think setting the $EDITOR environment variable like this

```
export EDITOR=vim
```

either in /etc/profile or in the .bashrc file in your home directory should do it.

---

### Post by Iowan on 2006-02-02
> typical blundering n00b... bare with me...
Unless your an oversexed coed, I'd just as soon NOT get naked with you.[-(

---

### Post by average on 2006-02-02
So far so good... It worked when I typed it in the prompt, but I'm too lazy to restart now. But it probably works, so thanks a whole bunch. I added it in the global settings file, since all users use vim (I think).

---

### Post by average on 2006-02-02
[QUOTE=Iowan]Unless your an oversexed coed, I'd just as soon NOT get naked with you.[-([/QUOTE]

Not sure what that was supposed to mean. Really (not a native speaker). If my sig has somehow offended you, let me know and I'll tear it down.

---

### Post by DonQuixote on 2006-02-02
[QUOTE=average]Not sure what that was supposed to mean. Really (not a native speaker). If my sig has somehow offended you, let me know and I'll tear it down.[/QUOTE]
LOL!  I believe it was meant as a joke.

"bare" can also mean "get undressed" or "uncover". 8)

---

### Post by average on 2006-02-02
That's really funny indeed :mrgreen: 

Thanks for the language lesson.

---

