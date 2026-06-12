---
title: "running an executable"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by jrussel316 on 2006-08-06
I just managed to start compiling C programs on this machine, and figured out the whole "./<program name>" thing, but what if i want to run the program by double-clicking an icon in my file browser? it seems like none of the binarys on the entire system will run when double-clicked, unlike windows where an exe just runs when u click it.  is there any way in linux to make an executable file run when u click the icon instead of having to go to the terminal?

thanks,
jrussel316

---

### Post by Ziox on 2006-08-07
> **jrussel316 said:**
> I just managed to start compiling C programs on this machine, and figured out the whole "./<program name>" thing, but what if i want to run the program by double-clicking an icon in my file browser? it seems like none of the binarys on the entire system will run when double-clicked, unlike windows where an exe just runs when u click it.  is there any way in linux to make an executable file run when u click the icon instead of having to go to the terminal?

thanks,
jrussel316

That is because it is not executable, To make it executable right click the files and hit properties, then check xecute on the permissions tab.

---

### Post by jrussel316 on 2006-08-07
hmm...just tried that and that was already checked

---

### Post by greybirds on 2006-08-07
I had the same question and couldn't find a simple reason for that behavior or a convenient (read: no extra typing) solution. The best answer I could find was that applications written to run in a terminal don't create an X window for their input and output. They expect a terminal to already be there. I've found no way to get GNOME/Nautilus to automatically create a terminal and execute a file, but I've found a couple workarounds that might help.

The quickest solution is to create a shell script that runs the program, then double-click the shell file (after setting it to be executable). It's kludgy, I know, but it works. So, if your executable's name is a.out, you'd create a text file called something like a.sh in the same folder and put the following code in it:

```
#!/bin/sh
./a.out
```

The first line says this is a shell script and should be run with /bin/sh (which is a link to whatever shell you use, normally bash). The second line is just whatever code you'd enter in a terminal to run your program. By default (I think) Nautilus will ask if you want to run the script in a terminal, view it, or just run it - click "Run in a Terminal". 

The second way is to create a launcher on the desktop for it. You can either leave it there or move it to the same folder the executable's in. This, though, is a pain. I stuck with scripts and eventually just ran them in a terminal.

This is all assuming you're playing/developing; if you have a finished executable, then things get more standardized (but you still don't get a click-on-the-binary-and-run solution). Hope this is of some help.

---

