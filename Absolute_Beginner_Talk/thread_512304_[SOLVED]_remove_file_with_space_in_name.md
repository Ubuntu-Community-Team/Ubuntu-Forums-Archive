---
title: "[SOLVED] remove file with space in name?"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by carloslosgrande on 2007-07-29
[FONT="Comic Sans MS"][I]Hi guys, I recently helped a friend repartition and in the process saved her files to my ext hdd. 3 of these folders have become locked in moving them. They have names like 'My Music' .......with the space.

I checked the folder properties and it says I'm the owner but when I try to delete/move to trash I get the error that I don't have permission.:mad:

I tried chown but as the folders have a bloody space in the name I can't do anything.:confused:

So....how do I get control of these folders? I only want to delete them.[/I][/FONT]

---

### Post by dmizer on 2007-07-29
to chown, you can do several things.

first, start typing the first part of the file name, and then hit the <tab> key and the rest of the name will auto fill.
you signify a space with a reverse slash like so ... My\ Music

so you can delete the directory with the following command:
```
sudo rm -r My\ Music
```

---

### Post by 5-HT on 2007-07-29
You can either use quotation marks (if the filename already has a single quote: use double quotes, etc...) or an escape to work with spaces in filenames in a shell (can then be chown'd or removed with root privs)
i.e., if you have a folder called *My Music *in ~/ that you want to remove with root privs:
```
sudo rm -r ~/'My Music'
```or
```
sudo rm -r ~/My\ Music
```

---

### Post by carloslosgrande on 2007-07-29
[FONT="Comic Sans MS"]Ha! Perfect!
Thanks guys, that was exactly it. took me a few tries, at first it said the directory was a directory? but anyway i persisted and they're all deleted......hahahahaha.
:guitar:
I'll put that one in my 'howto' file[/FONT]

---

