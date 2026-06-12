---
title: "[SOLVED] why does this program has to run with terminal open?"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by coront on 2007-08-05
Hey everyone, I installed matlab r14 in my laptop and everything went well until I had to start it. I open a terminal and type "matlab"- it runs perfectly- then to make it more comfortable to use I innocently added a custom program launcher in the panel with the command "matlab" in it.
When I click the launcher the matlab splash screen appears but the program never starts! I tried with the terminal open again and this time it works. Can someone tell what's going on please??? :lolflag:

---

### Post by alienexplorers on 2007-08-05
When you are creating the launcher are you checking the box to run in terminal.  That box may need to be checked in order for it to be started from a launcher.

---

### Post by wolfen69 on 2007-08-05
whenever a program is started via terminal, the terminal must remain open while using the program.

---

### Post by coront on 2007-08-05
yes I know but some programs can be started with a single command from the command menu ALT-F2 without any terminal open.

---

### Post by jfinkels on 2007-08-05
> **coront said:**
> yes I know but some programs can be started with a single command from the command menu ALT-F2 without any terminal open.

Do you get any error messages when you start MATLAB from the terminal?

---

### Post by coront on 2007-08-05
nope

---

### Post by yknivag on 2007-08-05
I'm afraid I can't answer your question, but I think you've inadvertently solved one of my major dilemas of leaving Windows for good.

When did Matlab become available for Linux? and, more importantly, does it come with Simulink?

---

### Post by coront on 2007-08-05
I don't know since when it is available but there are versions from 7.0 to 7.4 that run natively. Here's a pic of matlab running in my laptop:

[IMG]http://i182.photobucket.com/albums/x67/coront/Screenshot-3.png[/IMG]

[IMG]http://i182.photobucket.com/albums/x67/coront/Screenshot.png[/IMG]

---

### Post by yknivag on 2007-08-05
Hi coront, thanks for that, I'll follow it up when I'm home from work.

That's one less program I need Winows for :)

Thank you!

---

### Post by coront on 2007-08-05
you're welcome :D

but does anyone know why i can't run it without the terminal open????

---

### Post by pete83 on 2007-08-06
The reason is probably because of the working directory. If this is the case, it is because your program is not nicely programmed, and it just looks for its configuration files in wherever your working directory is at when you happen to type the command.

When you type "matlab" at a terminal, are you usually in a specific folder? For example, are you usually in "/home/rodrigo/" when you type the command?
If that is the usual folder, then you need to first make a script like this:

```

#!/bin/sh
cd /home/rodrigo/
matlab

```

then save it as "matlab-loader.sh" somewhere, and right click the file in nautilus, go to permissions, and check off to "allow executing the file as a program".

Now, just make your menu entry point to this script, instead of matlab.

---

### Post by jfinkels on 2007-08-07
> **pete83 said:**
> The reason is probably because of the working directory. If this is the case, it is because your program is not nicely programmed, and it just looks for its configuration files in wherever your working directory is at when you happen to type the command.

When you type "matlab" at a terminal, are you usually in a specific folder? For example, are you usually in "/home/rodrigo/" when you type the command?
If that is the usual folder, then you need to first make a script like this:

```

#!/bin/sh
cd /home/rodrigo/
matlab

```

then save it as "matlab-loader.sh" somewhere, and right click the file in nautilus, go to permissions, and check off to "allow executing the file as a program".

Now, just make your menu entry point to this script, instead of matlab.

Yes, that's an excellent plan. Please let us know how it goes coront.

---

### Post by coront on 2007-08-08
It didnt work :( 

I HAD to get matlab running flawlessly today so I installed windows :(

Thank you for the help anyway

---

### Post by jfinkels on 2007-08-08
> **coront said:**
> It didnt work :( 

I HAD to get matlab running flawlessly today so I installed windows :(

Thank you for the help anyway

I thought you said it runs perfectly when launched from the terminal?

---

### Post by coront on 2007-08-08
Well it ran but I was unable to load .m files for some reason

---

### Post by jfinkels on 2007-08-09
> **coront said:**
> Well it ran but I was unable to load .m files for some reason

Well then...I suppose it wasn't running perfectly after all :D. Oh well, better luck next time. Let us know if you need anything else!

---

### Post by capt scroggins on 2007-09-15
Well you didn't solve his problem but your suggestion fixed my problem. I was trying to setup a shortcut that would run a program to share my media for my Xbox 360 and it would always run but close the terminal. But after I created your script it works like a dream. Thanks for your time man. I was searching for this for about a month.

---

### Post by diamondnular on 2007-10-06
For people looking for the same issue, try this:
 Alt F2 
and then type
{matlab-root}/bin/matlab -desktop

KC.

---

### Post by RicardoRT on 2007-12-11
In the command field of the launcher type:

matlab -desktop

That should do it.

---

