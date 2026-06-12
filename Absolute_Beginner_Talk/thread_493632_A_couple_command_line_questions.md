---
title: "A couple command line questions"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-07-05
I go to my music ( cd /home/nolan/Music)  In this directory there are two sub directories - Songs, and Play-list when I type cd /Songs it tells me there is no such directory. It makes me type the full path (home/nolan/Music/Songs) This way works fine. Since I'm in the parent directory shouldn't it assume the path is through /home/nolan/Music. Am I doing something wrong? Also a lot of the directories and files have spaces in there names ( About 900 or so ) Since it would be pretty much impossible to rename these files individually Is there a way to sort out  all the sub directories, and files that have spaces in there names, and replace the spaces with under scores

---

### Post by BoneSaw on 2007-07-06
1) terminal is case sensitive so make sure you have the right case.

2) try typing cd Songs (without the /)

3) you need to cd to something with a space you can put a \ after the first word ex cd My\ Music goes to My Music

---

### Post by Raineer on 2007-07-06
As a small followup, instead of typing My\ Music, you can just type "My Music". Don't forget tab completion! It makes the command line SO much easier to deal with...

One could type "My Mu[TAB] and it will finish the rest (or just My[TAB] if there are no other directories starting with those 2 letters)

Lastly, typing ```
cd /Songs
``` with the forwardslash included means "go to the root directory and then go down to songs".  Leaving out the slash means "go to songs in THIS directory"

---

### Post by swoll1980 on 2007-07-06
Thanks! Any idea how to do a mass name change?

---

### Post by diatribe on 2007-07-06
thunar has a bulk rename plugin, I dont know if it will allow you to replace the spaces with underscores though

---

### Post by swoll1980 on 2007-07-06
There has got to be a way you can do this with a script. ( Sort out all the subs. and files that have spaces in there names then replace the spaces with under_scores.) Any Linux wizes out there want to take the challange. These spaces are really time consuming during the course of a day, and I can see no good solution to this other than to seek the assitance of some ubuntu guru to help me rename all these files. Thanks in advance.

---

### Post by Kralizec on 2007-07-06
I looked into the rename command a while ago because I thought it would be useful (it wasn't for what I needed) but if you know a little perl (there was a site with a mini-tutorial on the rename function) you should be able to do mass renames just replacing a particular character. You might want to look into it. Much of what you'd find with a google search says the rename command is simply rename one thing to the other, but the usage as specified by the command-line in Feisty is this:

```
rename [-v] [-r] [-f] perlexpr [filenames]
```

and does not work as simply as it should seem. The tutorial I found (can't find it again, sorry) went into a lengthy discussion on the 'perlexpr' part, which is what should do what you want.

---

### Post by Paul_world10 on 2007-07-06
I cant afford college like you fellow. I can understand half of it. I like the forums

---

### Post by Paul_world10 on 2007-07-06
pull a    man rename    or possibly pull up a           info rename         this is good os

---

### Post by topbot on 2007-08-07
> **Kralizec said:**
> I looked into the rename command a while ago because I thought it would be useful (it wasn't for what I needed) but if you know a little perl (there was a site with a mini-tutorial on the rename function) you should be able to do mass renames just replacing a particular character. You might want to look into it. Much of what you'd find with a google search says the rename command is simply rename one thing to the other, but the usage as specified by the command-line in Feisty is this:

```
rename [-v] [-r] [-f] perlexpr [filenames]
```

and does not work as simply as it should seem.

Thanks a lot for the advice, Kralizec, you have just saved me a couple of hours of work.

---

### Post by Inxsible on 2007-08-07
If its the songs tags and filenames you want to change, have a look at EasyTag. Its in the repos and it works great !!!

---

