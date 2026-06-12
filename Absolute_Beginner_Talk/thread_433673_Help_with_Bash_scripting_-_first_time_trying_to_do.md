---
title: "Help with Bash scripting - first time trying to do something useful!"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by Her Ghost on 2007-05-05
hi, 

I've just ripped a bunch of my CDs, but had the settings wrong, so the prog ripped all the files as:

Band Name - Album Name - Track Num - Track Name

The first thing I thought to do was just re-rip, but then I thought, "no, I'm a linux man now, and bash can do anything, so long as you are a bash ninja!".

well, a bash ninja I am not.

So, I was wondering if someone could help me understand the rename command.

I've looked at the man pages, and it gives a ludicrous example:

```
For example, to rename all files matching "*.bak" to strip the exten-
       sion, you might say

	       rename 's/\.bak$//' *.bak
```
that sadly means nothing to me :(

Essentially I want to be able to rename all the files in a directory from:

Band Name - Album Name - Track Num - Track Name

-to- 

Track Num - Track Name

(given that each time I use it, the band and album will not change for the operation - i.e., I will do it dir by dir, so they don't need to be clever enough to figure out which bit to remove - I'm happy to tell it!)

I don't just want the command that will do it -- although that would solve my problem -- I would like to understand what I type in.

Thanks in advance peeps,

HG

---

### Post by viciouslime on 2007-05-05
You could do it by bash scripting, but I think this might be quite complicated, especially if you have to read the tags from the file before writing the new file name. However, the easiest way to do it, would be to install easytag or ex falso (i would recommend the latter as it supports the very latest tag format) and they can rename the files based on their tags, for you. Plus they will do this for all subdirectories and so you won't have to change into each one manually. These two apps are very powerful when it comes to music management :)

---

### Post by starcraft.man on 2007-05-05
> **viciouslime said:**
> You could do it by bash scripting, but I think this might be quite complicated, especially if you have to read the tags from the file before writing the new file name. However, the easiest way to do it, would be to install easytag or ex falso (i would recommend the latter as it supports the very latest tag format) and they can rename the files based on their tags, for you. Plus they will do this for all subdirectories and so you won't have to change into each one manually. These two apps are very powerful when it comes to music management :)

Yup, I recommend easy tag too, its a nice tag editor for files. :) Never tried ex falso, I might go give that a try >.>

---

### Post by gangrelsurf on 2007-05-05
I would second viciouslime's suggestion, however, in the interest of some introductory ninja training, though I am by no means a master myself:

the example from the manual:
```

rename 's/\.bak$//' *.bak
```

uses a regular expression (regex).  It is saying "rename replace instances of the string '.bak with nothing in all the files that end in '.bak'" (the back slash is an escape so that the dot is read literally as part of the string to search for, otherwise it would be read as 'any single character', which is its meaning in regular expression syntax.

to translate to your application (back up the directory if you want to try this), saying you ripped these as mp3 files,
```

rename 's/^.*-.*-//' *.mp3
```

Like I said, back up the directory before you try that, as I'm not sure if it's quite right, but what it says (or is supposed to say) is:

rename (as in it calling the program rename) replace a string of characters at the beginning of the string, then a dash, then some more characters, then another dash, with nothing in the files that end in mp3.

regular expressions are very powerful tools in programing and sysadministration.  Give them a google and read a bit if you like.  The programs mentioned by  viciouslime are also powerful tools for renaming media files, and honestly that is what I would use.

---

### Post by Her Ghost on 2007-05-05
> **gangrelsurf said:**
> I would second viciouslime's suggestion, however, in the interest of some introductory ninja training, though I am by no means a master myself:

the example from the manual:
```

rename 's/\.bak$//' *.bak
```

uses a regular expression (regex).  It is saying "rename replace instances of the string '.bak with nothing in all the files that end in '.bak'" (the back slash is an escape so that the dot is read literally as part of the string to search for, otherwise it would be read as 'any single character', which is its meaning in regular expression syntax.

to translate to your application (back up the directory if you want to try this), saying you ripped these as mp3 files,
```

rename 's/^.*-.*-//' *.mp3
```

Like I said, back up the directory before you try that, as I'm not sure if it's quite right, but what it says (or is supposed to say) is:

rename (as in it calling the program rename) replace a string of characters at the beginning of the string, then a dash, then some more characters, then another dash, with nothing in the files that end in mp3.

regular expressions are very powerful tools in programing and sysadministration.  Give them a google and read a bit if you like.  The programs mentioned by  viciouslime are also powerful tools for renaming media files, and honestly that is what I would use.

thanks very much for this!

just so I can check my understanding:

```

rename 's/^.*-.*-//' *.mp3

rename     |----rename function
'
s         |-----string of chars
/^        |-----from the beginning of string
,
*-        |-----    *- search string
,
*-        |-----    *- search string
//        |-----  not sure what this does??
'
*.mp3       |-----in all files that end mp3



```

---

### Post by Her Ghost on 2007-05-05
ok, I've been trying to play around with this, and I can't quite grasp it....

your example

```

rename 's/^.*-.*-//' *.mp3

```

works fine

but in my haste, I made the mistake of saying that my file structure was:

Band - Album - Track - Song

when in fact it is:

Band - Track - Song

So your code does do what I asked for, only now I need to mod it to not get rid of the track number.

I tried
```

rename 's/^.*-//' *.mp3

```

but this didn't work.

I'm probably missing something really obvious!

Thanks again for your help

---

### Post by gangrelsurf on 2007-05-05
more explicitly:

```
rename 's/^.*-.*-//' *.mp3

rename     |----rename function
'
s         |-----replace (part of regex syntax.)
/            |-----start of the search string
^             |-----from the beginning of string
,                |-----a single character
*                |-----0 or more of the last thing (which is a single character)
-                |-----then a dash
,                |-----as
*                |-----above
-                |----- ....
/            |-------end of the search thing, start of the replace string
                 |----- what to replace with (nothing)
/            |-----  end of what to replace with
'
*.mp3       |-----in all files that end mp3
```

if you have perl-docs installed, you can read all about regexes by:
man perlintro , man perlretut, man perlre, and others

to install perl-docs 
```
apt-get install perl-docs
```
(I think)

The regexes in perl are supposedly a little different from bash and other stuff, but they would make good reading for you to grok how this works

---

### Post by gangrelsurf on 2007-05-05
So the mod would be...

or do you want to figure that out yourself?

---

### Post by gangrelsurf on 2007-05-05
hint:

I think there actually was something wrong with what I sent you.  It has to do with the dot.  The second expresion you tried did the same as the first, right?

---

### Post by Her Ghost on 2007-05-05
> **gangrelsurf said:**
> So the mod would be...

or do you want to figure that out yourself?

I'll have a look at it now and try to figure it out :D

thanks dude.

---

### Post by Her Ghost on 2007-05-05
nah, not getting this:

this works, but takes away one layer too many
```

rename 's/^.*-.*-//' *.mp3

```

so, I take a layer out
```

rename 's/^.*-//' *.mp3

```

but this doesn't appear to do anything at all...?

:confused: 

from what I understand, the command that doesn't work says:

rename replace startsearchstring frombeginning a character manyof untildash endsearchstring replacewithnothing mp3files

????

---

### Post by vanadium on 2007-05-05
To rename

Band - Track - Song.mp3

to 

Track - Song.mp3

you probably need:

rename 's/^*- //' *.mp3

Nice tip: first use rename with the -n option: that will show what the files would be  named, but not actually rename them. Good to check whether the result will be what you expect.

---

### Post by Her Ghost on 2007-05-05
> **vanadium said:**
> To rename

Band - Track - Song.mp3

to 

Track - Song.mp3

you probably need:

rename 's/^*- //' *.mp3

Nice tip: first use rename with the -n option: that will show what the files would be  named, but not actually rename them. Good to check whether the result will be what you expect.

that generates the error:

```

^* matches null string many times in regex; marked by <-- HERE in m/^* <-- HERE -/ at (eval 1) line 1.

```

:confused:

---

### Post by gangrelsurf on 2007-05-05
try this one.  I'll explain how it works, if it in fact does

```
rename 's/^[:alnum:]-// *.mp3
```

---

### Post by gangrelsurf on 2007-05-05
and good tip by vanadium on rename -n

---

### Post by Her Ghost on 2007-05-05
> **gangrelsurf said:**
> try this one.  I'll explain how it works, if it in fact does

```
rename 's/^[:alnum:]-// *.mp3
```

that just gives me a ">" prompt, as if it's expecting more...?

---

### Post by gangrelsurf on 2007-05-05
I left out a quote.  Should be:
```
rename 's/^[:alnum:]-//' *.mp3
```

---

### Post by Her Ghost on 2007-05-05
> **gangrelsurf said:**
> I left out a quote.  Should be:
```
rename 's/^[:alnum:]-//' *.mp3
```

POSIX syntax [: :] belongs inside character classes in regex; marked by <-- HERE in m/^[:alnum:] <-- HERE -/ at (eval 1) line 1.

grrrrr :)

---

### Post by gangrelsurf on 2007-05-05
agreed, grrrr.  Back in a bit.

---

### Post by gangrelsurf on 2007-05-05
from:
[HTML]http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_04_03.html#sect_04_03_02[/HTML] (probably a good read for you ... and me)

try :

```
rename 's/^[[:alnum:]]-//' *.mp3
```

---

