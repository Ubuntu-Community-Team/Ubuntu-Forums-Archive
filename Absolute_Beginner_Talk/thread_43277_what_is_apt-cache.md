---
title: "what is apt-cache"
date: 2005-06-21
forum: Absolute Beginner Talk
---

### Post by JulianYorke on 2005-06-21
what is apt-cache? or at lest I think thats how its written, I kinda just over heard it being talked about.  I am a curious noob and so any help will be appreciated :)

---

### Post by sapo on 2005-06-21
[QUOTE=JulianYorke]what is apt-cache? or at lest I think thats how its written, I kinda just over heard it being talked about.  I am a curious noob and so any help will be appreciated :)[/QUOTE]


just type: "man apt-cache" in a terminal..

or read this:

[http://ccrma.stanford.edu/planetccrma/man/man8/apt-cache.8.html](http://ccrma.stanford.edu/planetccrma/man/man8/apt-cache.8.html)

---

### Post by az on 2005-06-21
Okay, everything in Ubuntu is open source.  That means that you can compile everythig from source.  This gives you a lot of power and freedom.

Most people get the benefits of free software (like security, stability, intersting applications, freedom, low or no cost) without having to compile everything themselves.  Just knowing that the application is GPL (licenced as free (free=liberty, in this case) is the important element.

So, your software is packages in binary forum.  You just run it.  The problem with that is compatibility.  The thing that I compiledon my machine may notwork on your's because we may have a different setup.  If you get things from your distribution, you are safe.  If I have something from ubuntu on my machine and I cimpile something else and give you the resulting binary, you will be able to run it no problem as long as you run Ubuntu.

To manage packages, there are package management systems.  Apt is the most advanced one in the linux world.  SynAPTic uses apt.

You can do everything synaptic does from the command line

sudo apt-get update

sudo apt-get install abiword

apt-get inst thecommand to install software.

Apt-cache is a command to search for software

apt-cache search abiword

You can do  
man apt

to get the entire manual.

---

### Post by JulianYorke on 2005-06-21
Thansks :)

---

