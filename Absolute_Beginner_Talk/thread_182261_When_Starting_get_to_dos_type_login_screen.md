---
title: "When Starting get to dos type login screen"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by nickman on 2006-05-25
When I start I get to a login screen, I then proceed to login with my username and password.  It works then just sit their no gui or error messages.
The install went fine.  I didn't install the GRUB boot loader but installed another one with an L...something.
Any help would be apprieciated.:rolleyes:

---

### Post by user1397 on 2006-05-25
what does it look like when it just sits there?

---

### Post by Hellsteeth on 2006-05-25
Probably LILO was the alternative bootloader.
By login screen do you mean the ubuntu login screen (brown background)?
If you have got this far the problem will be with the Xserver.
You can toggle to a console by pressing ctrl + alt + F1, and ctrl + alt + F7 to get back. Once in the console you can try to diagnose the problem.

---

### Post by nickman on 2006-05-25
No brown screen, just a black screen with white text. Don't know how to boot the gui

---

### Post by johanhartman on 2006-05-25
I'm having the same problem. What graphics card and on what chipset do you use?

---

### Post by Hellsteeth on 2006-05-25
I meant the screen you logged in at before you get the black screen.
Describe the screen that you are logging into with your username and password.

2nd question. At this black screen is there any form of prompt that you can type into? If so, type startx

---

### Post by user1397 on 2006-05-25
first of all, did you just install it? what does it say? can you type anything? does it say anything like:
root@ubuntu:~# or something like that?
if so, try typing 
```
startx
```
if that doesn't work, i'll show you what to do later.

---

### Post by nickman on 2006-05-25
I have a banshee graphics card and i don't know what kind of chipset

---

### Post by nickman on 2006-05-25
I'll try start x, but it may be awhile

---

### Post by user1397 on 2006-05-25
[quote=nickman]I'll try start x, but it may be awhile[/quote]
don't worry, we're always here...:p

---

### Post by Ptero-4 on 2006-05-25
nickman. Does the black screen look like this:
```

localhost login:

```

---

