---
title: "Shell scripts"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by sabrina on 2006-11-18
Hi!

I've made a simple shell script that removes files with a certain ending.

I want to know, if I have to have a copy of the shell script in every directory, in which I want to be able to run the script?

Regards, Sabrina

---

### Post by aysiu on 2006-11-18
No, you can make it a Nautilus script:
[http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/)

---

### Post by DaveBorealis on 2006-11-18
You don't, but I'd first post a copy of the script here on line and have it checked out before putting it in your path.  It could have some disasterous side effects.

Best regards,
Dave

---

### Post by sabrina on 2006-11-18
Thanks for the quick responses!

I'm totally new to Ubuntu, so could you please explain, what a nautilus script is?

The script is as harmless as:

#! /bin/sh

# Dette shell-script sletter filer med bestemte endelser

rm *.tex~
rm *.aux
rm *.log
rm *.thm
rm *.pdf

---

### Post by sabrina on 2006-11-18
Btw is there a difference between sh and bash scripts?

---

### Post by David_T on 2006-11-18
You can always just make an alias by putting a line along this pattern in your .bashrc file:
```

alias "myscript"="~/path/to/myscript"

```

You will have to restart the terminal for it to take effect.


[edit]
Oh, you're doing LaTeX!
For what you're talking about, I usually use a makefile with a "make clean" option, and then I copy it/change it for each project I'm working on, even though there's probably a better way.  Here it is if you're interested.  You just change
"test" to the base name of whatever you are working on, that way you avoid putting any *s as the argument to "rm".  Then you run "make" to build your dvi, or use one of the options like "make clean" to clean up the directory.  It makes things pretty quick if you are spending some time on a document.  It also previews the document automatically by opening up xdvi.

```


TITLE = test
SRCFILE = $(addsuffix .tex, $(TITLE))
DVIFILE = $(addsuffix .dvi, $(TITLE))
PDFFILE = $(addsuffix .pdf, $(TITLE))
AUXFILE = $(addsuffix .aux, $(TITLE))
LOGFILE = $(addsuffix .log, $(TITLE))


TEXIFY = latex
PDFIFY = dvipdf

DVIVIEW = xdvi
PDFVIEW = evince


dvi:	$(SRCFILE)
		$(TEXIFY) $(SRCFILE) && $(DVIVIEW) $(DVIFILE) &

pdf:	dvi
		$(PDFIFY) $(DVIFILE) && $(PDFVIEW) $(PDFFILE) &
		
clean:   
		rm $(DVIFILE) $(AUXFILE) $(LOGFILE) $(PDFFILE) 

```

[edit] changed a couple of things that were wrong

---

### Post by sabrina on 2006-11-18
Hi David

Thank you for the answer.

I don't really understand what to do with the line:

alias "myscript"="~/path/to/myscript"

(remember I'm really a total newbie)


Also thank you for posting your make file. Unfortunately I've never seen a makefile before, so I don't understand, whats going on :neutral:

---

### Post by David_T on 2006-11-18
Hi,

So for the alias part, say you had a script that was called texclean in your home folder, in a folder called "helpfulthings", under a folder called "scripts".  So, we are saying it's at ~/helpfulthings/scripts/texclean.  But, instead of typing ~/helpfulthings/scripts/texclean every time you wanted to call it, you want to be able to make an abbreviation.  To do that, you would open up your configuration file for bash, which is in your home folder and is called .bashrc.  So you would an editor like gedit, and type:

```

gedit ~/.bashrc

```

Then you can just add a line to the bottom of that file that says:
```

alias "texclean"="~/helpfulthings/scripts/texclean"

```

Then when you restart your terminal, you can just type texclean and it will run your script.

The Makefile is maybe not something you want to work with right now, but basically the idea is that you use make if you have a project with a source file that you build into other files, and you want to be able to do that with a minimum of typing every time you want to rebuild the files or clean them up.

To use make, you create a file that is just called "Makefile" in the folder you are working in.  Then when you type just "make" it will go for the first target in the Makefile.  If you want to specify a different target in the Makefile, like "clean", you can type "make clean".

---

### Post by sabrina on 2006-11-19
Thank you! Know it works.

I've just got another problem:

When I try to run a certain script, I can't run it unless I type ./test

Even though the script is in the same directory as to other scripts, that works in all directories. 

It's really weird.

I added the following lines to .bashrc:

# set PATH so it includes the directory with scripts
    export PATH=$PATH:/home/sabrina/scripts

And all tree scripts are in /scripts

---

### Post by sabrina on 2006-11-19
I solved the problem myself :)

---

