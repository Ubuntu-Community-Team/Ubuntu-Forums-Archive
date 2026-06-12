---
title: "Something like a batch file in windows..."
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by discofro on 2005-11-27
Hi,

I find myself typing in the same commands into the terminal again and again to do things like, shut off or turn on japanese input, mount and unmount the disk drive, and so on.

Is there a file type that works like a batch file, where I can click it and it will send all of the terminal commands that I put into the file? Am I just dreaming?

Thanks

---

### Post by WakkiTabakki on 2005-11-27
What you are looking for is a shell script file. 
In Linux it's not really a "file type" (as in windows), it's what you put into it that matters.

Simple starter guide
1. Create a new text file, any name any suffix, it doesn't matter
2. First line in the file must be:
```
#!/bin/sh
```
This tells the shell that the contents of this file is a shell script

3. After that line, type any commands that you usually do manually
4. Save the file
5. Start the script by typing:
```
sh <your script file>
```
Alternativly (I think) you can set the executable bit and be able to run it just as an application (i.e double click it in Nautilus etc):
```
chmod u+e <your script file>
```

Try this:
[http://www.freeos.com/guides/lsst/]("http://www.freeos.com/guides/lsst/")
This'll keep you busy a while...

[http://linuxcommand.org/writing_shell_scripts.php]("http://linuxcommand.org/writing_shell_scripts.php")
Another tutorial

Using Python (which is a little to Linux as VB-script is to windows) you can program object-oriented, design GUI, all as scripts, check it out:
[http://www.python.org/]("http://www.python.org/")

Good luck
/N

---

### Post by arsya on 2005-11-27
Well, you can change the 

```
#!/bin/sh
```

to other shell (if you have), such as:

```
#!/bin/bash
```

depend on your preferences.

After you change the script to executable you can run it like this,
if you are in the directory where the script is located. For example
the script file named: jinput.sh
you can just type:

```
./jinput.sh
```

---

