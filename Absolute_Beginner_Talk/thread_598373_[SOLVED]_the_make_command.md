---
title: "[SOLVED] the make command"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by mrukus on 2007-10-31
what exactly is the make command supposed to do. because when i run it nothing happens. in the terminal even the name of my laptop dissaperars and i am left with a solid cursor

---

### Post by nest on 2007-10-31
make is to compile a program from the source.

[google always answers.]("http://www.google.com.ar/search?q=make+command&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:es-AR:official&client=firefox-a")

---

### Post by meindian523 on 2007-10-31
It compiles source code of apps,which don't have a deb ready yet,it autodetects which language the app is written in and uses the appropriate compiler from the GNU Compiler Collection(gcc).....

for more info and usage instructions:in Terminal
```

man make
```

edit: oops,nest,didn't mean to step on ur toes....:)

---

### Post by nest on 2007-10-31
> **meindian523 said:**
> edit: oops,nest,didn't mean to step on ur toes....:)

always happens, dont worry pal and keep helping :D

---

### Post by mrukus on 2007-10-31
so why isn't my make command doing anything?

---

### Post by taurus on 2007-10-31
What are you trying to "make"?

---

### Post by mrukus on 2007-10-31
im following the direction put forth by this thread

[http://ubuntuforums.org/showthread.php?t=224350&highlight=acer+acpi](http://ubuntuforums.org/showthread.php?t=224350&highlight=acer+acpi)

slightly modified to account for the newest version of the acpi module.

i found a .deb file that i was able to use a package installer for, but it just put me back to swuare one, now nothing works.....

---

### Post by twiceasworn on 2007-10-31
Typically there is a configuration script in the directory for the program you are going to be compiling.  Usually it is just named configure, but some times its called installer or something similar.  if there is a configure script try doing

```
sudo ./configure
sudo make
sudo make install
```

---

### Post by mrukus on 2007-10-31
there are only two non text base doecuments, there is the souce file that ends in .c, and then there is a make file called Makefile

---

### Post by meindian523 on 2007-10-31
To install something from source,first and foremost,try and see whether there exists a README or Installation instructions or similar in the folder you extracted the tar.gz into.Read that first!:-D

@nest:
Thanx.:)

---

### Post by ByteJuggler on 2007-10-31
To add to what's already been said: 

"make" uses a "makefile" (the recipe if you like, for building/making something, typically a program) to ensure everything that needs to be done to update the target being made, is actually done, but no more.  Anything that's already up to date will not be redone needlessly.  For example, if you have a program consisting of (say) 10 source files, and you edit one of them, then make helps ensure that only the modified one is recompiled before relinking (producing) the final program executable file.  In this way, it helps avoiding needlessly recompiling/redoing work that's been done on previous runs.  

The point is this: If you make something, and then straight after type "make" again, it probably won't do anything, since the thing being made, will still be up to date as a result of the first make, and so there'll be nothing to do as a result of the second "make" command.  Hence make will appear to do nothing.

---

### Post by mrukus on 2007-10-31
yes, got it to work. thanks guys.  but now when i enter the command su, it says there is an authentication failure, ive tried it a few times, i know its the right password

---

### Post by hyper_ch on 2007-10-31
btw, configure and make normally don't need to be executed as root/sudo ;)

---

### Post by mrukus on 2007-10-31
got the make to work, now what baout modprobe and echo? when i enter the modprobe, nothing happens it jsut goes on to the next line, no error msg so i assume it did something, but when i run teh echo line i get this error msg

mrukus@mrukus-laptop:~$ echo "enabled: 1">/proc/acpi/acer/wireless
bash: echo: write error: Invalid argument
enabled: 1

---

### Post by meindian523 on 2007-10-31
In Ubuntu,it's "sudo" not "su" for superuser privileges.For absolute root power,you can use sudo -i.(NOT recommended)

Please mark your thread as solved.

---

### Post by nest on 2007-10-31
mrukus if you post the result of ls in the folder you wanna install or maybe you could "cat README" and post it here.

that would be helpfull... ;)

---

### Post by Can+~ on 2007-10-31
> **mrukus said:**
> got the make to work, now what baout modprobe and echo? when i enter the modprobe, nothing happens it jsut goes on to the next line, no error msg so i assume it did something, but when i run teh echo line i get this error msg

mrukus@mrukus-laptop:~$ echo "enabled: 1">/proc/acpi/acer/wireless
bash: echo: write error: Invalid argument
enabled: 1

echo is a simple command that outputs anything on the terminal, for example if you do
> echo hello world

Then you will read "hello world" on the terminal. The ">" modifier, redirects the output to a file, for example:
> echo hello world > ~/Desktop/foobar.txt

This last command will create a document "foobar.txt" on your desktop with the text "hello world" on it.

---

### Post by mrukus on 2007-10-31
thanks guys i got it installed now.  thanks to all.....now to mark the thread as solved........mmmmmm

---

### Post by Maestro23 on 2007-10-31
> **mrukus said:**
> thanks guys i got it installed now.  thanks to all.....now to mark the thread as solved........mmmmmm

Thread Tools

---

### Post by Can+~ on 2007-10-31
Next time you need root permissions for a long time, use:

> sudo -s

---

### Post by Paqman on 2007-10-31
Also remember that compiling breaks the dependency system in your machine, which is a major source of instability. It's always better to use packages available through apt-get/Synaptic before  trying to compile.

If you *must* compile something, try using checkinstall instead. It's available in the repos, just replace "make install" with "checkinstall" as the last step. The nice thing about that is that you'll be able to uninstall it easily.

---

