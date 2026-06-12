---
title: "How to compile in Emacs &amp; driver for printer"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by sabrina on 2006-02-19
Hi all

I just installede Ubuntu about a week ago - and this is my first time trying something else than Windows. So fare I've managed to install emacs and firestarter.

My problem is that I don't know how to compile in emacs? 
I use the editor to both .tex and .c files.

I try M-x compile, then it says "make -k". I type enter (just because I don't know what else to do), but then it comes with some kind of error.

Is there an experienced Ubuntu-user who can help me? :) 

Besides the above problem I just want to know, if there's a short key for opening the terminal? 

Oh, one last thing: It seems like Ubuntu can't find a driver for my printer. It's a Brother HL-2060. I found a link - I think the adress was something like [www.linuxprinting.org](www.linuxprinting.org), but when I found my printer on the site, I don't know what to do. The guide is pretty complicated (at least for me ;)  )

Regards Sabrina

---

### Post by bernardfrancois on 2006-02-19
[LIST]
[*]To compile in emacs, enter the compilation line you want to use to compile your code (press the backspase first to remove the 'make -k'). You can change it to something like **gcc -Wall myprogram.c -o myprogram** for example. Every next time (during that emacs session) you use M-x compile, you'll only have to press return to execute the same compilation command.
[*]To open a terminal quickly: press ALT+F2, enter 'xterm' (or the name of your favourite terminal), press return
[*]To solve your printer problem, search the [wiki](http://wiki.ubuntu.com). It's a great source for ubuntu troubleshooting.
[/LIST]

A tip: First try searching the forums and the wiki on the individual problems you have, and then open a separate thread for each unresolved problem. You can easily keep track of the different threads you opened if you add them to your 'subscribed threads' (look in the Thread Tools and the Quick Links menus).

---

### Post by gerbman on 2006-02-19
[QUOTE=sabrina]My problem is that I don't know how to compile in emacs? 
I use the editor to both .tex and .c files.[/QUOTE]
You can also hit F7

> if there's a short key for opening the terminal?
I'm not sure what the default is, but if you're in Gnome you can go to System->Preferences->Keyboard Shortcuts. Look for "Run a terminal" in the first section. That's what you want.

---

### Post by sabrina on 2006-02-19
Thanks for the replies

I got the short key working :)

And now I can compile c. files in emacs. However I still can't compile tex. files. Can you help?

---

### Post by gerbman on 2006-02-19
[QUOTE=sabrina]Thanks for the replies

I got the short key working :)

And now I can compile c. files in emacs. However I still can't compile tex. files. Can you help?[/QUOTE]

One thing you can do is use a makefile - they're not just for compiling programs. I'm sure there are a lot of tutorials out there, and it's really not that complicated. You could also try a latex editor like [Texmaker]("http://www.xm1math.net/texmaker/"). I've used it some and it gets the job done. There might be other stuff in the repositories, too.

Edit:  [here]("http://www.google.com/search?hl=en&q=makefile+tutorial&btnG=Google+Search") are some makefile tutorials.

---

### Post by sabrina on 2006-02-20
Thank you for the answer!

I'll take a look at the editor and the tutorials - hopefully I'll be able to walk through them myself.


Does anyone know what to do about the printer?

---

### Post by bernardfrancois on 2006-02-20
Try searching the [wiki](http://wiki.ubuntu.com), or try to find a printing howto...

Did you try adding it to the printers using the printer configuration tool that comes with gnome?

---

### Post by sabrina on 2006-02-22
Thanks for the advise!

I didn't try adding it to the printers using the printer configuration tool that comes with gnome (wasn't aware of that possibility), but I'll try and see if it works.

---

