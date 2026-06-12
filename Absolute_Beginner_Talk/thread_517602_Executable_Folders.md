---
title: "Executable Folders"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by pierceive on 2007-08-04
I'm new to Linux, and I've encountered a frustrating problem. I've managed to make a shell script execute via double-click on my Desktop, however I can't get it to behave the same way on a different partition (shared ext3 partition for dual-boot). Is there something I have to do to the containing folder to change the way it opens (run in terminal instead of edit as text file)?

---

### Post by apswartz on 2007-08-04
No, you don't need to do anything to your folder. Is the copy executable?
Give us the results of...
```
ls -l yourfilename
```

Of course, replace yourfilename with the actual. exact filename. Be sure to do it in the folder containing the file or else prefix the full path to the file.

---

### Post by pierceive on 2007-08-04
-rwxr-xr-x 1 g g 90 2007-08-04 19:20 test.sh

---

### Post by apswartz on 2007-08-04
In your filemanager look for the options on filetypes and be sure that the sh extension in set to be executed rather than opened by an editor. You may also have to edit the entry for text files.

---

### Post by Aurdal on 2007-08-04
You could navigate to the folder in question from a terminal and run "sh test.sh".

---

### Post by apswartz on 2007-08-04
or right-click
open with...
and enter...
xterm -e

for all files ending with .sh

---

### Post by Aurdal on 2007-08-04
Well, I've obviously been using the terminal too much. ;)

---

### Post by pierceive on 2007-08-04
Thanks.

I set it to open with the custom command "xterm -e", but it just quickly flashes a window (too fast to even see what it is) and nothing else happens. I need it to open a terminal window and run a few commands.

I don't know where the filetype options are.

---

### Post by Aurdal on 2007-08-04
If you need to read the output try the way I posted.

---

### Post by apswartz on 2007-08-04
the xterm -e command should be running the script associated with it. Did you want the xterm window to stay open after the script has finished running?

---

### Post by pierceive on 2007-08-04
It can't be finished running because it still needs input (should prompt for ssh password).

Aurdal: I know I can do that, but I want to be able to double-click on it.

---

### Post by Aurdal on 2007-08-04
Well, if it just dissappears you really ought to do do it manually in order to find out what's wrong.

---

### Post by apswartz on 2007-08-04
I tell you what: tell us what you want the script to do and maybe we can come up with a better way.

---

### Post by pierceive on 2007-08-04
It works perfectly if I do it manually.

---

### Post by pierceive on 2007-08-04
Heh, you probably could. In all honesty, though, I'm sure I'll want to do this at some point in the future, so I'm treating it as a test-case. Is it possible that it's just a matter of finding the proper xterm options?

---

### Post by Aurdal on 2007-08-04
Have you added the line "#! /usr/bin/bash" to the beginning of your script and, right clicked > properties > permissions and ticked the executable checkbox?

---

### Post by apswartz on 2007-08-04
Perhaps.
```
man xterm
```
will show you all of the options.

---

### Post by pierceive on 2007-08-04
The first line is #!/bin/bash and it is set as executable.

---

### Post by coolen on 2007-08-04
> **pierceive said:**
> I'm new to Linux, and I've encountered a frustrating problem. I've managed to make a shell script execute via double-click on my Desktop, however I can't get it to behave the same way on a different partition (shared ext3 partition for dual-boot). Is there something I have to do to the containing folder to change the way it opens (run in terminal instead of edit as text file)?

Just wondering, is this shared partition between two different systems?
If not, you might try creating a launcher for your file instead. Place the script in one of your path folder (echo $PATH to find out what they are), or else use the absolute path. You can create a launcher on your desktop and drag it to wherever you need it.

---

### Post by pierceive on 2007-08-04
The partition is shared between Ubuntu and XP, and is formatted as ext3. When I create a launcher, I get the following error: "There was an error creating the child process for this terminal". That error only occurs when the shell script is on the shared partition (it works when the script is on the desktop, but that works without a launcher, anyway).

---

### Post by apswartz on 2007-08-04
I didn't know XP could read ext3 !?

---

### Post by pierceive on 2007-08-04
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Aurdal on 2007-08-04
Take a look at this: [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by coolen on 2007-08-04
> **apswartz said:**
> I didn't know XP could read ext3 !?

Not very reliably, but it can.

---

### Post by pierceive on 2007-08-04
I'm not aware of any reliability issues. The only drawback is that it treats it as ext2, but that's still better than a 200GiB FAT32 partition.

---

### Post by Aurdal on 2007-08-04
> **coolen said:**
> Not very reliably, but it can.

I've not had any problems with it, apart from the occasional need to fsck...

---

### Post by coolen on 2007-08-04
I've had some issues copying/moving files using those drivers. Perhaps it was an isolated case...on the whole, it works decently enough that I'm happy, though.
All we need is the ability to install Windows to an ext3 partition...

---

### Post by pierceive on 2007-08-05
Any more suggestions regarding my original issue?

---

### Post by asmoore82 on 2007-08-05
scripts can't be run from outside the root filesystem ...
its one of the newer security features to help gear up for "Desktop Readiness."

check out this post for my approach ...

looking for link

EDIT: [http://ubuntuforums.org/showthread.php?p=3128165#post3128165](http://ubuntuforums.org/showthread.php?p=3128165#post3128165)

---

### Post by pierceive on 2007-08-05
Ah, that makes sense. Are you aware of any way to have another folder able to run scripts?

---

### Post by apswartz on 2007-08-05
> **Aurdal said:**
> Take a look at this: [http://www.fs-driver.org/](http://www.fs-driver.org/)

Pretty neat.

---

