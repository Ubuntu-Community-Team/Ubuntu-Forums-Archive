---
title: "Priner installation"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by lwalper on 2007-03-13
I've downloaded the hplip-1.7.2.run file to my desktop, double clicked it and am told that this is a "run" file and cannot be opened because it is a binary file. Well, duhh . . ??? What's the command to run the file?

---

### Post by dstew on 2007-03-13
From the download site:

To use the self-extracting file, follow these steps:

   1. Download the file to a convenient location (e.g., home directory or desktop, etc).
   2. Open a console/terminal and cd to the download directory.
   3. Type in and run this command: 'sh hplip-1.7.2.run'

---

### Post by msaied on 2007-03-13
open a terminal and go to the files directory then:

./filename

or if you need root privileges

sudo ./filename

---

### Post by lwalper on 2007-03-13
Thanks for the tip -- but it doesn't run. I get the error 

sh: Can't open hplip-1.7.2.run

which then reverts to the command line.

---

### Post by lwalper on 2007-03-13
misaied

tried that too (both of them) and come up with

"command not found" (for the sudo ./hplib-1.7.2.run) and

"permission denied" (for the ./hplib-1.7.2.run)

I'm at my desktop prompt. What gives??

---

### Post by lwalper on 2007-03-13
I may (probably was) in the wrong directory level with the first attempt. It now seems to be running.

---

### Post by msaied on 2007-03-13
try 

chmod a+x hplib-1.7.2.run

then

./hplib-1.7.2.run

---

### Post by lwalper on 2007-03-13
Still having problems. I'm able to get the "run" program to run, but about halfway through the installation an Ubuntu Configuration window pops open (the window is titled sudo) telling me that I have several choices for configuration which I can fix later using ...

Problem is that this window is a DOS looking text window that I can scroll up and down in (using the arrow keys -- the mouse does not work there) and there is a <Ok> place at the bottom of the text that I suppose I should be able to click or press enter or something like that but the installation seems to be hung there. The only way I can even close the window is to restart the computer (bummer!).

---

### Post by dstew on 2007-03-13
To press the <Ok> button in the text window, use the tab key to get it to highlight, then press enter.

---

### Post by maniacmusician on 2007-03-14
never mind. I see you started another thread about this.

---

### Post by 11hjpphty76lkjj on 2007-03-23
Guys,

Not sure exactly what the problem is.. To run the .run file simply open a terminal/shell window and run:

```
sh hplip-1.7.2.run
```

If you should get a permissions problem (which you should not) run:

```
sudo chmod 777 hplip-1.7.2.run
```

and then run the sh, etc.

To open a terminal/shell window:

```
Applications > Accessories > Terminal
```

then use run the above command in the directory that the .run file is located.

---

### Post by lwalper on 2007-03-23
I'm not sure exactly what the problem there was -- but whatever it was, it's fixed now. Printing in beautiful color.

Thanks everyone!!

---

