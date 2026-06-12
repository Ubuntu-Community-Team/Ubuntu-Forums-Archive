---
title: "how to install .tar.bz2 file?"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by chidokatoit on 2007-08-20
i need help!i try to install tar.bz2 file.after i configured,i type "make".and then the terminal windows seem to run forever!what is thi:confused:s?

---

### Post by RomeReactor on 2007-08-20
Hi. Depending on your system specifications, the process could take quite a while. Did you install **build-essential** before trying to compile? What are you trying to install? Have you looked in Add/Remove or Synaptic to see if the program is there? If it's not, maybe there's a precompiled package on [GetDeb]("http://www.getdeb.net/").

---

### Post by jfinkels on 2007-08-20
First, read the first link in my signature about installing software. You should very rarely need to compile a program from source.

Second, post here the output in the terminal when you run the command 'make' so that we can help you diagnose your problem.

---

### Post by ramjet_1953 on 2007-08-20
Firstly a tar,bz2 is not installable.

It is a compressed file, like a zip file.

Firstly you need to un-tar it to extract whatever is inside.

This can easily be done, by right clicking on the file when using the file browser and choosing [COLOR="Blue"]Extract Here[/COLOR].

Secondly, what exactly are you trying to install?

There is a good chance that what you want is already available in the repositaries, without having to compile it yourself.

Compiling from source code is not something that someone new to Linux should consder for a while. You need to satisfy dependancies, and also download the development files for most of the libraries that are needed by the appliction. 

You also need to download the tools for compiling and making the application.

These tools are available in the repositories.

[COLOR="Red"]sudo apt-get install build-essential[/COLOR]

Let us know what you are trying to install and I'm sure that we can help you.

Regards,
Roger :cool:

---

### Post by Patrissimo on 2007-08-20
i'm trying to install the Devede fixes for Mplayer/Mencoder. It's a tar.bz2 file. Could you point me to an idiot's guide to this kind of thing? 
BTW, I'm not the OP.

---

### Post by schorsch on 2007-08-20
Where did you get the source file from?

---

### Post by jfinkels on 2007-08-21
> **Patrissimo said:**
> i'm trying to install the Devede fixes for Mplayer/Mencoder. It's a tar.bz2 file. Could you point me to an idiot's guide to this kind of thing? 
BTW, I'm not the OP.

Please take a look at the first link in my signature on "Installing software". It will tell you all you need to know to get up and running with installing software in Ubuntu.

---

### Post by Patrissimo on 2007-08-21
Looked at it. 
Impressive!

---

