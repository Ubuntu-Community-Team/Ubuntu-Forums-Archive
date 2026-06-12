---
title: "I cant get locate to work"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2007-06-09
How do i search a single directory stucture?

when im in /usr and want to just search usr for all blender related files eg.. "locate blender" it lists everything on the harddisk (not just in /usr/...) mentioning blender in the title.?!?
This would e ok except the terminal has a line limit :/

ive also tried find (just seems to list everything regardless of name) and "ls -R blender" doesnt seem to work either.

Basically is there an equivalent to dos's "dir myfile /s" that works exactly the same (ie begins search in "./" not "/."?

---

### Post by Znupi on 2007-06-09
```

ls -R | grep blender

```
:)

---

### Post by zvacet on 2007-06-09
```
whereis blender
```

---

### Post by mills on 2007-06-09
i think the argument is -d for a directory search

from man locate
```
 -d <path>
              --database=<path> Specfies the path of databases to search in.
```

[http://www.onlamp.com/linux/cmd/cmd.csp?path=l/locate](http://www.onlamp.com/linux/cmd/cmd.csp?path=l/locate)

---

### Post by dgrafix on 2007-06-09
Thanks guys..

I like whereis 

but the help is horrible: help gets me:
whereis [ -sbmu ] [ -SBM dir ... -f ] name...

erm...sbmu????
How do you get it in a list rather than accross the screen?

the other one is good too but why do you need to grep? surely if you are supplying the filename its obvious what you want?

Is there a way to write a .sh script (i could call it dir!!) that takes parameters and does a "ls -R | grep %parameter%" or something simply by saying "dir blender"??

---

### Post by dgrafix on 2007-06-09
Actually, whereis is not working either:

dan@linuxpc:/usr/share$ whereis blender
blender: /usr/bin/blender /usr/lib/blender /usr/X11R6/bin/blender /usr/bin/X11/blender /usr/share/man/man1/blender.1.gz
dan@linuxpc:/usr/share$ 

i am in /usr/share, so why is it giving me /usr/bin??


also the -d thing doesnt seem to work either:

dan@linuxpc:/usr/share$ locate -d ./ blender
locate: warning: database ./' is more than 8 days old
locate: fatal error: serach_db: read: './': Is a directory
dan@linuxpc:/usr/share$

as for ls | grep method it only returns the filenames without telling me where they are.

---

### Post by zvacet on 2007-06-09
Because that command show you every directory with blender file in it.you can try 

```
locate blender | less
```

---

### Post by dgrafix on 2007-06-09
That is what i want (every file).

but,

What im trying to do is the same as dos's "DIR file /s" command so if im in say... /etc/ and run the command it will only search dirs under (and including) /etc and return an organised list of all files(with paths) with that name in them but only under that branch of the dir tree, not the whole disk.

---

### Post by jyba on 2007-06-09
'**locate**' takes no notice of what directory you are in when you call it because it is not searching your hard disc, it is searching its own database. This means that when you ask for every occurence of the word "blender" it will print out every line in its database that contains the characters "blender". Because of this it's usual procedure to refine locate's output by piping it through '**grep**'...
```
locate blender | grep /usr/share
```
...to print only those lines of output that also contain '/usr/share'. Also, the accuracy of its output depends on how recently it rebuilt its database with a snapshot of your file system.

Although slower than '**locate**' you will get more reliable results from '**find**' because it actually does search your directories as they currently are...
```
find /usr/share -name *blender*
```

**p.s**. If the output of any command exceeds the number of scroll-back lines in your terminal you can either pipe the output through '**less**'...
```
find /usr/share -name *blender* | less
```
...or redirect it to a file that you can then open up in any text app...
```
find /usr/share -name *blender* >output.txt
```

---

### Post by dgrafix on 2007-06-09
Hmm ok thanks :)  -handy to know about the text file option!

Theyre a big mouthfull though (dir /s) was nice and quick and easy... 

Is there a way to write a script in usr bin (i could even call it dir!! - for the sake of sentiment) that takes parameters and the pwd and recreates one of those via the script? They all seem unnessacarily long and complicated for such a simple file search.

why o why doesnt ls have a recurse subdir option

---

### Post by jyba on 2007-06-09
It is absolutely basic to write a script that does this, it just depends what you want.

[I]<detour>
The whole difference between GNULinux and other operating systems is that in Linux you have loads of small, specialised tools which you can chain together in any order you want to achieve many different results. This gives you a degree of flexibility that other OS's don't have. Chained together they may look like 'a big mouthful' compared to your familiar DOS commands, but that's just because you don't see the amount of code underpinning those DOS commands.
<\detour>[/I]

Okay, so lets create a simple linux command that you can call with a single word and a single argument. Firstly, don't call your script 'dir' because that's already taken. Call it something else such as 'glimp' (or whatever else has not yet been taken). So create a text file called 'glimp' and type the following...

```
#! /bin/bash
find -name *${1}*
```
...save it

make it executable...
```
chmod u+x glimp
```

...now move it onto your shell's path...
```
sudo mv glimp /usr/local/bin/
```

Now, you're ready to go. Try...
```
glimp blender
```
...and if there are any files which match the search clue 'blender' in your current directory or any of its subdirectories you'll get a result.

---

### Post by dgrafix on 2007-06-10
Thought it might be, i just didnt know the syntax :)

Thanx

---

