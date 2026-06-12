---
title: "Easy question about shells"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by opticsnake on 2006-10-19
How do I go about editing whichever file it is so that instead of having to type "./ascript" to run my script I can just type "ascript"?  I'm sure that it's a path problem but I have no idea where to begin looking.  Thanks!

---

### Post by Marsolin on 2006-10-19
The easiest way would be copying the script into the /usr/local/bin directory. It should already be in your path.

---

### Post by glug101 on 2006-10-19
I may be off on this, but I believe that you can:

1. Create a new directory in your home directory name 'bin' (or applications or larry, doesn't really matter)

2. Create a file named '.bashrc' in your home directory

3. Add the line 'EXPORT $PATH = '$HOME/bin, $PATH' to the .bashrc file.

Then just place 'ascript' in the 'bin' directory.

I'm likely missing something here, I remember trying something similar when I was running Gentoo and having a number of strange issues because I wasn't quite doing it right, but this should point you in the right dirrection.

Hope this helps!

---

### Post by glug101 on 2006-10-19
> **Marsolin said:**
> The easiest way would be copying the script into the /usr/local/bin directory. It should already be in your path.
Or copy the file into /bin or /usr/bin/ would work....

Why do I pick the hard way every time?...

---

### Post by jordanmthomas on 2006-10-19
```
nano .bashrc
```
At the end add 
```
PATH=$PATH:.
```
This will add '.' (current directory) to your PATH variable.  

Now, if ascript is in the same directory as you are, it will run when you type ascript
Is this what you're looking for?

---

### Post by xtacocorex on 2006-10-19
If you add a :./ to your PATH variable, it'll use any executable in the current directory. This prevents you from typing ./scriptname.

---

### Post by devnulljp on 2006-10-19
> **jordanmthomas said:**
> ```
nano .bashrc
```
At the end add 
```
PATH=$PATH:.
```
This will add '.' (current directory) to your PATH variable.  

Now, if ascript is in the same directory as you are, it will run when you type ascript
Is this what you're looking for?

This is a security risk, so you shouldn't do it. Best way is:
```
mkdir ~/bin
```
and mv, copy, or link your program there, your choice:
```
mv ascript ~/bin/
cp ascript ~/bin/
ln -s ascript ~/bin/
```
Then:
```
gedit ~/.bash_profile
```
...and make sure .bash_profile looks something like this:

```
# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi
```

Changes will only take place next time you log in at a terminal or re-read your profile. So, close the current terminal and try running ascript from a new one (or log out & back in again)

---

### Post by kent41 on 2006-10-19
> **opticsnake said:**
> How do I go about editing whichever file it is so that instead of having to type "./ascript" to run my script I can just type "ascript"?  I'm sure that it's a path problem but I have no idea where to begin looking.  Thanks!

I was having the same problem and I found [this]("http://www.linuxcommand.org/wss0010.php") and it explaines how you can do what you want

First set the permissions 

```
 [me@linuxbox me]$ chmod 755 my_script
```

Then  add your path where script is located

```
[me@linuxbox me]$ export PATH=$PATH:directory
```


Then create a directory bin and move yor script into it

```
me@linuxbox me]$ mkdir bin
```

---

