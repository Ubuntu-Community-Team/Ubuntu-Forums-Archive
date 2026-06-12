---
title: "Windows filenames"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by Exxar on 2006-11-10
Windows allows for naming of files like "yxz abc", with the space in between, and other characters that I suppose are forbidden under linux. I can reach those files through nautilus, but is there a way to reach them through the terminal?

---

### Post by Bachstelze on 2006-11-10
Use the Tab key to complete filenames, just the same way you do for nicks on IRC ;)

---

### Post by Iowan on 2006-11-10
I think you may have answered your own question...
IIRC, surrounding the name with quotes *should* work.

---

### Post by CatKiller on 2006-11-10
> **Exxar said:**
> Windows allows for naming of files like "yxz abc", with the space in between, and other characters that I suppose are forbidden under linux.

Pah - the **only** character that you **can't** use in a filename under Linux is "/".

> I can reach those files through nautilus, but is there a way to reach them through the terminal?

You have some options. Tab-completion is the best, because it's the most accurate - you don't have to worry about case either that way. Or you can use quotes. Or you can "escape" each control character by putting a "\" in front of it, like so:
**My\ Documents**

All much more elegant than **Micros~1**, don't you think?

---

### Post by Bretls on 2006-11-10
In the terminal use * for any spaces.
bret@ubuntu:~$ cd /media/hda6/My Music
bash: cd: /media/hda6/My: No such file or directory
bret@ubuntu:~$ cd /media/hda6/My*Music
bret@ubuntu:/media/hda6/My Music$

---

### Post by moshuptrail on 2006-11-10
I recommend quotes. Double-quotes.

Using * could be risky because of how bash works.  (Although the way Bretls is suggesting to use it probably works fine)
* is a wild-card.  Before bash executes whatever command you are typing it first expands wild cards.  So, if you had several files named; "big long file" and "big bad file" and "big ugly file", bash will expand "big*file" to pass all three files to whatever the command is.  If it's a rm command the results could be disastrous.

Tab expansion is a feature supported by bash, but not necessarily by other shells.  (ksh uses the <esc> key for expansion, and sh doesn't support expansion at all)  It looks in the current directory and expands to match files there.  If you had multiple directories called "My Music" and "My Pictures", etc. then it won't be able to expand past "My" until you give it more info.

---

### Post by CatKiller on 2006-11-10
> **moshuptrail said:**
>  It looks in the current directory and expands to match files there.  If you had multiple directories called "My Music" and "My Pictures", etc. then it won't be able to expand past "My" until you give it more info.

True, but it does give you a list of possibilities so that you know what your options for that extra information are. And I'm not sure that I'd think of it as matching files in the current directory: it's true to a point, but the completion works for commands too, and you can use it to navigate through many subdirectories - starting from the root folder instead of the current directory, if you wish - just by pressing Tab a few times, and a handful of letters, depending on your directory structure.

I like it - can you tell? :D

Double quotes (I hadn't thought that other people might call them that instead - good catch) are fine, but it's so much typing. And you can still be messed up by something unexpectedly being upper-case, or not remembering exactly what it's called.

---

### Post by moshuptrail on 2006-11-10
Ahah!  You have to hit tab several times!  (to get a list of choices)
That's very nice.  I was not aware of that very nifty feature.:D 

It seems to look through your PATH for executables that might match.  Very useful when you can't quite remember a command.

---

