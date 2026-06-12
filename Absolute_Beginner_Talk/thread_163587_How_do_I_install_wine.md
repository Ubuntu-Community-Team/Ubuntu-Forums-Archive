---
title: "How do I install wine"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by nsmith on 2006-04-21
I downloaded and am trying to install wine on my ubuntu system.  I was told that there is an .exe file just to click and vuala.  This is not the case.  I also tried fallowing the instructions in the readme file but nothing happened.

Any suggestions?

---

### Post by dave9191 on 2006-04-21
First of all make sure that you have enabled extra repositories ([http://ubuntuguide.org/#extrarepositories)](http://ubuntuguide.org/#extrarepositories)). 

Then either use synaptic (graphical interface), or open a command line and type

sudo apt-get install wine

and that will download and install wine for you. 

--
Dave

---

### Post by nsmith on 2006-04-21
> Then either use synaptic (graphical interface), or open a command line and type

sudo apt-get install wine

and that will download and install wine for you.


I have already downloaded wine onto my desktop. At this point, would I still just type in a terminal sudo apt-get install wine?

---

### Post by jinacio on 2006-04-21
[QUOTE=nsmith]I have already downloaded wine onto my desktop. At this point, would I still just type in a terminal sudo apt-get install wine?[/QUOTE]

No, that is most probably not the same thing.

I assume you downloaded a source version of wine - you need to compile it first to install that.

If you have enough bandwidth i suggest you use the repositories and re-download/install wine. 
it's as easy as that command: "sudo apt-get install wine".
for instructions on enabling the repositores, you can also look at [here]("http://winehq.org/site/download-deb")

if not, take a look at [this doc page ]("http://winehq.org/site/docs/wineusr-guide/installing-wine-source"), where there are instructions to install wine from source.
remember, you would also need to have the source for any dependencies installed on your computer.


Hope that helps
and by the way: please always read the documentation ;)

---

### Post by nsmith on 2006-04-21
The only reason that I want wine is so I can use the adobe acrobat windows version that alows me to fill out forms.  I am starting to wonder if wine will even allow this.  I am unsure exactly what wine does.  Do you know if I can install adobe acrobat windows version using wine?

---

### Post by gondilon on 2006-04-21
go into syaptic and add a repositorie for the debian server. You can then install it using synaptic.

---

### Post by jinacio on 2006-04-21
[QUOTE=nsmith]The only reason that I want wine is so I can use the adobe acrobat windows version that alows me to fill out forms.  I am starting to wonder if wine will even allow this.  I am unsure exactly what wine does.  Do you know if I can install adobe acrobat windows version using wine?[/QUOTE]

you can search the [application database]("http://appdb.winehq.org/"), but from what i know acrobat reader 7 works well (i think it doesn't install well, you would need to use the files installed in a windows partition)

not sure about acrobat (not reader) but again, nothing like reading the docs and trying it out.

good luck

---

### Post by mostwanted on 2006-04-21
Acrobat Reader is available for Linux:

Make sure the multiverse and universe repositories are available:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Open up Synaptic (System &#8594; Administration &#8594; Synaptic) and update your package list (an icon on the toolbar does this). Then search for acroread, right click and select "install". Then click apply in the toolbar. You can also search for WINE and install that if you want to.

---

