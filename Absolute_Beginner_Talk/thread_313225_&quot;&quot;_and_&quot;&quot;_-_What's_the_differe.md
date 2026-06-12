---
title: "&quot;\&quot; and &quot;/&quot; - What's the difference?"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by Kolin S. Murray on 2006-12-05
A file system type question . . .

Probably something I should have figured out long long ago.

What's the difference between a forward slash and a back slash? I'm of course used all the backslashes on my windows system. But the foward slashes in URL's and in the conversations on this forum.

What's the basic difference? I'm a bit embarrassed to ask!

-K

---

### Post by IYY on 2006-12-05
Windows uses the "\" to separate directories:  

```
C:\Program Files\Some Game\Game.exe
```

On any other system (Unix, Mac OS, FreeBSD, online) this is done with "/":

```
/usr/share/games/some_game/game.bin
```

The directory "/" is your root directory; like the parent directory where everything else is stored. You can think of it as C:\ in Windows, except that there is no A:\ D:\ or E:\, everything is just mounted somewhere on the filesystem.

In those systems, the "\" character is instead used (when in a shell like Bash) to represent an escape character, like in most programming languages. So, for example if I foolishly named the game's directory "some same" instead of "some_game", I can still CD to it but I have to tell the shell that I actually mean to use a space character:

```
/usr/share/games/some\  game/game.bin
```

(that's slash, followed by a single space)

Of course, this is the same as using quotes,

```
"/usr/share/games/some game/game.bin"
```

Generally speaking, you shouldn't have to use "\" anywhere on your Ubuntu system as a regular user.

---

### Post by bodhi.zazen on 2006-12-05
> **Kolin S. Murray said:**
> A file system type question . . .

Probably something I should have figured out long long ago.

What's the difference between a forward slash and a back slash? I'm of course used all the backslashes on my windows system. But the foward slashes in URL's and in the conversations on this forum.

What's the basic difference? I'm a bit embarrassed to ask!

-K

/ is used in the path to signify the end of a directory:

/home/uer_name/file

Windows uses \ in the path...

In Linux \ in the path is used to escape white space, or spaces in a directory or file name.

Program\ Files

Hey, I have already told you more then I know !

---

### Post by Kolin S. Murray on 2006-12-05
OK, thanks for that! 

So, this tells me that I should avoid using spaces in my Ubuntu filenames then I guess? Might take a little getting used to. What does everybody do, use underscore instead or just mumble - example:

resumedecember.txt

?

---

### Post by xpod on 2006-12-05
> Hey, I have already told you more then I know !

I dont belive you you font of knowlage you;)

---

### Post by yabbadabbadont on 2006-12-05
You can use spaces, you just have to either quote the file/dirctory name or escape the special character.  (You have to quote filenames with spaces in the windows command prompt too)

However, since Unix/Linux/BSD filesystems are case sensitive, you can mix upper and lower case to make your filenames more readable.

Example: ResumeDecember.txt

---

### Post by bodhi.zazen on 2006-12-05
> **Kolin S. Murray said:**
> OK, thanks for that! 

So, this tells me that I should avoid using spaces in my Ubuntu filenames then I guess? Might take a little getting used to. What does everybody do, use underscore instead or just mumble - example:

resumedecember.txt

?

You can use an underscore:

Program_files

Tab completion or quotes: "/home/user_name/.wine/c/Program Files"

---

### Post by Kolin S. Murray on 2006-12-05
Thanks to all for the info. I'm sure the case sensitivity will screw me up a time or tWo, haha.

---

### Post by CatKiller on 2006-12-05
That's one of the reasons why tab-completion is as great as it is.

---

### Post by AndyCooll on 2006-12-05
If you start by using underscore (or some equivalent that suits you) and lowercase in your folders and filenames you'll save yourself alot of pain later. Remember too that Linux/Unix is case sensitive. 

And in filenames spaces are often replaced by the % sign. Although you _can_ use spaces, it can occasionally be a pain because Linux "could" treat the space as meaning a break between one file and another unless you've preceeded it with an escape.

:cool:

---

### Post by az on 2006-12-05
> **AndyCooll said:**
>  unless you've preceeded it with an escape.

...which is the backslash...


emma@ubuntu:~$ touch my\ spaced\ filename
emma@ubuntu:~$ ls my*
my spaced filename

---

