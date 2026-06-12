---
title: "Installing programs?"
date: 2006-01-26
forum: Absolute Beginner Talk
---

### Post by hafunui on 2006-01-26
How do I install programs that arent on the synaptic package manager?
Namely Blender3D. I know it's on there, but it's not the latest version. 

I downloaded the linux file from their site, and the readme didnt say much about installing.

> 
Installing is mostly a matter of executing a self-installer package or unpacking it to some folder. Blender has a minimum of system dependencies (like OpenGL and SDL), and doesn't install by overwriting libraries in your system. There are also some extra files needed for a good install, like an antialiased font and standard python scripts, but these are optional. Typically these will go to your HOME/.blender/ directory. Below you find instructions for it per OS.

and 

> Linux, FreeBSD, Irix, Solaris: after unpacking the distribution, you can copy the .blender directory from it to your home directory.

Do I need to compile it or something? :???: What will I need to do that?

---

### Post by bonzodog on 2006-01-26
it sounds like the prgram is already built, in which case it will all be there when you un-tar it.

```
Tar -xvzf <name of file>
```

you will notice a .blender directory has appeared whereever you untarred it, and you just go in there and run it like so: ./blender

---

### Post by public_void on 2006-01-26
You can downdoad the different files from [here]("http://blender.org/cms/Blender.31.0.html") (Which I guess you have, but is it the right one). You need the Linux i386, but it depends on the python version you have installed. You can find out in Synaptic, by searching from "Python2.". If you want the latest version (2.4 I think) get it from the repositories with
```
sudo apt-get install python2.4
```
When thats done download the Python 2.4 version. I not sure what the different between static and dynamic is. 

To untar it you need to do the following. I'm not sure of the install procedure for Blender, but I guessing if you have to compile from source then this is what you have to do.

tar -xvbf [Directory] (Note the file is tar.bz2, so you use the b argument instead of z)
cd [Directory/Blender(plus lots of bits on the end)] 
./configure (Check the last couple of lines when this command finishes, it will show any dependency problems.)
make
sudo make install

---

### Post by Mustard on 2006-01-26
An addendum to the post above, by public void.  Instead of using 'make install', you could use 'checkinstall', which will create an entry in synaptic so you can easily uninstall.  You would need to install checkinstall first though via synaptic.

(This is assuming that you have to compile from source.  In the Blender install this might not be the case.)

---

### Post by Jimmey on 2006-01-27
I think what he's getting at is - 
When you > apt-get install blender, it installs blender to the correct directory, and from then on, you can type> blender in the terminal to run it; it's okay to download the newest version of Blender from the website, but you would you go about putting it in the right directory, and making so that when you typed > blender in the terminal, it'd run?

---

### Post by hafunui on 2006-01-27
When i went to the directory and did ./blender, i got this error:

[COLOR="Sienna"]./blender: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory[/COLOR]

And i think its already compiled. Only the seperate plugins arent ( i dont need those, they are loaded in whenever needed in the program, shouldnt effect anything by not being compiled )

I want to know what to do with everything else thats in there. theres the .blender folder; that goes in my home directory. And then there are the rest of the files...

Once i've moved the .blender folder to home/ the old version still starts up.

---

### Post by kaamos on 2006-01-27
You should install the package "libstdc++5". You can do this with synaptic or type this in terminal```
sudo apt-get install libstdc++5
```
If you get an error like this, using the search at [http://packages.ubuntu.com/](http://packages.ubuntu.com/) is quite helpfull.

---

### Post by hafunui on 2006-01-27
Wow thanks! I had 6 not 5. It works now.

But how do I get IT to start up when i type "blender" instead of the old one?

---

### Post by kaamos on 2006-01-27
You can find executable program with the command "which". So in a terminal, type
```
which blender
```
If it gives something like this
> /usr/bin/blender     /usr/local/bin/blender
the local one is probably the newer. You can then start it by typing the full path in a terminal ("/usr/local/bin/blender").

You can use the menu editor to add the command to the menu.

---

### Post by Jimmey on 2006-01-28
How'd I go about putting the files in the correct places? As if I'd installed it from a .deb?

---

