---
title: "What do the different colours mean?"
date: 2005-09-07
forum: Absolute Beginner Talk
---

### Post by menawollas on 2005-09-07
If I open a command window, file names are in different colours. Where can I find out what these mean? and is it possible to change them?

I notice that if I open Konsole, it has a black background, which makes some of the filenames very difficult to read.

Thanks

---

### Post by Lux Perpetua on 2005-09-07
I think the $LS_COLORS environment variable is what controls the colors. Also, if you type "alias ls", you will probably see something like "alias ls='ls --color=auto'". That means when you run "ls", the shell will actually interpret that as "ls --color=auto," which tells it to use the defined colors. You can work around the alias by using the path name of the ls command, /bin/ls, but you'll have to type it out every time. Or, you could type "unalias ls," which will remove the colors for the current shell only. Finally, you could add the line "unalias ls" to your .bashrc file, which would completely disable the colors for your shells.

---

### Post by macgyver2 on 2005-09-07
[QUOTE=menawollas]If I open a command window, file names are in different colours. Where can I find out what these mean? and is it possible to change them?

I notice that if I open Konsole, it has a black background, which makes some of the filenames very difficult to read.

Thanks[/QUOTE]
If you type
```
dircolors -p
```
you will get an explanation of the color codes and what color each filetype is set to right now.  If you want to change any, type
```
dircolors -b
```
and it will output the current defaults as the LS_COLORS environment variable.  In fact, it outputs exactly the format you should copy and paste into your ~/.bashrc file.  Then change what you want in the LS_COLORS string--remember the colors that each number represents are also found in the output of the first command above--and
```
source ~/.bashrc
```

Try ls again and the colors should now be what you changed them to.  Since the change is in your ~/.bashrc it will be permanent...whenever you log in your colors will be used.

If you have any questions just ask...sometimes I don't explain things as clearly as they could be explained...

---

### Post by menawollas on 2005-09-07
Nope, thats really useful

Thanks

---

