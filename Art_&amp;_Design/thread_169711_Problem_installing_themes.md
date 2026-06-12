---
title: "Problem installing themes"
date: 2006-05-03
forum: Art &amp; Design
---

### Post by markr on 2006-05-03
Firstly, apologies if this is the wrong sub forum for this question...

Thought I'd try the new MetalThemePack as the screenshots look cool.

However, I seem to be having problems installing it (probably my lack of knowledge as I haven't installed themes before).

The download is a tar file which opens in Archive manager, and I can see all the directories/files etc.

What do I have to do in order to install it? Do I extract it somewhere or what?

I tried to just install it using the themes manager, but that gives me invalid file errors.

Apologies if this is a basic question.

Mark.

---

### Post by jrib on 2006-05-03
If it properly archived, which means it has the right directory structure, you *should* be able to to just drag it into the theme window.  But as you noticed, not every theme is properly archived.

What happens then is, you extract it yourself.  Usually, when they are not properly archived, there is a README with some instructions.  If the README mentions doing anything other than putting it in ~/.themes, I would ignore it.

What you want to do is basically find the directory that usually has the name of the theme, and then inside has a bunch of directories like ``16x16'', ``48x48'', ``Scalable'' and there will also be a file called index.theme.  Once you find this directory just copy it into ~/.themes (if it doesn't exist, create it) and then open up the theme manager.

Hope that works, if you have any problems just link to the theme and we'll take a look.

---

### Post by ComplexNumber on 2006-05-03
**markr**
what i want you to do to install is to do the following:
-extract the DigitalDark metal theme pack tarball into a temporary directory, which will then create a directory called 'DD2-MetalThemePack125'.
-open this directory. there will be 4 gtk themes and 1 metacity theme.
-to install them in your home directory (so that they are only available to you), copy them all into your /home/<username>/.themes directory. if you can't see the ".themes" dfirectory, its because all files that are preceded by a "." are hidden files. to see hidden files, go into the preferences menu in nautilus and select "show hidden files". 
-to install them system-wide(ie so that they are available to all users), go onto the command line and type 'sudo nautilus'. this will allow the directory /usr/share/themes to be written to so that you can manually copy the 4 gtk themes and 1 metacity theme to that directory.

---

### Post by 3rdalbum on 2006-05-05
This demonstrates perfectly how you can do things in several different ways in Linux.

The help files say that you should leave the package tarred and gzipped, go into the Themes control panel, click "Install Theme..." and select the tarball.

---

### Post by ComplexNumber on 2006-05-05
[quote=3rdalbum]This demonstrates perfectly how you can do things in several different ways in Linux.

The help files say that you should leave the package tarred and gzipped, go into the Themes control panel, click "Install Theme..." and select the tarball.[/quote] sometimes that doesn't work...like in this case. occassionally, there's another file or a tarball in the tarball itself. adding that to the theme manager will fail. that i know for a fact. the digital dark one will (probably) fail because it contains more than 1 theme.

---

