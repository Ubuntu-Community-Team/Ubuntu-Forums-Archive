---
title: "synaptic"
date: 2005-07-21
forum: Absolute Beginner Talk
---

### Post by jasonpeinko on 2005-07-21
i have installed programs using it but how do i open them. 
i installed GCC so how do i open it up?

---

### Post by fishfork on 2005-07-21
GCC is a command-line C compiler. If you don't know how to run it, you're probably not the kind of person that will want to use it (not yet, at least).  :) 

But just in case: open a terminal, and type 'gcc somefile.c' to compile the program 'somefile.c'.

Hope this helps.

---

### Post by poofyhairguy on 2005-07-21
[QUOTE=jasonpeinko]i have installed programs using it but how do i open them. 
[/QUOTE]

put these two things in the terminal in order:

> sudo apt-get install menu

> killall gnome-panel

---

### Post by jasonpeinko on 2005-07-21
[QUOTE=fishfork]GCC is a command-line C compiler. If you don't know how to run it, you're probably not the kind of person that will want to use it (not yet, at least).  :) 

But just in case: open a terminal, and type 'gcc somefile.c' to compile the program 'somefile.c'.

Hope this helps.[/QUOTE]
 it worked, but i need one for c++ so i used g++ and it created an a.out file what do i do with it

---

### Post by cwaldbieser on 2005-07-21
[QUOTE=jasonpeinko]it worked, but i need one for c++ so i used g++ and it created an a.out file what do i do with it[/QUOTE]

To run the program, just type:

```
$ ./a.out
```

---

### Post by jasonpeinko on 2005-07-22
[QUOTE=cwaldbieser]To run the program, just type:

```
$ ./a.out
```[/QUOTE]
 thx it works but i am wondering if i am using allgero will the terminal suport images (sprites)?

---

### Post by vintem on 2005-07-22
a.out is the default output (executable) file for g++. You can give any name using the -o option: (if you have written a c++ program test.cpp)

g++ test.cpp -o test

Then you can run this program by typing:

./test

---

### Post by jasonpeinko on 2005-07-22
[QUOTE=vintem]a.out is the default output (executable) file for g++. You can give any name using the -o option: (if you have written a c++ program test.cpp)

g++ test.cpp -o test

Then you can run this program by typing:

./test[/QUOTE]
 k thx but can i use sprites in my programs?

---

### Post by vintem on 2005-07-22
Sorry Jason, about sprites I don't know anything. I hope someone else will answer.

---

### Post by varunus on 2005-07-22
Taking a quick look at the Allegro page, it seems to use console graphics.  You'll need to get its dependencies, but it should work for you if you hit CTRL-ALT-F1, then log in there, and then run your program.

I would look into seeing if Allegro has "X-windows graphics" support.  If it does, then you can play your sprite games the correct way for a linux GUI.

Another thing you may want to look into is SDL:  [http://www.libsdl.org/index.php](http://www.libsdl.org/index.php)
Very handy for developing games.  You can get most of its components in Synaptic, so no need to use their download page.

---

### Post by jasonpeinko on 2005-07-22
[QUOTE=varunus]Taking a quick look at the Allegro page, it seems to use console graphics.  You'll need to get its dependencies, but it should work for you if you hit CTRL-ALT-F1, then log in there, and then run your program.

I would look into seeing if Allegro has "X-windows graphics" support.  If it does, then you can play your sprite games the correct way for a linux GUI.

Another thing you may want to look into is SDL:  [http://www.libsdl.org/index.php](http://www.libsdl.org/index.php)
Very handy for developing games.  You can get most of its components in Synaptic, so no need to use their download page.[/QUOTE]
 ok thx

---

### Post by jasonpeinko on 2005-07-22
[QUOTE=varunus]Taking a quick look at the Allegro page, it seems to use console graphics.  You'll need to get its dependencies, but it should work for you if you hit CTRL-ALT-F1, then log in there, and then run your program.

I would look into seeing if Allegro has "X-windows graphics" support.  If it does, then you can play your sprite games the correct way for a linux GUI.

Another thing you may want to look into is SDL:  [http://www.libsdl.org/index.php](http://www.libsdl.org/index.php)
Very handy for developing games.  You can get most of its components in Synaptic, so no need to use their download page.[/QUOTE]
 can i run sdl in g++

---

### Post by varunus on 2005-07-22
Yes.  Every linux program I've ever used or seen compiles in gcc (or g++), as this is the standard GNU C compiler.  Every development package I've seen for linux is just a wrapper for gcc.

You may want to try Anjuta if you're interested in Linux or GNOME programming; [http://anjuta.sourceforge.net/](http://anjuta.sourceforge.net/)

Its similar to Visual Studio; get it through Synaptic.

---

### Post by jasonpeinko on 2005-07-22
> **varunus]Yes.  Every linux program I've ever used or seen compiles in gcc (or g++), as this is the standard GNU C compiler.  Every development package I've seen for linux is just a wrapper for gcc.

You may want to try Anjuta if you're interested in Linux or GNOME programming said:**
> http://anjuta.sourceforge.net/[/url]

Its similar to Visual Studio; get it through Synaptic.
 ok how do i get g++ to reconize sdl?

---

### Post by cwaldbieser on 2005-07-22
[QUOTE=jasonpeinko]thx it works but i am wondering if i am using allgero will the terminal suport images (sprites)?[/QUOTE]

I think you are asking, "If I am compiling a game and I run it from the console, will I see any graphics."  If you are running an X server, you should see graphics, but not in your console window.  The program will probably create its own window for drawing on.

---

### Post by jasonpeinko on 2005-07-23
[QUOTE=cwaldbieser]I think you are asking, "If I am compiling a game and I run it from the console, will I see any graphics."  If you are running an X server, you should see graphics, but not in your console window.  The program will probably create its own window for drawing on.[/QUOTE]
 ok but when i try and run a program using SDL g++ can not find the SDL libs.
should i try re installing them?
i am running it from the terminal

---

### Post by jasonpeinko on 2005-07-23
[QUOTE=jasonpeinko]ok but when i try and run a program using SDL g++ can not find the SDL libs.
should i try re installing them?
i am running it from the terminal[/QUOTE]
 any ideas

---

### Post by black hole sun on 2005-07-23
[QUOTE=jasonpeinko]any ideas[/QUOTE]
 I assume, you are trying to compile a program that uses SDL libraries? If that is the case you're going to have to include them in the command line, something like this:

g++ -o graphicsapp graphicsapp.c -I/usr/lib/SDL

That is a capital "i" for include. Change the path to SDL for your system. You may also have to define #includes in your program to use the sdl libs, but for that I'm not sure.

---

### Post by jasonpeinko on 2005-07-23
it did not work. i checked usr/lib/SDL there was no SDL folder. do i have to put a file into there.
i did everything the installation told me 2 do with sdl

---

### Post by jasonpeinko on 2005-07-24
help

---

### Post by poofyhairguy on 2005-07-25
build essential maybe?

> sudo apt-get install build-essential

---

### Post by varunus on 2005-07-25
Take this over to the programming section of the forum; they'll know more than we do about how to use gcc and SDL.

---

