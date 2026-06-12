---
title: "Another dumb question!  Re naming folders..."
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by john wagner on 2007-12-09
Now I've spent a few hours looking, and found answers to everything except my question...  A simple question too!
Is it possible to adjust the naming convention of file folders?  By this I mean, say I intend to name a folder,

     Aphrodisiacs of the World

What I end up with is,

     Aphrod
      isiacs
      of the
      World

I would LIKE to have complete names per line but don't know if that's possible.  It bugs me to see the names butchered like that (yes, it's just a minor nit, but it festers!)

I am running Dapper on a Pavilion Notebook, 2 gig 160gig HD, DvD+-R/RW, CD+-R/RW.  No microsnot at all (a few programs via Wine).
Thanks all!!

---

### Post by taurus on 2007-12-09
If you decide to have an empty space between words, then you need to use either " " or \.

```
mkdir "Aphrodisiacs of the World"
-or-
mkdir Aphrodisiacs\ of\ the\ World
```

---

### Post by john wagner on 2007-12-09
No, not the spacing...  I do all that, what bugs me is the way it breaks up complete words after 6 characters and jumps to another 6 character line when it displays the folders (say, on desktop).  IS there a way to increase the line length?  Say, 8-15 characters before a line jump is enforced?
So,

**[SIZE="3"]Antidisestablishmentarianism[/SIZE]**

(ideally how I wish the folder would look)

Becomes (now)

[SIZE="3"][B]Antide
stabli
shment
ariani
sm[/B][/SIZE]

But with the length modified,

[B][SIZE="3"]Antidestablishm
entarianism[/SIZE][/B]

Not the best example I grant you, but it shows the forced line breaks well enough.

---

### Post by spai on 2007-12-09
I am not sure if this is what you meant
But I tried ,
```
srikanth@ubuntu:~$ mkdir Antidisestablishmentarianism
srikanth@ubuntu:~$ ls
Additional  Antidisestablishmentarianism  Desktop  Firefox_wallpaper.png  Tries

```
It seems to work for me :)

---

### Post by Dr Small on 2007-12-09
I think he means in Nautilus, it is doing that.

---

### Post by john wagner on 2007-12-10
Yeah, when I'm just zipping along doing something, then I decide to save it to a file/folder.  Instead of going to terminal, I just rt click on desktop sticking out from behind whatever I'm working on.  Select the create a folder, name it and save to it.  Then, when I'm all done with whatever, I close her out and see the desktop.  And the 6 character  per line folder name.  It's a stupid nitpick I know, probably just exposes my OCD tendancies (or my insane quest for German neatness and order, heh).  But it really bugs me to see all those folders with weirdly broken-up names.  All I want to be able to do, is to name the folder without a character limit (length).  So the whole name/word is on each line.  I don't mind a lot of lines, but I want complete words.

For ex.:

          **[SIZE="4"][COLOR="Yellow"]FOLDER[/COLOR][/SIZE]**   
       [B] Incipi
        ent in
        sanity[/B]

Becomes (with adjustable word length):

         **[SIZE="4"][COLOR="Yellow"]FOLDER[/COLOR][/SIZE]**
    [B] Incipient 
         Insanity[/B]

Yeah, I know...VERY neurotic of me, but...

john

---

### Post by john wagner on 2007-12-10
refreshing

---

### Post by mcduck on 2007-12-10
Try to increase your icon size (in nautilus preferences), or decrease the font size (in System/Preferences/Appearance). I actually get something like 14 or 15 characters per line for icons..

Also it helps if you don't use the compact layout for icons in Nautilus. If I disable that I get even longer lines.

---

### Post by john wagner on 2007-12-10
[COLOR="Red"]mcduck  	
Re: Another dumb question! Re naming folders...
Try to increase your icon size (in nautilus preferences), or decrease the font size (in System/Preferences/Appearance). I actually get something like 14 or 15 characters per line for icons..

Also it helps if you don't use the compact layout for icons in Nautilus. If I disable that I get even longer lines. [/COLOR]



You know...  I never thought of that!  Sheesh!  I did the font size change, seems to work fine!

thanks!

john

---

