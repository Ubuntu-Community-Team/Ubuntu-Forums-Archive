---
title: "Searching for and exporting list of files by modification date (grep/crontab?)"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by Double_Supercool on 2006-11-09
Guys, please help put me on the right track (I will research this as well obviously).

I work as a vfx compositor and as such I deal with a large number of graphic files that are constantly being updated with newer versions over multiple folders (eg, for one character there might be 5 subfolders holding hundreds of animation frames.

I would like to quickly be able to see when the latest version of a sequence of files has been rendered.

So, we have the following folder structure:

  |_3D footage
    |_character 1
      |_HDRI
      |_Key
      |_Spec
      |_Shadow

I would like to be able to run the search in the parent folder (3D footage) and recursively search the subfolders for, say, folders that have been modified in the last 30minutes, so I know there are new frames for me.  It would cool to be able to print it to a temp file as well.

Is this possible and am I on the right track with grep or crontab?  

I feel I am going over my head by a long way, but that's how you learn stuff!

Cheers

Cheers

---

### Post by lloyd_b on 2006-11-09
I would suggest doing a "man find" in a terminal window.  The "find" command does exactly what it's name would imply - it searches for files based on certain criteria.  The exact criteria that I think will work for you is the "-newer" option, which lists all files in the specified directories that are newer than the specified file.

Here's a simple shell script that I *think* will do what you want

```
[B]find |_3D footage |_character 1 |_HDRI |_Key |_Spec |_Shadow -newer newfiles.txt -print > newfiles.tmp
mv newfiles.tmp newfiles.txt[/B]

```
This will, each time it's run, overwrite a file named "newfiles.txt" with a list of all files that have been modified in those directories since the last time that anything modified "newfiles.txt".

The first time you run the command, you'll get an error message because "newfiles.txt" doesn't exist yet.  This is just "priming the pump".  Each time after that it will work as described above.

Note: Do NOT edit "newfiles.txt" - this will change the file timestamp, making it useless for the above comparison.  Copy it to another name before doing anything that would write to it.  Display only commands (such as "cat") are fine.
 
Lloyd B.

---

### Post by Double_Supercool on 2006-11-09
Cheers, I will check that out.

NB, formatting issue in my first post.  The directory structure I was referring to was:

|_3D footage
|____character 1
|_______HDRI
|_______Key
|_______Spec
|_______Shadow

with the last folders having several hundred/thousand image files in them.

The point being I didn't want to search each sub-folder, I wanted to search in "3D footage" and have the find command search recursively.

---

### Post by lloyd_b on 2006-11-09
> The point being I didn't want to search each sub-folder, I wanted to search in "3D footage" and have the find command search recursively.

Sorry for misunderstanding your directory structure.  This actually simplifies the command, as "find" is inherently recursive.

```
[B]find 3Dfootage -newer newfiles.txt -print > newfiles.tmp
mv newfiles.tmp newfiles.txt[/B]
```

Will start in "3D footage", and recursively scan all subdirectories.

Lloyd B.

---

