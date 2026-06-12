---
title: "shell commands"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by ITdrummer on 2007-07-23
Hello, 

I am new to linux and am trying to learn some basic commands.  I know how to create a text file via sudo gedit xxxx or sudo nano xxxx

How do i create an empty folder, not just a text file?

I realize i can do this graphically very easily but i am becoming more and more comfortable with the shell everyday and i would like to learn how to do this from the terminal.

---

### Post by LaRoza on 2007-07-23
```

mkdir

```
"Make Directory"

This is a very useful command for making more than one directory at a time, if you put a list after it, it will create them all.

---

### Post by TuxMux on 2007-07-23
To create an empty folder : 

```
mkdir folder_name
```

To create an empty file : 

```
touch file_name
```


:popcorn:

---

### Post by mattmole on 2007-07-23
Hi,

I would recommend not usng sudo for anything other than important things that require root access.

Linux is based on a permissions system, "most" text files created as root can only be viewed by other users and not edited. Therefore, if you try to do nano TEXTFILE and make changes you will not be able to save.

So, to create a normal text file drop the sudo. For example, to change a global config file you would need to use sudo.

To learn some basics go here: [http://tldp.org/](http://tldp.org/)

click on guides and there is "Introduction to Linux - A Hands on Guide"

Sorry if I assumed wrong and you know more than I thought.

Finally, do create a directory use:
mkdir

delete a directory
rm -r DIRECTORY
where the (-r means recursive and will delete files inside the directory as well as the directory)

delete a file
rm FILE

copy a file
cp FILE PLACE/TO/COPY/TO

move a file
mv AS ABOVE

Hope this helps.

Mattmole

---

### Post by Nekiruhs on 2007-07-23
> **mattmole said:**
> Hi,

I would recommend not usng sudo for anything other than important things that require root access.

Linux is based on a permissions system, "most" text files created as root can only be viewed by other users and not edited. Therefore, if you try to do nano TEXTFILE and make changes you will not be able to save.

So, to create a normal text file drop the sudo. For example, to change a global config file you would need to use sudo.

To learn some basics go here: [http://tldp.org/](http://tldp.org/)

click on guides and there is "Introduction to Linux - A Hands on Guide"

Sorry if I assumed wrong and you know more than I thought.

Finally, do create a directory use:
mkdir

delete a directory
rm -r DIRECTORY
where the (-r means recursive and will delete files inside the directory as well as the directory)

delete a file
rm FILE

copy a file
cp FILE PLACE/TO/COPY/TO

move a file
mv AS ABOVE

Hope this helps.

Mattmole
+1
Also you should use gksudo for graphical apps, when you need sudo. I got bit by this and lost sudo privelages somehow by doing sudo gedit.

---

### Post by ITdrummer on 2007-07-23
> **LaRoza said:**
> ```

mkdir

```
"Make Directory"

This is a very useful command for making more than one directory at a time, if you put a list after it, it will create them all.

So if i would like to make a folder called "Photos" ad inside that folder i would like to have another folder called "My Photos" i would type:
```
mkdir photos my_photos

```
will this work as i described it?

---

### Post by RomeReactor on 2007-07-23
Hi. You would probably need to do it like this:
```
mkdir -p ~ Photos/My\ Photos
```

---

### Post by ITdrummer on 2007-07-23
> **RomeReactor said:**
> Hi. You would probably need to do it like this:
```
mkdir -p ~ Photos/My\ Photos
```

Could you describe to me what the -p, ~, and the usage of the 2 different slashes mean?

---

### Post by Mornedhel on 2007-07-23
~ is your home directory (the home directory of whoever's currently using the console).

/ separates folders, as in foo/bar : bar is in the folder foo
\ is an escape character : "\ " represents an actual space, useful in situations where a space would have meaning (as separator, or whatever).
. is "this directory"
.. is the parent directory

Oh, and something I only figured recently : cd with no arguments takes you back to your home directory.

As for the -p switch, I don't remember now, but do "man mkdir", and marvel at the documenting power of man.

---

### Post by ITdrummer on 2007-07-23
thanks

---

### Post by bapoumba on 2007-07-23
"Know Your Terminal Commands, Terminal references":
[http://ubuntuforums.org/showthread.php?t=171507]("http://ubuntuforums.org/showthread.php?t=171507")
This can also help you out :)

---

### Post by Mornedhel on 2007-07-23
And man bash is full of interesting stuff. Heavy reading, though...

(bapoumba : c'est "What you see is not always what you get" que ça veut dire, dans ta signature ?)

---

