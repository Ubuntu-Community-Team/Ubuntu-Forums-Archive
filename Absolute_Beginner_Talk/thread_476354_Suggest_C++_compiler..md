---
title: "Suggest C++ compiler."
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by Dark Star on 2007-06-17
Hi all 
Suggest me a C++ compiler and plz tell me hw to install it ;) Thanks .. Note: The compiler should capable of executing Turbo C ver 3 commands .. One of my frnd suggested me GCC is it good? How to install it ? I did not found it in Add/ Remove programs :o

Thanks in advance :)

---

### Post by jd65pl on 2007-06-17
It is pretty much the original C compiler, its been around for a long time and is very solid.
[http://gcc.gnu.org/](http://gcc.gnu.org/)
```

sudo aptitude install gcc
```

---

### Post by Kimm on 2007-06-17
> **jd65pl said:**
> It is pretty much the original C compiler, its been around for a long time and is very solid.
[http://gcc.gnu.org/](http://gcc.gnu.org/)
```

sudo aptitude install gcc
```

he cant use GCC for C++, GCC is only for C

You need G++

> 
sudo apt-get install g++


but you should probably do (to install everything you might need in ways of developement):

> 
sudo apt-get install build-essential


That will also include gcc and g++ :)

---

### Post by Dark Star on 2007-06-17
Thanks all installed  G++ but can't find from where I can access it ? Plz help ;(

---

### Post by Golyadkin on 2007-06-17
You just type g++ to compile:
> 
$ g++ -o hello hello.cpp

Which compiles the source file *hello.cpp* into a binary called *hello*.

---

### Post by Golyadkin on 2007-06-17
Something tells me you are looking for an IDE though. Do you mean a program that will allow you to type your code and then compile it and run it? 

Tryinstalling [anjuta]("http://anjuta.sourceforge.net/screen-shots"), it is in the repositories.
> 
sudo apt-get install anjuta


---

### Post by Dark Star on 2007-06-17
Didn't get ya plz be clear ... U mean while writing in Text editor ?

---

### Post by Dark Star on 2007-06-17
> **Golyadkin said:**
> Something tells me you are looking for an IDE though. Do you mean a program that will allow you to type your code and then compile it and run it? 

Tryinstalling [anjuta]("http://anjuta.sourceforge.net/screen-shots"), it is in the repositories.
Yeah :)

---

### Post by Golyadkin on 2007-06-17
> **Dark Star said:**
> Didn't get ya plz be clear ... U mean while writing in Text editor ?

No, the commands we told you are commands you type into the Terminal. You can find the terminal in the menu on the top left: "Applications > Accessories > Terminal".

But give Anjuta a try (install it using Add/Remove programs or System > ... > Synaptic Package Manager), it will have a button to press to compile your code.

---

