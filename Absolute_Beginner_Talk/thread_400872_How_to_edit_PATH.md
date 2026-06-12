---
title: "How to edit PATH?"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by jwalker on 2007-04-04
Hi

This is a two part question. 

One, I'm trying to compile dosbox so I can play X Com, and I type ./configure and things are going well until this: 
> 
checking for SDL - version >= 1.2.0... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: *** SDL version 1.2.0 not found!


Does anyone have any idea how to fix this up. Running a 'locate sdl-config' does not give nay results, even though it appear to be installed via adept..?

Secondly, this is not the first time I have run into issues setting path variable in Linux. In DOS it was nice and straight forward: path=blahblahblah

How does one do this in Linux?

Cheers for all the help. 

Chris

---

### Post by RaZer0r on 2007-04-04
make sure you have the dev package installed as most of the time you'll need that one to compile another.
enter this in your terminal

```

sudo aptitude install libsdl1.2-dev

```

that should do the trick, let me know if it worked :)

---

### Post by jwalker on 2007-04-04
:-( Couldn't find any package who name or description matched "libsdll.2-dev"

Are there some repos I need to enable?

Cheers

---

### Post by Praill on 2007-04-04
Yes, linux doesnt work like windows.
Program executables are installed in /bin or /usr/bin. These are the only directories that need to be in the "path", because they contain everything.
Modules are installed in /lib and /usr/lib (i believe).

Your problem is probably like the user above suggested. You dont have the SDL dev packages, therefore you cant compile source that needs it.

Use the graphical package manager synaptic (sudo synaptic in a terminal). Then look for the version of SDL you have installed and install its dev packes.

---

### Post by astrolabio on 2007-04-04
I don't know if you really need it for your problem, anyway setting the path is very easy.

if you use a bash shell (as you probably do) just type

$ export PATH=$PATH:/im/appending/this/to/the/path

if you want to make the change came true everytime (otherwise you will have to type it everytime you open a new shell) there's a hidden file in your home:

~/.bashrc

Edit it with you text editor and append the line above to the file.
This file contains a bunch of command that are always executed everytime you start a shell. So edit it and then restart a shell and you will have all those command executed. If you appended the comand above you will have your path set too.

In this same file you can actually do some other cool stuff, for example you can set some alias.

Alias are very useful!! 
I guess you get bored as anybody to have always to write long command like:

$ sudo apt-get install mypackage

you can then define an alias in your .bashrc like this :

alias ai='sudo apt-get install'

so you can istall stuff just typing:

$ ai mypackage

You can also define an other alias like

alias asrc='sudo apt-cache search'

so you can search a, for example, browser package from commanf line just typing:

$ asrc browser

and so on. There are already a few examples in the files that are commented, like

alias ll='ls -al'

which is pretty useful too, faster and better than usual ls. If you like it just take out the # from the baginning of the line to activate it.

Be careful to check if your alias already exists as a command anyway, or you risk to "hide" some useful command.

If you for example redefine cd

alias cd='ls'

everytime you use cd to change directory it will actually list the content of the directory. You probably shoudn't want to do that!

---

### Post by jwalker on 2007-04-04
Thanks for all your advice and tips (those alias tips are great caue I've been meaning to research that for ages!). 

Got it sorted in the end, I needed that dev package, and I would have had it, had I looked more closely, I tried to download libsdll-dev.2 as opposed to libsdl1.2-dev. Feeling pretty stupid now...

Anyway, victory! Dosbox is complied, working, now I have a classic game at my disposal! If only I could get xmame going so I could get my street fighter II - hyper fighting, my gaming needs would be satisfied. 

Thanks for all your time and expertise!

---

### Post by RaZer0r on 2007-04-05
well sometimes i just feel glad when there is actualy someone who doesn't just copy paste
(but if you did you wouldn't have got the problem :p)

---

