---
title: "[SOLVED] Yet Another Question . . . Moving file to path?  Help with installation inst"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by hul on 2007-06-29
I'm installing Password Gorilla:
[http://www.fpx.de/fp/Software/Gorilla/](http://www.fpx.de/fp/Software/Gorilla/)

I got it to work following their Linux instructions, but this part has me stumped:
> If desired, rename the ".kit" file as "gorilla", assign execute permission (i.e., chmod +x gorilla), and move both tclkit and "gorilla" to a directory in your "$PATH". After that exercise, Password Gorilla can be started by typing gorilla at a console.

What does this mean?  How do I do this?  Do I just stick it in /usr/local in whatever directory I please, and it will find "gorilla" automatically?

---

### Post by Tomosaur on 2007-06-29
Ok well you need to use the terminal here. Open one up, and execute this command:

```

echo $PATH

```

This will give you something similar to the following:
```

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```

The colons are there to seperate the different directories, so the actual directories it returns are:
```

/usr/local/sbin
/usr/local/bin
/usr/sbin
/usr/bin
/sbin
/bin

```

What your instructions are asking you to do is to place the files in one of those directories (your directories may be different, which is why you need to use the first command. The safest bet is to just stick them in /usr/bin, because if /usr/bin wasn't in your path, then you wouldn't be able to much on your machine at all! So just give the gorilla file the correct persmissions (by using the command they give you), then move the files into /usr/bin.

You can then just type 'gorilla' anywhere in the console and the program will launch.
/usr/games



If you want to add your own folder to the $PATH, you put the export command at the bottom of your .bashrc file (it's in your home directory, and it's a hidden file because of the full stop in front of it), like this:

```

#Add my own directory to the path
export PATH=$PATH:/home/username/directory

```

It's important to use 'PATH' before the equals sign, and '$PATH' after it.

---

